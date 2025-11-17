# Using AVScreenCapture in Custom Scenarios

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

AVScreenCapture enables applications to implement scenario-based custom configurations. Refer to the guidelines below for specific setup instructions.

## Setting Screen Capture Strategies

### Cellular Call Handling

Starting from API version 20, cellular call handling is supported.

Call [OH_AVScreenCapture_StrategyForKeepCaptureDuringCall](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall) to set whether screen capture continues during cellular calls.

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

### B-Frame Encoding Control

Starting from API version 20, you can set whether to use B-frame encoding.

Call [OH_AVScreenCapture_StrategyForBFramesEncoding](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforbframesencoding) to enable B-frame encoding, which helps reduce the size of captured files.

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForBFramesEncoding(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

### Screen Capture Picker Control

Starting from API version 20, you can set whether the screen capture picker should display.

Call [OH_AVScreenCapture_StrategyForPickerPopUp](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpickerpopup) to set whether to display the screen capture picker.

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

## Setting Rotation Adaptation

Starting from API version 20, you can set rotation adaptation.

Call [OH_AVScreenCapture_StrategyForCanvasFollowRotation](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforcanvasfollowrotation) to set whether screen capture automatically follows screen rotation.

After this API is called, you do not need to call [OH_AVScreenCapture_ResizeCanvas](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas) to manually change the resolution.

```c++
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
// Set StrategyForCanvasFollowRotation to true to enable automatic rotation following. This will automatically adjust the virtual screen size after a rotation, ensuring the output follows the rotation promptly.
OH_AVScreenCapture_StrategyForCanvasFollowRotation(strategy, true);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

## Setting Microphone Control

Call [OH_AVScreenCapture_SetMicrophoneEnabled](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setmicrophoneenabled) to enable or disable the microphone during screen capture. The microphone is enabled by default.

> **NOTE**
> To use the microphone during screen capture, you must:
>
> - Configure the ohos.permission.MICROPHONE permission. For details, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
> - Apply for a continuous task. For details, see [Continuous Task](../../task-management/continuous-task.md).

```c++
bool isMic = true;
OH_AVScreenCapture_SetMicrophoneEnabled(capture, isMic);
```

## Setting Privacy Mode

Starting from API version 20, you can call [OH_AVScreenCapture_StrategyForPrivacyMaskMode](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforprivacymaskmode) to set the privacy window masking mode for screen capture.


```c++
// The value 0 means that the full-screen masking mode is used, and 1 means that the window masking mode is used. The default value is full-screen masking mode.
int value = 0;
OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
OH_AVScreenCapture_StrategyForPrivacyMaskMode(strategy, value);
OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
```

Starting from API version 12, you can call [OH_AVScreenCapture_SkipPrivacyMode](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_skipprivacymode) to set windows exempt from privacy masking during screen capture. Currently, you must pass all privacy child window and main window IDs. Pass an empty array to cancel privacy mode exemptions.

```c++
std::vector<int> windowIdsSkipPrivacy = {};
OH_AVScreenCapture_SkipPrivacyMode(capture, &windowIdsSkipPrivacy[0],
    static_cast<int32_t>(windowIdsSkipPrivacy.size()));
```

## Setting the Capture Area

Starting from API version 20, you can configure the capture area.

Call [OH_AVScreenCapture_SetCaptureArea](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setcapturearea) to set the coordinates and size of the area to capture. The example below creates a 100 px * 100 px rectangle area starting at (0, 0). This API can be called both before and after capture starts.

```c++
OH_Rect* region = new OH_Rect;
    region->x = 0;
    region->y = 0;
    region->width = 100;
    region->height = 100;
uint64_t regionDisplayId = 0; // ID of the display where the rectangle area is located.
OH_AVScreenCapture_SetCaptureArea(capture, regionDisplayId, region);
```

## Setting Cursor Visibility

Starting from API version 15, you can set cursor visibility during capture.

Call [OH_AVScreenCapture_ShowCursor](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_showcursor) to set cursor visibility during capture. This API can be called both before and after capture starts.

```c++
OH_AVScreenCapture_ShowCursor(capture, false);
```

## Setting the Maximum Frame Rate

Starting from API version 14, you can set the maximum frame rate.

Call [OH_AVScreenCapture_SetMaxVideoFrameRate](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setmaxvideoframerate) to set the maximum frame rate for screen capture. This API must be called after capture starts.

```c++
OH_AVScreenCapture_SetMaxVideoFrameRate(capture, 20);
```

## Setting Screen Resolution

Call [OH_AVScreenCapture_ResizeCanvas](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_resizecanvas) to adjust the screen capture resolution. This API must be called after capture starts, and resolution values are constrained to specific ranges.

```c++
OH_AVScreenCapture_ResizeCanvas(capture, 768, 1280);
```

## Setting Content Filtering

Filter specific audio and windows during screen capture.

Call [OH_AVScreenCapture_ContentFilter_AddAudioContent](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_contentfilter_addaudiocontent) to exclude specific audio types, including system sounds and the application's own audio.

Call [OH_AVScreenCapture_ContentFilter_AddWindowContent](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_contentfilter_addwindowcontent) to exclude specific windows by their window IDs.

```c++
OH_AVScreenCapture_ContentFilter *contentFilter= OH_AVScreenCapture_CreateContentFilter();
// Filter notification sounds.
OH_AVScreenCapture_ContentFilter_AddAudioContent(contentFilter, OH_SCREEN_CAPTURE_NOTIFICATION_AUDIO);
// Exclude specific window IDs.
std::vector<int> windowIdsExclude = {};
OH_AVScreenCapture_ContentFilter_AddWindowContent(contentFilter, &windowIdsExclude[0],
    static_cast<int32_t>(windowIdsExclude.size()));

OH_AVScreenCapture_ExcludeContent(capture, contentFilter);
```

## Additional Resources

- API reference: For details, see [native_avscreen_capture.h](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md).

- Sample project: This sample demonstrates screen capture using the AVScreenCapture component APIs. For details, see [Screen Capture](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample).
