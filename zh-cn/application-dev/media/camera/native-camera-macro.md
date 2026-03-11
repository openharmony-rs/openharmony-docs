# 微距能力设置(C/C++)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

从API version 19开始，支持设置微距能力。微距能力是指通过光学设计与算法优化，实现近距离对焦并清晰捕捉微小物体细节的相机功能。

## 开发步骤

详细的API说明请参考[Camera API参考](../../reference/apis-camera-kit/capi-oh-camera.md)。

1. 导入NDK接口。选择系统提供的NDK接口能力，导入NDK接口的方法如下。

   <!-- @[import_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/NDKPhotoVideoSample/entry/src/main/cpp/camera_manager.h) -->
   
   ``` C
   #include <cstdint>
   #include <native_buffer/buffer_common.h>
   #include <unistd.h>
   #include <string>
   #include <thread>
   #include <cstdio>
   #include <fcntl.h>
   #include <map>
   #include <string>
   #include <vector>
   #include <native_buffer/native_buffer.h>
   #include "iostream"
   #include "mutex"
   
   #include "hilog/log.h"
   #include "ohcamera/camera.h"
   #include "ohcamera/camera_input.h"
   #include "ohcamera/capture_session.h"
   #include "ohcamera/photo_output.h"
   #include "ohcamera/preview_output.h"
   #include "ohcamera/video_output.h"
   #include "napi/native_api.h"
   #include "ohcamera/camera_manager.h"
   #include <window_manager/oh_display_info.h>
   #include <window_manager/oh_display_manager.h>
   
   namespace OHOS_CAMERA_SAMPLE {
   class NDKCamera {
     public:
       struct CameraBuildingConfig {
           char *str;
           uint32_t focusMode;
           uint32_t cameraDeviceIndex;
           bool isVideo;
           bool isHdr;
           char *videoId;
       };
       ~NDKCamera();
       explicit NDKCamera(CameraBuildingConfig config);
       // ...
   };
   } // namespace OHOS_CAMERA_SAMPLE
   ```

2. 在CMake脚本中链接相关动态库。

   ```txt
   target_link_libraries(entry PUBLIC
       libace_napi.z.so
       libohcamera.so
       libhilog_ndk.z.so
   )
   ```

3. 通过[OH_CaptureSession_IsMacroSupported()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_ismacrosupported)方法，检测当前设备是否支持微距能力。

   <!-- @[is_macro_supported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/NDKPhotoVideoSample/entry/src/main/cpp/camera_manager.cpp) -->
   
   ``` C++
   bool NDKCamera::IsMacroSupported(Camera_CaptureSession* captureSession)
   {
       // 判断设备是否支持微距能力。
       bool isMacroSupported = false;
       if (captureSession == nullptr) {
           OH_LOG_ERROR(LOG_APP, "IsMacroSupported: session is nullptr.");
           return isMacroSupported;
       }
       Camera_ErrorCode ret = OH_CaptureSession_IsMacroSupported(captureSession, &isMacroSupported);
       if (ret != CAMERA_OK) {
           OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_IsMacroSupported failed.");
       }
       if (isMacroSupported) {
           OH_LOG_INFO(LOG_APP, "support macro capability.");
       } else {
           OH_LOG_ERROR(LOG_APP, "No support macro capability.");
       }
       return isMacroSupported;
   }
   ```

4. 使用[OH_CaptureSession_EnableMacro()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_enablemacro)方法开启或关闭微距能力。

   <!-- @[enable_macro](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/NDKPhotoVideoSample/entry/src/main/cpp/camera_manager.cpp) -->
   
   ``` C++
   void NDKCamera::EnableMacro(bool isMacro)
   {
       OH_LOG_INFO(LOG_APP, "EnableMacro: isMacro is %{public}d", isMacro);
       if (IsMacroSupported(captureSession_)) {
           Camera_ErrorCode ret = OH_CaptureSession_EnableMacro(captureSession_, isMacro);
           if (ret != CAMERA_OK) {
               OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_EnableMacro failed.");
           }
       }
   }
   ```

## 状态监听

从API version 20开始，支持监听微距能力是否发生改变。

通过[OH_CaptureSession_RegisterMacroStatusChangeCallback()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_registermacrostatuschangecallback)函数注册回调，返回监听结果。

<!-- @[macro_status_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/NDKPhotoVideoSample/entry/src/main/cpp/camera_manager.cpp) -->

``` C++
void MacroStatusCallback(Camera_CaptureSession *captureSession, bool isMacroDetected)
{
    OH_LOG_INFO(LOG_APP, "MacroStatusCallback isMacro: %{public}d", isMacroDetected);
}

// 注册回调函数。
Camera_ErrorCode NDKCamera::RegisterMacroStatusCallback()
{
    Camera_ErrorCode ret = OH_CaptureSession_RegisterMacroStatusChangeCallback(captureSession_, MacroStatusCallback);
    if (ret != CAMERA_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_RegisterMacroStatusChangeCallback failed.");
    }
    return ret;
}

// 解注册
Camera_ErrorCode NDKCamera::UnregisterMacroStatusCallback()
{
    Camera_ErrorCode ret = OH_CaptureSession_UnregisterMacroStatusChangeCallback(captureSession_, MacroStatusCallback);
    if (ret != CAMERA_OK) {
        OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_UnregisterMacroStatusChangeCallback failed.");
    }
    return ret;
}
```