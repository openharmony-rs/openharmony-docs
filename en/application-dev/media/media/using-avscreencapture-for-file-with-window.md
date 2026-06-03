# Using AVScreenCapture for Window-Level Screen Recording (C/C++)

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yxc2-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T07:17:04.459Z pushedAt=2026-06-03T10:16:59.262Z -->

Starting from API version 10, developers can use the C API of the AVScreenCapture module to implement window/screen recording, capturing audio and video source data from the microphone and device.

This development guide takes recording a specified window as an example to introduce how to use the C API of AVScreenCapture to achieve precise window capture. This solution focuses on the content of a specific window, avoiding full-screen interference, and is suitable for scenarios such as teaching demonstrations, online courses, meeting recordings, and specific content capture.

- Method 1: Record a specified window by setting the specified window ID. In this scenario, after starting screen recording, a share content selection dialog box will pop up. For detailed API declarations, refer to the OH_CAPTURE_SPECIFIED_WINDOW mode in [OH_CaptureMode](../../reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturemode).

- Method 2 (Recommended): Use the system Picker list popup to select the desired window for recording. Use [OH_AVScreenCapture_StrategyForPickerPopUp](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpickerpopup) to set whether to pop up the screen capture Picker. Starting from API version 20, it supports popping up the screen capture Picker on PC/2in1 devices; starting from API version 23, it supports popping up the screen capture Picker on Phone/Tablet devices.

## Applying for Permissions

Before developing this feature, developers should apply for the relevant permissions based on actual requirements:

- If capturing microphone audio data is configured, you need to [request user authorization](../../security/AccessToken/request-user-authorization.md) to configure the microphone permission **ohos.permission.MICROPHONE** and apply for a [continuous task (ArkTS)](../../task-management/continuous-task.md).

- Starting from API version 22, when recording the screen of an application on a PC/2-in-1 device, you can apply for the permission **ohos.permission.TIMEOUT_SCREENOFF_DISABLE_LOCK** to continue recording even when the screen turns off but the device is not locked. For the configuration method, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

- Starting from API version 22, when recording the screen of an application on a PC/2-in-1 device, you can apply for the permission **ohos.permission.CUSTOM_SCREEN_RECORDING** to prevent the privacy warning popup from appearing during screen recording. For the configuration method, see [Restricted Permissions](../../security/AccessToken/restricted-permissions.md).

## How to Develop

**Link the dynamic library in the CMake script**

``` C
target_link_libraries(entry PUBLIC libnative_avscreen_capture.so)
```

1. Add the header file.

   <!-- @[screenCapture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/main.h) -->

   ``` C
   #include "napi/native_api.h"
   #include <multimedia/player_framework/native_avscreen_capture.h>
   #include <multimedia/player_framework/native_avscreen_capture_base.h>
   #include <multimedia/player_framework/native_avbuffer.h>
   #include <multimedia/player_framework/native_avscreen_capture_errors.h>
   #include "hilog/log.h"
   #include <unistd.h>
   #include <fcntl.h>
   #include <string>
   ```

2. Call the [OH_AVScreenCapture_Create](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_create) method to create an AVScreenCapture instance, capture.

   <!-- @[screenCapture_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   g_avCapture = OH_AVScreenCapture_Create();
   ```

3. Call the [OH_AVScreenCapture_Init](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_init) method to configure screen recording parameters.

   After creating the AVScreenCapture instance capture, you can set the parameters required for screen recording.

   <!-- @[screenCapture_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   void SetConfig(OH_AVScreenCaptureConfig &config)
   {
       OH_AudioCaptureInfo micCapInfo = {
           .audioSampleRate = 48000,
           .audioChannels = 2,
           .audioSource = OH_MIC
       };
   
       OH_AudioCaptureInfo innerCapInfo = {
           .audioSampleRate = 48000,
           .audioChannels = 2,
           .audioSource = OH_ALL_PLAYBACK
       };
   
       OH_AudioEncInfo audioEncInfo = {
           .audioBitrate = 48000,
           .audioCodecformat = OH_AAC_LC
       };
   
       OH_VideoCaptureInfo videoCapInfo = {
           .videoFrameWidth = 720,
           .videoFrameHeight = 1280,
           .videoSource = OH_VIDEO_SOURCE_SURFACE_RGBA
       };
   
       OH_VideoEncInfo videoEncInfo = {
           .videoCodec = OH_H264,
           .videoBitrate = 2000000,
           .videoFrameRate = 30
       };
   
       OH_AudioInfo audioInfo = {
           .micCapInfo = micCapInfo,
           .innerCapInfo = innerCapInfo,
           .audioEncInfo = audioEncInfo
       };
   
       OH_VideoInfo videoInfo = {
           .videoCapInfo = videoCapInfo,
           .videoEncInfo = videoEncInfo
       };
   
       config = {
           .captureMode = OH_CAPTURE_HOME_SCREEN,
           .dataType = OH_ORIGINAL_STREAM, // Screen recording data type: raw stream or file
           .audioInfo = audioInfo,
           .videoInfo = videoInfo
       };
   }
   ```

   Method 1: Pass the desired window ID for screen recording.

   ``` C++
   // If you want to record a single window, pass a single window ID; if you want to record multiple windows simultaneously, pass a list of the desired window IDs.
   std::vector<int32_t> missionIds = {88}; // Specifies the window ID for recording.e window ID for recording.
   config.videoInfo.videoCapInfo.missionIDs = missionIds.data();
   config.videoInfo.videoCapInfo.missionIDsLen = static_cast<int32_t>(missionIds.size());
   config.captureMode = OH_CAPTURE_SPECIFIED_WINDOW; // Set the screen recording mode to record a specified window. recording mode to record a specified window.

   // Set to false, meaning the system Picker will not pop up after screen recording starts; instead, a privacy prompt dialog will appear.
   OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, false);
   OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);
   ```

   Method 2 (Recommended): Perform window-level screen recording by popping up the screen capture Picker list and selecting an open application window.

   <!-- @[screenCapture_createCaptureStrategy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Select an open application window for window-level screen recording by popping up the screen capture Picker list.
   OH_AVScreenCapture_CaptureStrategy *strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
   OH_AVScreenCapture_SetCaptureStrategy(g_avCapture, strategy);
   ```

4. Call the [OH_AVScreenCapture_StartScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording) method to start window-level recording.

   <!-- @[screenCapture_startScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   result = OH_AVScreenCapture_StartScreenRecording(g_avCapture);
   ```

5. Call the [OH_AVScreenCapture_StopScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_stopscreenrecording) method to stop recording.

   <!-- @[screenCapture_stopScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   result = OH_AVScreenCapture_StopScreenRecording(g_avCapture);
   ```

6. Call the [OH_AVScreenCapture_Release](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_release) method to destroy the instance and release resources.

   <!-- @[screenCapture_releaseScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   OH_AVScreenCapture_Release(g_avCapture);
   g_avCapture = nullptr;
   ```