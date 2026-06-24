# 使用AVScreenCapture实现窗口级录屏(C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yxc2-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->


从API version 10开始，开发者可通过AVScreenCapture模块的C API接口实现窗口/屏幕录制，采集麦克风和设备的音视频源数据。

本开发指导以指定窗口录制为例，介绍如何使用AVScreenCapture的C API实现精准窗口捕获。该方案聚焦特定窗口内容，避免全屏干扰，适用于教学演示、在线课程、会议记录及特定内容采集等场景。

- 方式一：录制某个指定窗口，需要设置指定窗口ID。该场景下，启动录屏后，会弹出共享内容选择对话框。详细的API声明请参考[OH_CaptureMode](../../reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturemode)中的OH_CAPTURE_SPECIFIED_WINDOW模式。
- 方式二（推荐）：使用系统Picker列表弹窗，选择期望录制的窗口。使用[OH_AVScreenCapture_StrategyForPickerPopUp](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpickerpopup)设置是否弹出屏幕捕获Picker。从API version 20开始，支持在PC/2in1设备上设置弹出屏幕捕获Picker；从API version 23开始，支持在Phone/Tablet设备上设置弹出屏幕捕获Picker。

## 申请权限

在开发此功能前，开发者应根据实际需求申请相关权限：
- 如果配置了采集麦克风音频数据，需[向用户申请授权](../../security/AccessToken/request-user-authorization.md)配置麦克风权限**ohos.permission.MICROPHONE**和申请[长时任务(ArkTS)](../../task-management/continuous-task.md)。
- 从API version 22开始，在PC/2in1设备上对应用进行录屏时，可通过申请权限**ohos.permission.TIMEOUT_SCREENOFF_DISABLE_LOCK**，实现在屏幕熄灭但不锁屏的场景下，继续保持录制的效果。配置方式请参见[声明权限](../../security/AccessToken/declare-permissions.md)。
- 从API version 22开始，在PC/2in1设备上对应用进行录屏时，可通过申请权限**ohos.permission.CUSTOM_SCREEN_RECORDING**，实现在录制屏幕时不再弹出隐私警告弹窗。配置方式请参见[受限开放权限](../../security/AccessToken/restricted-permissions.md)。

## 开发步骤及注意事项

**在CMake脚本中链接动态库**

``` C
target_link_libraries(entry PUBLIC libnative_avscreen_capture.so libability_runtime.so libnative_display_manager.so)
```

1. 添加头文件。

   <!-- @[screenCapture_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/main.h) -->
   
   ``` C
   #include "hilog/log.h"
   #include "napi/native_api.h"
   #include <window_manager/oh_display_info.h>
   #include <window_manager/oh_display_manager.h>
   #include <AbilityKit/ability_runtime/application_context.h>
   #include <multimedia/player_framework/native_avscreen_capture.h>
   #include <multimedia/player_framework/native_avscreen_capture_base.h>
   #include <multimedia/player_framework/native_avscreen_capture_errors.h>
   #include <unistd.h>
   #include <fcntl.h>
   #include <string>
   ```

2. 调用[OH_AVScreenCapture_Create](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_create)方法创建AVScreenCapture实例capture。

   <!-- @[screenCapture_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   g_avCapture = OH_AVScreenCapture_Create();
   ```

3. 调用[OH_AVScreenCapture_Init](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_init)方法配置屏幕录制参数。

   创建AVScreenCapture实例capture后，可以设置屏幕录制所需要的参数。

   <!-- @[screenCapture_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->  
   
   ``` C++
   // 录屏时获取麦克风或者内录，内录参数必填，如果都设置了，内录和麦克风的参数设置需要一致。
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
   // 录屏音频输出规格配置。audioBitrate保证输出文件的比特率为设置的预期比特率，和audioSampleRate无强关联。
   // 此处音频比特率取值为高质量录屏的取值。如果录屏内容以语音为主，不包含音乐、游戏音效等，可以降低为96000或48000。
   OH_AudioEncInfo audioEncInfo = {
       .audioBitrate = 48000,
       .audioCodecformat = OH_AAC_LC
   };
   
   // 获取屏幕信息
   uint64_t displayId = 0;
   NativeDisplayManager_ErrorCode ret = OH_NativeDisplayManager_GetDefaultDisplayId(&displayId);
   
   NativeDisplayManager_DisplayInfo* displayInfo = nullptr;
   ret = OH_NativeDisplayManager_CreateDisplayById(displayId, &displayInfo);
   if (ret != DISPLAY_MANAGER_OK || !displayInfo) {
       return;
   }
   int32_t screenWidth = displayInfo->width;
   int32_t screenHeight = displayInfo->height;
   OH_VideoCaptureInfo videoCapInfo = {
       .videoFrameWidth = screenWidth,
       .videoFrameHeight = screenHeight,
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
       .dataType = OH_CAPTURE_FILE, // 录屏数据类型，文件。
       .audioInfo = audioInfo,
       .videoInfo = videoInfo
   };
   ```

   方式一（推荐）：通过弹出屏幕捕获Picker列表方式，选择已打开的应用窗口进行窗口级录屏。

   <!-- @[screenCapture_createCaptureStrategy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 通过弹出屏幕捕获Picker列表方式，选择已打开的应用窗口进行窗口级录屏。
   OH_AVScreenCapture_CaptureStrategy *strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
   OH_AVScreenCapture_SetCaptureStrategy(g_avCapture, strategy);
   ```

   方式二：需传入期望录制的窗口ID进行录屏。
   
   <!-- @[screenCapture_withWindow_forID](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 如果期望录制单个窗口，需传入单个窗口ID；如果期望同时录制多个窗口，需传入期望录制的窗口ID列表。
   g_missionIds = {g_windowId}; // 指定录制的窗口ID。
   config.videoInfo.videoCapInfo.missionIDs = g_missionIds.data();
   config.videoInfo.videoCapInfo.missionIDsLen = static_cast<int32_t>(g_missionIds.size());
   config.captureMode = OH_CAPTURE_SPECIFIED_WINDOW; // 设置录屏模式为录制指定窗口。
   
   // 设置为false，代表录屏启动后不弹出系统Picker，弹出隐私提示弹窗。
   OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, false);
   OH_AVScreenCapture_SetCaptureStrategy(g_avCapture, strategy);
   ```

4. 调用[OH_AVScreenCapture_StartScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording)方法开始进行窗口级录制。

   <!-- @[screenCapture_startScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   result = OH_AVScreenCapture_StartScreenRecording(g_avCapture);
   ```

5. 调用[OH_AVScreenCapture_StopScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_stopscreenrecording)方法停止录制。

   <!-- @[screenCapture_stopScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   result = OH_AVScreenCapture_StopScreenRecording(g_avCapture);
   ```

6. 调用[OH_AVScreenCapture_Release](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_release)方法销毁实例，释放资源。

   <!-- @[screenCapture_releaseScreenRecording](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   OH_AVScreenCapture_Release(g_avCapture);
   g_avCapture = nullptr;
   ```
