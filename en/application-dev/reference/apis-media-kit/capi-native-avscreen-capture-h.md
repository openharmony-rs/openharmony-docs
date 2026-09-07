# native_avscreen_capture.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## Overview

The file declares the APIs used to create an OH_AVScreenCapture instance.

The API supports two modes: screen recording for data rate and screen recording for file storage. It can collect microphone audio and internal recording audio data, obtain video buffer data, and provide callback mechanisms for status changes, data processing, and error handling. It also supports screen recording in surface mode, content filtering, privacy protection, capture policy configuration, capture area setting and highlighting, and multi-screen recorder functions. This API is applicable to scenarios where screen recorder, screen sharing, or live streaming needs to be implemented within an app.

**File to include**: <multimedia/player_framework/native_avscreen_capture.h>

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

 

## Summary

### Functions

<!--Table: 50%; 50% -->
| Name| Description|
| -- | -- |
| [struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)](#oh_avscreencapture_create) | Creates an OH_AVScreenCapture instance.<br> You can release the instance by calling [OH_AVScreenCapture_Release](#oh_avscreencapture_release).|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)](#oh_avscreencapture_init) | Initializes parameters related to an [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance, including audio sampling parameters for external capture using microphones (optional), audio sampling parameters for internal capture, and video resolution parameters.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreencapture) | Starts screen capture and collects original streams.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreencapture) | Stops screen capture. This function is used in pair with [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture). After calling this function, the application stops screen capture or screen share and releases the microphone.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_startscreenrecording) | Starts screen recording, with recordings saved in files.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_stopscreenrecording) | Stops screen recording. This function is used in pair with [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording).|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)](#oh_avscreencapture_acquireaudiobuffer) | Obtains an audio buffer. When calling this function, the application must allocate the memory of the corresponding struct size to the audio buffer.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|
| [OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)](#oh_avscreencapture_acquirevideobuffer) | Obtains a video buffer. The application can call this function to obtain information such as the video buffer and timestamp.<br> When a video buffer is no longer needed, call **OH_AVScreenCapture_ReleaseVideoBuffer** to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)](#oh_avscreencapture_releaseaudiobuffer) | Releases an audio buffer. When an audio buffer is no longer needed, call this function to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_releasevideobuffer) | Releases a video buffer. When a video buffer is no longer needed, call this function to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)](#oh_avscreencapture_setcallback) | Sets a callback to listen for available video buffers and audio buffers and errors that occur during the function calling.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_SetErrorCallback](#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](#oh_avscreencapture_setdatacallback) instead.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_release) | Releases an OH_AVScreenCapture instance. This function is used in pair with [OH_AVScreenCapture_Create](#oh_avscreencapture_create).|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)](#oh_avscreencapture_setmicrophoneenabled) | Enables or disables the microphone.<br> When **isMicrophone** is set to **true**, the microphone is enabled, and the original PCM data of the microphone can be obtained by calling [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer). When **isMicrophone** is set to **false**, the obtained audio data is silent data.<br> By default, the microphone is enabled.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)](#oh_avscreencapture_setstatecallback) | Sets a state change callback. This function must be called before screen capture starts.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)](#oh_avscreencapture_setdatacallback) | Sets a data processing callback. This function must be called before screen capture starts.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)](#oh_avscreencapture_seterrorcallback) | Sets an error processing callback. This function must be called before screen capture starts.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)](#oh_avscreencapture_startscreencapturewithsurface) | Starts screen capture in surface mode. Different from [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture), this API directly outputs video data to a specified surface window by passing in **OHNativeWindow**. It is suitable for scenarios where screen capture data needs to be rendered to a specific window. In contrast, **OH_AVScreenCapture_StartScreenCapture** obtains the original data rate through a callback, making it suitable for scenarios where audio and video data needs to be processed independently.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)](#oh_avscreencapture_setcanvasrotation) | Sets whether the captured screen data should rotate. This function must be called before screen capture starts.<br> When **canvasRotation** is set to **true**, rotation is enabled and the captured screen data remains upright. When **canvasRotation** is set to **false**, rotation is disabled and the captured screen data will not automatically remain upright.<br> The default value is **false**.|
| [struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)](#oh_avscreencapture_createcontentfilter) | Creates a content filter.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_releasecontentfilter) | Releases a content filter.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)](#oh_avscreencapture_contentfilter_addaudiocontent) | Adds audio content to a content filter.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)](#oh_avscreencapture_excludecontent) | Sets a content filter for an OH_AVScreenCapture instance.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_contentfilter_addwindowcontent) | Adds a list of window IDs to a ContentFilter instance.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)](#oh_avscreencapture_resizecanvas) | Adjusts the screen resolution.<br> This function is used to set the resolution of screen capture data. **width** indicates the screen width and **height** indicates the screen height.<br> Currently, this function supports only the scenario of capturing streams, but not the scenario of storing captured files. In addition, the caller of this function and the video data consumer must ensure that they support resolution changes of the received video data.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)](#oh_avscreencapture_skipprivacymode) | This function must be called before screen recording starts to skip privacy windows.<br> Currently, all the IDs of the subwindows and main windows to skip must be passed in.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)](#oh_avscreencapture_setmaxvideoframerate) | Sets the maximum frame rate for screen capture.<br> This function must be called after screen capture starts.<br>  <br> The maximum frame rate that can be configured is subject to the device's limitations and is ultimately governed by the capabilities of the underlying system.<br> Although there is no limit on the maximum value of the input parameter, the maximum frame rate supported is 60 FPS. If the input parameter value exceeds 60 FPS, 60 FPS is used. If the value does not exceed the upper limit, the passed value is used.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)](#oh_avscreencapture_showcursor) | Sets whether to show the cursor. This function must be called before screen capture starts.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)](#oh_avscreencapture_setdisplaycallback) | Sets a callback function for obtaining the display ID.|
| [OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)](#oh_avscreencapture_createcapturestrategy) | Creates a screen capture strategy.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)](#oh_avscreencapture_releasecapturestrategy) | Releases a screen capture strategy.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)](#oh_avscreencapture_setcapturestrategy) | Sets a screen capture strategy for an OH_AVScreenCapture instance.<br> This function must be called before screen capture starts.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforcanvasfollowrotation) | Sets the automatic rotation following configuration for screen capture. If the value is set to **true**, the screen capture follows the rotation, and the virtual screen size is automatically adjusted after a rotation to ensure the output image matches the new orientation.<br> After this setting, there is no need to manually call [OH_AVScreenCapture_ResizeCanvas](#oh_avscreencapture_resizecanvas) after screen rotation events.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforkeepcaptureduringcall) | Sets whether to keep screen capture during a cellular call.<br> When **value** is set to **true** and screen capture is active during a cellular call, for privacy reasons, the voices of both parties (local microphone and remote speaker) are not captured. Other system sounds are captured normally. After the call ends, the screen capture framework resumes microphone recording. If the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow background applications to activate microphone recording.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)](#oh_avscreencapture_setcapturecontentchangedcallback) | Sets the callback for screen capture content changes. This function must be called before screen capture starts. When the content in the screen capture area changes (for example, the window content is updated or the window is switched), the callback is invoked to notify the application.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture \*capture, uint64_t displayId, OH_Rect\* area)](#oh_avscreencapture_setcapturearea) | Sets or updates the capture area.<br> This function can be called before or after screen capture starts. The coordinates and dimensions provided must be non-negative, and the capture area must not span multiple screens. If setting the area fails, the previously set area is used for capturing.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode(OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)](#oh_avscreencapture_strategyforprivacymaskmode) | Sets the privacy window masking mode.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)](#oh_avscreencapture_setselectioncallback) | Registers a callback to handle user selection results on the recording source confirmation UI. This callback must be invoked before screen recording starts. When screen recording is started, the system displays a confirmation dialog box for the user to select the screen recording object (screen, window, or app). The user's selection result is returned to the app through this callback.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo \*selection, int32_t\* type)](#oh_avscreencapture_getcapturetypeselected) | Obtains the screen capture object type selected by the user on the confirmation UI. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo \*selection, uint64_t\* displayId)](#oh_avscreencapture_getdisplayidselected) | Obtains the display ID of the screen selected by the user for capture on the confirmation screen. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforbframesencoding) | Sets whether to enable B-frame encoding for a CaptureStrategy instance to reduce the size of the recorded file.<br> For details about the restrictions on B-frame video encoding, see [Constraints in B-Frame Video Encoding](../../media/avcodec/video-encoding-b-frame.md#constraints). If the current environment does not meet the restrictions, B-frames will be skipped during screen capture, and no error will be returned.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpickerpopup) | Sets whether to display the screen capture picker.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode(OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)](#oh_avscreencapture_strategyforfillmode) | Sets the fill mode of the captured image in the target region.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_presentpicker) | Displays the picker once more after the screen capture starts, allowing for dynamic updates to the recording source, such as changing the window or screen being captured. The ongoing capture process remains uninterrupted while updating the recording source.<br> Following the dynamic update of the recording source through the picker, the capture can proceed with the newly selected source.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)](#oh_avscreencapture_setcaptureareahighlight) | Sets the highlight style for the screen capture area. During screen recording, the specified capture area can be highlighted to distinguish the capture area from the non-capture area, helping users identify the current screen recording range.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)](#oh_avscreencapture_setpickermode) | Sets the display mode of the picker. Defines the type of content displayed in the picker. This is applicable to scenarios where you need to control the content displayed on the picker screen, for example, allowing users to select only the screen, only the window, or both the screen and window. The mode change takes effect when [OH_AVScreenCapture_PresentPicker](#oh_avscreencapture_presentpicker) is called next time.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)](#oh_avscreencapture_excludepickerwindows) | Hides the specified window in the picker. This function is called before the picker is displayed. It is to filter and hide a window.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t\*\* displayIds, size_t *count)](#oh_avscreencapture_getmultidisplayidsselected) | Obtains the list of display IDs selected by the user for recording on the picker page. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)](#oh_avscreencapture_getmultidisplaycapturecapability) | Obtains the multi-screen recording capability information and determines whether the selected screens support joint recording.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)](#oh_avscreencapture_setprivacyprotectcallback) | Sets a privacy protection callback so that the application can respond to privacy protection events generated during screen capture. This API must be called before screen recording starts. When a privacy window or content is detected during screen recording, the callback notification is sent to the application. The application can then perform privacy protection based on the callback information.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)](#oh_avscreencapture_strategyforpause) | Allows screen capture to be paused.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_pausescreencapture) | Pauses screen capture.|
| [OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)](#oh_avscreencapture_resumescreencapture) | Resumes screen capture.|

## Function Description

### OH_AVScreenCapture_Create()

```c
struct OH_AVScreenCapture *OH_AVScreenCapture_Create(void)
```

**Description**

Creates an OH_AVScreenCapture instance.<br> You can release the instance by calling [OH_AVScreenCapture_Release](#oh_avscreencapture_release).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) * | Pointer to the **OH_AVScreenCapture** instance, which is used for subsequent screen recording operations, parameter configuration, and callback setting.|

### OH_AVScreenCapture_Init()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Init(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureConfig config)
```

**Description**

Initializes parameters related to an [OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) instance, including audio sampling parameters for external capture using microphones (optional), audio sampling parameters for internal capture, and video resolution parameters.<br> In the scenario where screen recording files are stored, the application must ensure that the video encoding parameters, video sampling parameters, audio encoding parameters, audio sampling parameters for internal capture, and audio sampling parameters for external capture using microphones (optional) are valid.<br> In the scenario where screen capture streams are generated, the application must ensure that either audio sampling parameters for internal capture or video sampling parameters are valid, or both are valid, and audio sampling parameters for external capture using microphones are valid (optional).<br> The members of the struct variables are not initialized during initialization. Therefore, the application must correctly set the parameters based on the use scenario. You are advised to set all memory bytes of the OH_AVScreenCaptureConfig struct variables to **0**, and then set valid parameters based on the screen capture scenario.<br> If both **audioSampleRate** and **audioChannels** in the [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) struct are **0**, the OH_AVScreenCapture instance ignores the corresponding audio parameters and does not collect the audio data.<br> If both **videoFrameWidth** and **videoFrameHeight** in the [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md) struct are **0**, the OH_AVScreenCapture instance ignores the corresponding video parameters and does not collect the screen data. You need to call **OH_AVScreenCapture_Create()** to create an instance and then call this method to initialize the parameters.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCaptureConfig](capi-avscreencapture-oh-avscreencaptureconfig.md) config | Parameters related to screen capture initialization.<br> It includes the audio microphone sampling parameters (optional), audio recording sampling parameters, video resolution parameters, video encoding parameters, and audio encoding parameters.<br> Set the parameters based on the screen recording scenario. To save a file, ensure that the video, audio encoding, and sampling parameters are valid. To obtain the data rate, ensure that at least one of the audio or video sampling parameters is valid.<br> The app needs to correctly set the parameters based on the application scenario. You are advised to set all memory bytes of the structure to 0 before setting valid parameters.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the **capture** parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The configuration fails to be initialized. Check whether the screen recording initialization parameter configuration is correct.|

### OH_AVScreenCapture_StartScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen capture and collects original streams.

After the API is called, you can perform the following operations:

1. Use the [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) callback to check whether the data rate is generated.

2. Use the [OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange) callback to listen to the startup status.

3. Call [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer) to obtain the audio buffer.

4. Call [OH_AVScreenCapture_AcquireVideoBuffer](#oh_avscreencapture_acquirevideobuffer) to obtain the video buffer and then the original data rate of the screen recording.

Different from [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording) and [OH_AVScreenCapture_StartScreenCaptureWithSurface](#oh_avscreencapture_startscreencapturewithsurface), this API is used to obtain the original data rate of real-time audio and video, which is applicable to scenarios where the data rate needs to be processed. [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording) is used to directly save the screen recording content as a file, which is applicable to scenarios where only screen recording needs to be saved. [OH_AVScreenCapture_StartScreenCaptureWithSurface](#oh_avscreencapture_startscreencapturewithsurface) uses the surface mode for output, which is applicable to scenarios where data needs to be directly rendered or shared with other components.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the **capture** parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The privacy permission fails to be enabled (you can request the privacy permissions) or screen capture fails to start.|

### OH_AVScreenCapture_StopScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen capture. This function is used in pair with [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture). After calling this function, the application stops screen capture or screen share and releases the microphone.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. Screen capture fails to stop. Ensure that screen recording has started.|

### OH_AVScreenCapture_StartScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Starts screen recording, with recordings saved in files. This API is used together with **OH_AVScreenCapture_StopScreenRecording**.

In the screen recording file storage scenario, valid video encoding and audio encoding parameters need to be configured during initialization. For details, see [OH_AVScreenCapture_Init](#oh_avscreencapture_init).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The privacy permission fails to be enabled or screen capture fails to start. Check whether the privacy permission setting or screen recording configuration is correct.|

### OH_AVScreenCapture_StopScreenRecording()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StopScreenRecording(struct OH_AVScreenCapture *capture)
```

**Description**

Stops screen recording. This function is used in pair with [OH_AVScreenCapture_StartScreenRecording](#oh_avscreencapture_startscreenrecording).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. Screen capture fails to stop. Ensure that the recording has started.|

### OH_AVScreenCapture_AcquireAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_AcquireAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioBuffer **audiobuffer, OH_AudioCaptureSourceType type)
```

**Description**

Obtains an audio buffer. When calling this function, the application must allocate the memory of the corresponding struct size to the audio buffer.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

After the audio buffer is used, call [OH_AVScreenCapture_ReleaseAudioBuffer](#oh_avscreencapture_releaseaudiobuffer) to release the audio buffer.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AudioBuffer](capi-avscreencapture-oh-audiobuffer.md) **audiobuffer | Pointer to the struct for storing the audio buffer. This struct is used to obtain the information about the audio buffer and the timestamp of the buffer.|
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio buffer, which is used to distinguish external streams recorded by the microphone from internal streams played by the system. External streams are applicable to scenarios where external sounds need to be recorded, while internal streams are applicable to scenarios where system sounds need to be recorded.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **audiobuffer** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_NO_MEMORY**: The audio buffer fails to be allocated due to insufficient memory. Release resources and try again, or check whether the system memory is sufficient.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The privacy permission fails to be enabled or the audio buffer fails to be obtained. Check whether the privacy permission setting or screen recording status is correct.|

### OH_AVScreenCapture_AcquireVideoBuffer()

```c
OH_NativeBuffer* OH_AVScreenCapture_AcquireVideoBuffer(struct OH_AVScreenCapture *capture, int32_t *fence, int64_t *timestamp, struct OH_Rect *region)
```

**Description**

Obtains a video buffer. The application can call this function to obtain information such as the video buffer and timestamp.<br> When a video buffer is no longer needed, call **OH_AVScreenCapture_ReleaseVideoBuffer** to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| int32_t *fence | Pointer to parameters for synchronization display and synchronization control of video frames. This parameter is used to obtain the synchronization fence information of video frames to ensure that video frames are rendered before being displayed, preventing issues such as screen tearing.|
| int64_t *timestamp | Pointer to the timestamp of the video frame. The unit is ns.|
| [struct OH_Rect](capi-avscreencapture-oh-rect.md) *region | Pointer to the coordinate information related to video display. The display information (X and Y coordinates) and display dimensions (width and height) of the video frame are included to determine the display area and range of the video frame on the screen.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_NativeBuffer](capi-avscreencapture-avscreencapture-oh-nativebuffer.md)* | OH_NativeBuffer object if the operation is successful. The application can call the APIs provided by the OH_NativeBuffer object to obtain information such as the video buffer and resolution.|

### OH_AVScreenCapture_ReleaseAudioBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseAudioBuffer(struct OH_AVScreenCapture *capture, OH_AudioCaptureSourceType type)
```

**Description**

Releases an audio buffer. When an audio buffer is no longer needed, call this function to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio buffer, which is used to distinguish external streams recorded by the microphone from internal streams played by the system.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The data callback has been set or the audio buffer fails to be released. Use the **OH_AVScreenCapture_OnBufferAvailable** callback to process audio data.|

### OH_AVScreenCapture_ReleaseVideoBuffer()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseVideoBuffer(struct OH_AVScreenCapture *capture)
```

**Description**

Releases a video buffer. When a video buffer is no longer needed, call this function to release it.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The data callback has been set or the video buffer fails to be released. Use the **OH_AVScreenCapture_OnBufferAvailable** callback to process video data.|

### OH_AVScreenCapture_SetCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCallback(struct OH_AVScreenCapture *capture, struct OH_AVScreenCaptureCallback callback)
```

**Description**

Sets a callback to listen for available video buffers and audio buffers and errors that occur during the function calling.<br> Starting from API version 12, you are advised to use [OH_AVScreenCapture_SetErrorCallback](#oh_avscreencapture_seterrorcallback) and [OH_AVScreenCapture_SetDataCallback](#oh_avscreencapture_setdatacallback) instead.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [struct OH_AVScreenCaptureCallback](capi-avscreencapture-oh-avscreencapturecallback.md) callback | OH_AVScreenCaptureCallback struct, which stores related callback function pointers.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The callback fails to be set.|

### OH_AVScreenCapture_Release()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_Release(struct OH_AVScreenCapture *capture)
```

**Description**

Releases an OH_AVScreenCapture instance. This function is used in pair with [OH_AVScreenCapture_Create](#oh_avscreencapture_create).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The OH_AVScreenCapture instance fails to be released. Check whether the instance status or calling sequence is correct.|

### OH_AVScreenCapture_SetMicrophoneEnabled()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMicrophoneEnabled(struct OH_AVScreenCapture *capture, bool isMicrophone)
```

**Description**

Enables or disables the microphone. This function must be called before screen capture starts.<br> When **isMicrophone** is set to **true**, the microphone is enabled, and the original PCM data of the microphone can be obtained by calling [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture) and [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer). When **isMicrophone** is set to **false**, the obtained audio data is silent data.<br> By default, the microphone is enabled.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| bool isMicrophone | Whether to enable the microphone.<br> **true** to enable, **false** to disable.<br> The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The microphone fails to be enabled or disabled. Check the microphone permission and device status.|

### OH_AVScreenCapture_SetStateCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetStateCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnStateChange callback, void *userData)
```

**Description**

Sets a state change callback. This function must be called before screen capture starts.<br> A privacy dialog box is displayed to ask for user consent before screen capture starts. After a successful call to this function, the following scenarios are possible:<br> 1. If the user agrees, the screen capture startup process starts. If screen capture starts successfully, the state change callback is triggered to report the [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_STARTED status to notify the application of the startup success, with a screen capture notification displayed. If screen capture fails to start, the state change callback is triggered to report the failure information (for example, [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_MIC_UNAVAILABLE if the microphone is unavailable), or the error processing callback [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) is triggered to report the error information.<br> 2. If the user disagrees, the screen capture startup process stops. The state change callback is triggered to report the [OH_AVScreenCaptureStateCode](capi-native-avscreen-capture-base-h.md#oh_avscreencapturestatecode).OH_SCREEN_CAPTURE_STATE_CANCELED status to notify the application of the startup failure due to user rejection.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnStateChange](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onstatechange) callback | State change callback. Listens for screen recording status changes (such as successful start, failed start, or user rejection). This callback is triggered when the status changes and must be set before recording. If this parameter is not set, the status change cannot be obtained.|
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the state change callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The state callback fails to be set. Check whether the callback function is valid and whether the callback setting time is correct.|

### OH_AVScreenCapture_SetDataCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDataCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnBufferAvailable callback, void *userData)
```

**Description**

Sets a data processing callback. This function must be called before screen capture starts.<br> The callback is triggered when an audio buffer or a video buffer becomes available during the running of an **OH_AVScreenCapture** instance.<br> The application needs to process microphone audio, internal audio, and video data based on the data type in the callback. After the callback is triggered, the buffer is no longer valid.<br> A successful call to this function leads to the following scenarios:<br> 1. The callbacks [OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable) and [OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable) set by calling [OH_AVScreenCapture_SetCallback](#oh_avscreencapture_setcallback) will no longer be triggered, even when an audio buffer or a video buffer becomes available.<br> 2. A failure message is returned for a call to any of the following functions: [OH_AVScreenCapture_AcquireAudioBuffer](#oh_avscreencapture_acquireaudiobuffer), [OH_AVScreenCapture_ReleaseAudioBuffer](#oh_avscreencapture_releaseaudiobuffer), [OH_AVScreenCapture_AcquireVideoBuffer](#oh_avscreencapture_acquirevideobuffer), and [OH_AVScreenCapture_ReleaseVideoBuffer](#oh_avscreencapture_releasevideobuffer).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) callback | Data processing callback. Callback for obtaining the audio and video buffer. This callback is triggered when the buffer is available. It must be set before recording. After the setting, data needs to be processed in the callback.|
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the data processing callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory. Release resources and try again, or check whether the system memory is sufficient.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The data callback fails to be set. Check whether the callback setting time is correct.|

### OH_AVScreenCapture_SetErrorCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetErrorCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnError callback, void *userData)
```

**Description**

Sets an error processing callback. This function must be called before screen capture starts.<br> The callback is triggered when an error occurs during the running of an OH_AVScreenCapture instance.<br> After a successful call to this function, the callback [OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror) set by calling [OH_AVScreenCapture_SetCallback](#oh_avscreencapture_setcallback) will no longer be triggered, even when an error occurs in the OH_AVScreenCapture instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) callback | Error processing callback. Listens for error information during screen recording. It is triggered when an error occurs and needs to be set before recording. If this parameter is not set, error details cannot be obtained.|
| void *userData | Pointer to the user-defined data. The data is returned as an input parameter when the error processing callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr. Check whether the parameter is a valid pointer.<br>         **AV_SCREEN_CAPTURE_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory. Release resources and try again, or check whether the system memory is sufficient.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The error callback fails to be set. Check whether the callback is set at the correct time.|

### OH_AVScreenCapture_StartScreenCaptureWithSurface()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StartScreenCaptureWithSurface(struct OH_AVScreenCapture *capture, OHNativeWindow *window)
```

**Description**

Starts screen capture in surface mode.

Before calling this method to start screen capture, you need to call OH_AVScreenCapture_Create() to create an instance and call OH_AVScreenCapture_Init() to initialize parameters.

Different from [OH_AVScreenCapture_StartScreenCapture](#oh_avscreencapture_startscreencapture), this API directly outputs video data to a specified surface window by passing OHNativeWindow. It is suitable for scenarios where screen capture data needs to be rendered to a specific window. In contrast, OH_AVScreenCapture_StartScreenCapture obtains the original data rate through callback, making it suitable for scenarios where audio and video data needs to be processed independently.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OHNativeWindow](../apis-arkgraphics2d/capi-nativewindow-nativewindow.md) *window | Pointer to the OHNativeWindow instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture**, input parameter **window**, or **windowSurface** pointed to by **window** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The privacy permission fails to be enabled or screen capture with a surface fails to start.|

### OH_AVScreenCapture_SetCanvasRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCanvasRotation(struct OH_AVScreenCapture *capture, bool canvasRotation)
```

**Description**

Sets whether the captured screen data should rotate. This function must be called before screen capture starts.<br> When **canvasRotation** is set to **true**, rotation is enabled and the captured screen data remains upright. When **canvasRotation** is set to **false**, rotation is disabled and the captured screen data will not automatically remain upright.<br> The default value is **false**.

Unlike [OH_AVScreenCapture_StrategyForCanvasFollowRotation](#oh_avscreencapture_strategyforcanvasfollowrotation), this API is used for static rotation settings. It keeps the captured screen data upright only when canvasRotation is set to true. In contrast, StrategyForCanvasFollowRotation is an automatic rotation policy that automatically adjusts the dimensions of the virtual screen to keep the image upright when the screen rotates. You are advised to use this API only when fixed upright output is required. Use StrategyForCanvasFollowRotation when dynamic rotation is required.

> **NOTE**
>
> Since API version 20, foldable PCs/2-in-1 devices are supported.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| bool canvasRotation | Whether to enable rotation for the captured screen data.<br> The value **true** means to enable rotation, keeping the screen data upright regardless of the device's orientation. The value **false** means to disable rotation, allowing the screen data to rotate along with the device's orientation.<br> The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. Canvas rotation fails to be set for screen capture.|

### OH_AVScreenCapture_CreateContentFilter()

```c
struct OH_AVScreenCapture_ContentFilter *OH_AVScreenCapture_CreateContentFilter(void)
```

**Description**

Creates a content filter.

After the content filter is created, you need to call [OH_AVScreenCapture_ContentFilter_AddAudioContent](#oh_avscreencapture_contentfilter_addaudiocontent) or [OH_AVScreenCapture_ContentFilter_AddWindowContent](#oh_avscreencapture_contentfilter_addwindowcontent) to add the content to be filtered, and then call [OH_AVScreenCapture_ExcludeContent](#oh_avscreencapture_excludecontent) to set the filter. After the content filter is used, call [OH_AVScreenCapture_ReleaseContentFilter](#oh_avscreencapture_releasecontentfilter) to release it. This function is applicable to scenarios where specific content (such as sensitive windows and specific audio types) needs to be filtered out during screen recording to protect privacy or meet service requirements.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| struct [OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) * | An OH_AVScreenCapture_ContentFilter instance if the operation is successful, which is used to configure the types of sounds and window content to be filtered; nullptr otherwise.|

### OH_AVScreenCapture_ReleaseContentFilter()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseContentFilter(struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Releases a content filter.

This function is used together with [OH_AVScreenCapture_CreateContentFilter](#oh_avscreencapture_createcontentfilter) to release the created content filter instance. A content filter can be released after it is set to the OH_AVScreenCapture instance through [OH_AVScreenCapture_ExcludeContent](#oh_avscreencapture_excludecontent).

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **filter** is nullptr.|

### OH_AVScreenCapture_ContentFilter_AddAudioContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddAudioContent(struct OH_AVScreenCapture_ContentFilter *filter, OH_AVScreenCaptureFilterableAudioContent content)
```

**Description**

Adds audio content to a content filter.

You must call OH_AVScreenCapture_CreateContentFilter() to create a content filter instance before adding audio content. After the audio content is added, call OH_AVScreenCapture_ExcludeContent() to apply the content filter to the OH_AVScreenCapture instance. This method is applicable to scenarios where specific audio content needs to be excluded from screen recordings, such as filtering out system notification sounds during tutorial recording or excluding audio from other apps during conference recording. The call sequence is **CreateContentFilter**, **AddAudioContent/AddWindowContent**, **ExcludeContent**, and **ReleaseContentFilter**.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance.|
| [OH_AVScreenCaptureFilterableAudioContent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturefilterableaudiocontent) content | Filterable audio type. Type of audio content to be excluded from screen recording. Select the corresponding enumerated value based on the audio content type to be filtered. Multiple audio types can be filtered at the same time. For details about the enumerated values and their use scenarios, see [OH_AVScreenCaptureFilterableAudioContent](capi-native-avscreen-capture-base-h.md#oh_avscreencapturefilterableaudiocontent).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **filter** is nullptr or the input parameter **content** is invalid.|

### OH_AVScreenCapture_ExcludeContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludeContent(struct OH_AVScreenCapture *capture, struct OH_AVScreenCapture_ContentFilter *filter)
```

**Description**

Sets a content filter for an OH_AVScreenCapture instance.

This method is applicable to scenarios where specific audio or window content needs to be excluded during screen recording, for example, excluding sensitive windows for privacy protection or avoiding recording irrelevant system notification sounds.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **filter** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT**: The operation is not supported. For streams, the AudioCapturer API must be called for the operation to take effect during the start.<br>         For captured files, the Recorder API must be called for the operation to take effect during the start.|

### OH_AVScreenCapture_ContentFilter_AddWindowContent()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ContentFilter_AddWindowContent(struct OH_AVScreenCapture_ContentFilter *filter, int32_t *windowIDs, int32_t windowCount)
```

**Description**

Adds a list of window IDs to a ContentFilter instance.

This method is applicable to scenarios where specific windows need to be excluded from the screen recording, such as excluding the chat window during tutorial recording or excluding the notification panel during presentation recording.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture_ContentFilter](capi-avscreencapture-oh-avscreencapture-contentfilter.md) *filter | Pointer to the OH_AVScreenCapture_ContentFilter instance.|
| int32_t *windowIDs | Pointer to the array of window IDs to be filtered. The window ID can be obtained through the window management API.|
| int32_t windowCount | Length of the window ID list. The value must be a positive integer and the same as the actual length of the **windowIDs** array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK** if the operation is successful; a specific error code if the operation fails.|

### OH_AVScreenCapture_ResizeCanvas()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResizeCanvas(struct OH_AVScreenCapture *capture, int32_t width, int32_t height)
```

**Description**

Adjusts the resolution of screen capture data.<br> This function is used to set the resolution of screen capture data. **width** indicates the screen width and **height** indicates the screen height.<br> Currently, this function supports only the scenario of capturing streams, but not the scenario of storing captured files. Your app must ensure that it supports resolution changes of the received video data.

Constraints:

- This API can only be called during the running phase of screen recording.
- When the auto-follow rotation configuration [OH_AVScreenCapture_StrategyForCanvasFollowRotation](#oh_avscreencapture_strategyforcanvasfollowrotation) is set, this API cannot be simultaneously called to adjust the screen recording resolution.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| int32_t width | Width of the screen to capture. The unit is px. The value must be a positive integer. It is recommended that the value be less than or equal to the screen resolution width of the device. This parameter must be used together with height and set based on the actual recording requirements. Currently, this function supports only the scenario of capturing data rate, but not the scenario of storing captured files. This method cannot be called when the automatic rotation following configuration is being set.|
| int32_t height | Height of the screen to capture. The unit is px. The value must be a positive integer. It is recommended that the value be less than or equal to the screen resolution height of the device. This parameter must be used together with width. Set this parameter based on the actual recording requirements. Currently, this function supports only the scenario of capturing data rate, but not the scenario of storing captured files. This method cannot be called when the automatic rotation following configuration is being set.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_SkipPrivacyMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SkipPrivacyMode(struct OH_AVScreenCapture *capture, int32_t *windowIDs, int32_t windowCount)
```

**Description**

This function is used to skip privacy windows during screen recording. It must be called before screen recording starts.<br> Currently, all the IDs of the subwindows and main windows to skip must be passed in.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| int32_t *windowIDs | Pointer to the IDs of the privacy windows to skip.|
| int32_t windowCount | Length of the privacy window ID list. The value must be a positive integer and must be the same as the actual length of the **windowIDs** array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_SetMaxVideoFrameRate()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetMaxVideoFrameRate(struct OH_AVScreenCapture *capture, int32_t frameRate)
```

**Description**

Sets the maximum frame rate for screen capture.<br> This function must be called after screen capture starts.<br>  <br> The maximum frame rate that can be configured is subject to the device's limitations and is ultimately governed by the capabilities of the underlying system.<br> Although there is no limit on the maximum value of the input parameter, the maximum frame rate supported is 60 FPS. If the input parameter value exceeds 60 FPS, 60 FPS is used. If the value does not exceed the upper limit, the passed value is used.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 14

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| int32_t frameRate | Maximum frame rate for screen capture. The unit is frames per second (FPS). Currently, the maximum frame rate is 60 FPS. The low frame rate (1–15) is suitable for static content, the medium frame rate (16–30) is suitable for common scenarios, and the high frame rate (31–60) is suitable for scenarios that require high smoothness. The actual frame rate is limited by the device capability. If the input frame rate exceeds 60 FPS, 60 FPS is used.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr, or the input parameter **frameRate** is not supported.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_ShowCursor()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ShowCursor(struct OH_AVScreenCapture *capture, bool showCursor)
```

**Description**

Sets whether to show the cursor. This function must be called before screen capture starts.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| bool showCursor | Whether to show the cursor.<br> **true** to show, false to hide.<br> The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_UNSUPPORT** (available since API version 20): The device does not support the operation. Check whether the device supports screen recording.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The cursor setting fails.|

### OH_AVScreenCapture_SetDisplayCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetDisplayCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnDisplaySelected callback, void *userData)
```

**Description**

Sets a callback function for obtaining the display ID. This API must be called before recording starts.

When there are multiple screens in the system, this callback notification is used to notify the app of the ID of the screen selected by the user during screen recording startup, so that the app can determine the target screen for screen recording.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnDisplaySelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_ondisplayselected) callback | Callback function for returning the display ID. Obtains the ID of the screen selected by the user for recording. This callback function is triggered after the user selects a screen and needs to be set before recording. If this parameter is not set, the ID of the screen selected by the user cannot be obtained.|
| void *userData | Pointer to the custom data provided by the app. The data is returned as an input parameter when the screen ID callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_NO_MEMORY**: The memory fails to be allocated due to insufficient memory.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_STATE**: The callback must be called before the **start** function.|

### OH_AVScreenCapture_CreateCaptureStrategy()

```c
OH_AVScreenCapture_CaptureStrategy* OH_AVScreenCapture_CreateCaptureStrategy(void)
```

**Description**

Creates a screen capture strategy.

Configures the parameters of the screen capture strategy. You can use the StrategyFor* APIs to set the rotation, screen recording during calls, B-frame encoding, and picker pop-up policies.

After using the screen capture strategy, call [OH_AVScreenCapture_ReleaseCaptureStrategy](#oh_avscreencapture_releasecapturestrategy) to release it.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md)* | If the execution is successful, an **OH_AVScreenCapture_CaptureStrategy** instance is returned to configure the screen capture strategy (such as automatic rotation, screen recording during calls, and B-frame encoding). Otherwise, a null pointer is returned.|

### OH_AVScreenCapture_ReleaseCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ReleaseCaptureStrategy(OH_AVScreenCapture_CaptureStrategy* strategy)
```

**Description**

Releases a screen capture strategy.

This API is used with [OH_AVScreenCapture_CreateCaptureStrategy](#oh_avscreencapture_createcapturestrategy) to release the created CaptureStrategy instance.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md)* strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr.|

### OH_AVScreenCapture_SetCaptureStrategy()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureStrategy(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_CaptureStrategy *strategy)
```

**Description**

Sets a screen capture strategy for an **OH_AVScreenCapture** instance.<br> This function must be called before screen capture starts.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **strategy** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_STATE**: This function is called after screen capture starts.|

### OH_AVScreenCapture_StrategyForCanvasFollowRotation()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForCanvasFollowRotation(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets the automatic rotation following configuration for screen capture. If the value is set to **true**, the screen capture follows the rotation, and the virtual screen size is automatically adjusted after a rotation to ensure the output image matches the new orientation.<br> After this setting, there is no need to manually call [OH_AVScreenCapture_ResizeCanvas](#oh_avscreencapture_resizecanvas) after screen rotation events.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| bool value | Whether the width and height of the virtual screen rotate with the screen.<br> **true** to rotate with the screen, **false** to keep the initial settings.<br> The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr.|

### OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForKeepCaptureDuringCall(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to keep screen capture during a cellular call.<br> When **value** is set to **true** and screen capture is active during a cellular call, for privacy reasons, the voices of both parties (local microphone and remote speaker) are not captured. Other system sounds are captured normally. After the call ends, the screen capture framework resumes microphone recording. If the screen capture application is running in the background when the call ends, microphone recording fails to start because the audio module does not allow background applications to activate microphone recording.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| bool value | Whether to keep screen capture during a cellular call.<br> **true** to keep, **false** otherwise.<br> The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr.|

### OH_AVScreenCapture_SetCaptureContentChangedCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureContentChangedCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnCaptureContentChanged callback, void *userData)
```

**Description**

Sets the callback for screen capture content changes. This function must be called before screen capture starts.

When the content in the screen capture area changes (for example, the window content is updated or the window is switched), the callback is used to notify the application.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnCaptureContentChanged](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_oncapturecontentchanged) callback | Pointer to the callback method instance for the screen capture content change event. Listens for screen capture content change events. This function must be called before screen capture starts. If this parameter is not set, the content change information cannot be obtained.|
| void *userData | Pointer to the custom data provided by the app. The data is returned as an input parameter when the screen capture content change callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** or **callback** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The screen capture callback fails to be set.|

### OH_AVScreenCapture_SetCaptureArea()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureArea(struct OH_AVScreenCapture *capture, uint64_t displayId, OH_Rect* area)
```

**Description**

Sets or updates the capture area.<br> This function can be called before or after screen capture starts. The coordinates and dimensions provided must be non-negative, and the capture area must not span multiple screens. If setting the area fails, the previously set area is used for capturing.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| uint64_t displayId | ID of the screen to capture. You can obtain the screen IDs supported by the device through the **OH_AVScreenCapture_OnDisplaySelected** callback or system API. In multi-screen scenarios, you need to specify the ID of the screen to be recorded. In single-screen scenarios, you can use the default screen ID.|
| [OH_Rect](capi-avscreencapture-oh-rect.md)* area | Pointer to the structure of the capture area, which is used to specify the capture area on the screen. The coordinates (x, y) and dimensions (width, height) of the capture area. The coordinates and dimensions must be non-negative, and the capture area must not span multiple screens. If setting the area fails, the previously set area is used for capturing.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is a nullptr, the input **displayId** does not exist, or the input **area** is abnormal.|

### OH_AVScreenCapture_StrategyForPrivacyMaskMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPrivacyMaskMode(OH_AVScreenCapture_CaptureStrategy *strategy, int32_t value)
```

**Description**

Sets the privacy window masking mode.

The full-screen masking mode (value=0) is applicable to scenarios that have strict requirements on privacy protection. For example, during the recording of a financial app, once a privacy window appears, the entire screen is masked. The privacy window masking mode (value=1) is applicable to scenarios where only the privacy window area needs to be masked and other content can still be recorded normally.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| int32_t value | If this parameter is set to **0**, the full-screen masking mode is used when there is a privacy window.<br> If this parameter is set to **1**, the privacy window masking mode is used when there is a privacy window. Any other value will result in an error.<br> The default value is **0**, indicating the full-screen masking mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr or **value** is invalid.|

### OH_AVScreenCapture_SetSelectionCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetSelectionCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnUserSelected callback, void *userData)
```

**Description**

Registers a callback to handle user selection results on the recording source confirmation UI. This callback must be invoked before screen recording starts.

When screen recording is started, the system displays a confirmation dialog box for the user to select the screen recording object (screen, window, or app). The user's selection result is returned to the app through this callback.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the screen capture instance for which the callback needs to be registered.|
| [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback | Callback used to instruct the application to carry out the relevant logic processing once the user has confirmed on the UI. Callback used to obtain the information about the recording object (screen or window) selected by the user on the picker UI. This callback must be set before screen recording is started. If this parameter is not set, the user's selection result cannot be obtained.|
| void *userData | Pointer to the control block provided by the application. The control block is returned as an input parameter when the callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.|

### OH_AVScreenCapture_GetCaptureTypeSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetCaptureTypeSelected(OH_AVScreenCapture_UserSelectionInfo *selection, int32_t* type)
```

**Description**

Obtains the screen capture object type selected by the user on the confirmation UI. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to the OH_AVScreenCapture_UserSelectionInfo instance.|
| int32_t* type | Pointer to the type of the object to be captured. **0**: screen; **1**: window; **2**: application.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **selection** is nullptr.|

### OH_AVScreenCapture_GetDisplayIdSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetDisplayIdSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t* displayId)
```

**Description**

Obtains the display ID of the screen selected by the user for capture on the confirmation screen. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to the OH_AVScreenCapture_UserSelectionInfo instance.|
| uint64_t* displayId | Pointer to the ID of the screen selected by the user.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **selection** is nullptr.|

### OH_AVScreenCapture_StrategyForBFramesEncoding()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForBFramesEncoding(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to enable B-frame encoding for a CaptureStrategy instance to reduce the size of the recorded file.<br> For details about the restrictions on B-frame video encoding, see [Constraints in B-Frame Video Encoding](../../media/avcodec/video-encoding-b-frame.md#constraints). If the current environment does not meet the restrictions, B-frames will be skipped during screen capture, and no error will be returned.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| bool value | Whether to enable B-frame encoding for the recorded file.<br> **true** to enable, **false** otherwise.<br> The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr.|

### OH_AVScreenCapture_StrategyForPickerPopUp()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPickerPopUp(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Sets whether to display the screen capture picker. The picker is a screen for selecting the screen recording source. Users can select the screen or window to be recorded.

Use scenario: The picker is displayed when user interaction is required to select the recording source (for example, selecting a screen in a multi-screen environment). The picker can be disabled for automatic recording when the app has explicitly specified the recording source or user intervention is not required.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| bool value | If this parameter is set to **false**, the app has specified the content to capture, and the picker is not displayed after screen capture starts. If this parameter is set to **true**, the picker is displayed after screen capture starts. If this parameter is not set, the system automatically determines whether to display the picker based on the current recording configuration when screen recording is started.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr or **value** is invalid.|

### OH_AVScreenCapture_StrategyForFillMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForFillMode(OH_AVScreenCapture_CaptureStrategy *strategy, OH_AVScreenCapture_FillMode mode)
```

**Description**

Sets the fill mode of the captured image in the target region.

When the dimensions of the captured image are inconsistent with those of the target output region, the fill mode determines how the image is displayed in the target region. This is applicable to scenarios where the screen recording image does not match the output dimensions and the image adaptation mode needs to be specified. For example, in a video conference, the image aspect ratio is maintained without stretching; in game recording, the image is stretched to fill the full screen. For details, see [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode).

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode) mode | Fill mode of the captured image. Select a proper fill mode based on the difference between the dimensions of the capture area and output area. For details about the enumerated values and their use scenarios, see [OH_AVScreenCapture_FillMode](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_fillmode).<br>Different modes determine the scaling, clipping, or stretching mode of the captured image in the output region.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **strategy** is nullptr.|

### OH_AVScreenCapture_PresentPicker()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PresentPicker(struct OH_AVScreenCapture *capture)
```

**Description**

Displays the picker once more after the screen capture starts, allowing for dynamic updates to the recording source, such as changing the window or screen being captured. The ongoing capture process remains uninterrupted while updating the recording source.<br> Following the dynamic update of the recording source through the picker, the capture can proceed with the newly selected source.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_SetCaptureAreaHighlight()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetCaptureAreaHighlight(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureHighlightConfig config)
```

**Description**

Sets the highlight style for the screen capture area.

During screen recording, the specified capture area can be highlighted to distinguish the capture area from the non-capture area, helping users identify the current screen recording range. This function is applicable to scenarios where the capture area boundary needs to be highlighted during screen recording, for example, helping users identify the current recording range during multi-area recording or marking the key operation area during teaching demonstration.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCaptureHighlightConfig](capi-avscreencapture-oh-avscreencapturehighlightconfig.md) config | Highlight parameters for the screen capture area. Set this parameter when you need to visually highlight the capture area during recording. If this parameter is not set or is set to an empty value, the highlight mode is not used by default. You can configure attributes such as the border style and color of the highlighted area as required.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr or **config** is invalid.|

### OH_AVScreenCapture_SetPickerMode()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPickerMode(struct OH_AVScreenCapture *capture, OH_CapturePickerMode pickerMode)
```

**Description**

Sets the display mode of the picker. Defines the type of content displayed in the picker. This is applicable to scenarios where the content displayed on the picker needs to be controlled. For example, you can allow users to select only screens, only windows, or both screens and windows. The mode change takes effect when [OH_AVScreenCapture_PresentPicker](#oh_avscreencapture_presentpicker) is called next time.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_CapturePickerMode](capi-native-avscreen-capture-base-h.md#oh_capturepickermode) pickerMode | Picker display mode, which defines the type of content displayed in the picker.<br>For details about the effect of each enumerated value, see [OH_CapturePickerMode](capi-native-avscreen-capture-base-h.md#oh_capturepickermode). Different modes determine the types of screen capture objects that can be selected by users in the picker. You can select the content type to be displayed (such as only the screen, only the window, or both) based on application requirements.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr or **pickerMode** is invalid.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_ExcludePickerWindows()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ExcludePickerWindows(struct OH_AVScreenCapture *capture, const int32_t *excludedWindowIDs, uint32_t windowCount)
```

**Description**

Hides the specified window in the picker. This function is called before the picker is displayed. It is to filter and hide a window.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| const int32_t *excludedWindowIDs | Array of IDs of the windows to be hidden (existing windows).|
| uint32_t windowCount | Size of the array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode) | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is nullptr or **excludedWindowIDs** is invalid.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_GetMultiDisplayIdsSelected()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayIdsSelected(OH_AVScreenCapture_UserSelectionInfo *selection, uint64_t** displayIds, size_t *count)
```

**Description**

Obtains the list of display IDs selected by the user for recording on the picker page. This function is used in the [OH_AVScreenCapture_OnUserSelected](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onuserselected) callback. The **selection** pointer is destroyed after the callback is complete.

**Since**: 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_UserSelectionInfo](capi-avscreencapture-oh-avscreencapture-userselectioninfo.md) *selection | Pointer to the OH_AVScreenCapture_UserSelectionInfo instance.|
| uint64_t** displayIds | Array of display IDs selected by the user. The memory of the **displayIds** parameter is managed by **OH_AVScreenCapture_UserSelectionInfo** and does not need to be manually released.|
| size_t *count | Number of display IDs selected by the user. The value must be greater than or equal to 1 and must be the same as the actual length of the **displayIds** array.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **selection** is a null pointer.|

### OH_AVScreenCapture_GetMultiDisplayCaptureCapability()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_GetMultiDisplayCaptureCapability(struct OH_AVScreenCapture *capture, uint64_t *displayIds, size_t count, OH_MultiDisplayCapability *capability)
```

**Description**

Obtains the multi-screen recording capability information and determines whether the selected screens support joint recording.

**Since**: 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| uint64_t *displayIds | Array of display IDs selected by the user.|
| size_t count | Number of display IDs selected by the user.|
| [OH_MultiDisplayCapability](capi-avscreencapture-oh-multidisplaycapability.md) *capability | Pointer to the **OH_MultiDisplayCapability** instance.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input parameter **capture** is a null pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed, and data fails to be obtained.|

### OH_AVScreenCapture_SetPrivacyProtectCallback()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_SetPrivacyProtectCallback(struct OH_AVScreenCapture *capture, OH_AVScreenCapture_OnPrivacyProtect callback, void *userData)
```

**Description**

Sets a privacy protection callback so that the application can respond to privacy protection events generated during screen capture. This API must be called before screen recording starts.

When a privacy window or content is detected during screen recording, the callback notification is sent to the application. The application can then perform privacy protection based on the callback information.

**Since**: 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the OH_AVScreenCapture instance.|
| [OH_AVScreenCapture_OnPrivacyProtect](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onprivacyprotect) callback | Privacy protection callback function. It is used to respond to privacy protection events (for example, the appearance of a privacy window). It is triggered when an event occurs and needs to be set before screen recording. If this parameter is not set, privacy protection events cannot be obtained.|
| void *userData | Pointer to the custom data provided by the app. The data is returned as an input parameter when the privacy protection callback is triggered.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input screen capture instance or callback is a null pointer.|

### OH_AVScreenCapture_StrategyForPause()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_StrategyForPause(OH_AVScreenCapture_CaptureStrategy *strategy, bool value)
```

**Description**

Allows screen capture to be paused.

This is applicable to scenarios where screen recording may need to be paused temporarily, for example, when the user switches between apps or answers a call and wants to pause the recording without ending the screen recording session. If this parameter is set to **true**, screen capture can be paused. If this parameter is set to **false**, screen capture cannot be paused. After setting the value to **true**, you can call **OH_AVScreenCapture_PauseScreenCapture** to pause screen recording and **OH_AVScreenCapture_ResumeScreenCapture** to resume screen recording during screen recording. This policy must be configured using OH_AVScreenCapture_SetCaptureStrategy before screen capture starts.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVScreenCapture_CaptureStrategy](capi-avscreencapture-oh-avscreencapture-capturestrategy.md) *strategy | Pointer to the OH_AVScreenCapture_CaptureStrategy instance.|
| bool value | Whether to allow screen capture to be paused. **true**: yes; **false**: no. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The pointer of the **strategy** parameter is null.|

### OH_AVScreenCapture_PauseScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_PauseScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Pauses screen capture. This function must be called after screen capture starts.

This function is used together with [OH_AVScreenCapture_ResumeScreenCapture](#oh_avscreencapture_resumescreencapture). After this function is called, screen capture data collection is paused, and the collected data remains valid. Before calling this function, you need to call [OH_AVScreenCapture_StrategyForPause](#oh_avscreencapture_strategyforpause) to set the pause strategy (set value to **true**) and call OH_AVScreenCapture_SetCaptureStrategy to configure the strategy before screen capture starts.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the initialized screen capture instance.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input screen capture instance is a null pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVScreenCapture_ResumeScreenCapture()

```c
OH_AVSCREEN_CAPTURE_ErrCode OH_AVScreenCapture_ResumeScreenCapture(struct OH_AVScreenCapture *capture)
```

**Description**

Resumes screen capture. This function must be called after screen capture starts.

This function is used together with [OH_AVScreenCapture_PauseScreenCapture](#oh_avscreencapture_pausescreencapture). After this function is called, screen capture data collection is resumed. Before calling this function, you need to use **OH_AVScreenCapture_StrategyForPause** to set the pause policy (set value to **true**) and use **OH_AVScreenCapture_SetCaptureStrategy** to configure the policy before screen capture starts.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [struct OH_AVScreenCapture](capi-avscreencapture-oh-avscreencapture.md) *capture | Pointer to the initialized screen capture instance.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVSCREEN_CAPTURE_ErrCode | **AV_SCREEN_CAPTURE_ERR_OK**: The operation is successful.<br>         **AV_SCREEN_CAPTURE_ERR_INVALID_VAL**: The input screen capture instance is a null pointer.<br>         **AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|
