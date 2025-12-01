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

   ```c++
   // 导入NDK接口头文件。
   #include "hilog/log.h"
   #include "ohcamera/camera.h"
   #include "ohcamera/camera_input.h"
   #include "ohcamera/capture_session.h"
   #include "ohcamera/camera_manager.h"
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

   ```c++
   bool IsMacroSupported(Camera_CaptureSession* captureSession)
   {
        // 判断设备是否支持微距能力。
        bool isMacroSupported = false;
        if (captureSession == nullptr) {
           OH_LOG_ERROR(LOG_APP, "captureSession is nullptr.");
           return isMacroSupported;
        }
        Camera_ErrorCode ret = OH_CaptureSession_IsMacroSupported(captureSession, &isMacroSupported);
        if (ret != CAMERA_OK) {
           OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_IsMacroSupported failed.");
        }
        if (isMacroSupported) {
           OH_LOG_INFO(LOG_APP, "Support macro capability.");
        } else {
           OH_LOG_ERROR(LOG_APP, "No Support macro capability.");
        }
       return isMacroSupported;
   }

   ```

4. 使用[OH_CaptureSession_EnableMacro()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_enablemacro)方法开启或关闭微距能力。

   ```c++
   void EnableMacro(Camera_CaptureSession* captureSession, bool enabled)
    {
        if (IsMacroSupported(captureSession)) {
            Camera_ErrorCode ret = OH_CaptureSession_EnableMacro(captureSession, enabled);
            if (ret != CAMERA_OK) {
            	OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_EnableMacro failed.");
            }
        }
    }

   ```


## 状态监听

从API version 20开始，支持监听微距能力是否发生改变。

通过[OH_CaptureSession_RegisterMacroStatusChangeCallback()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_registermacrostatuschangecallback)函数注册回调，返回监听结果。

   ```c++
   void MacroStatusCallback(Camera_CaptureSession* captureSession, bool isMacroDetected)
   {
        if (isMacroDetected) {
            OH_LOG_INFO(LOG_APP, "Entering macro mode");
        }
        else {
            OH_LOG_INFO(LOG_APP, "Not entering macro mode");
        }
        
   }

    // 注册回调函数。
    Camera_ErrorCode RegisterMacroStatusCallback(Camera_CaptureSession* captureSession)
    {
        Camera_ErrorCode ret = OH_CaptureSession_RegisterMacroStatusChangeCallback(captureSession, MacroStatusCallback);
        if (ret != CAMERA_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_RegisterMacroStatusChangeCallback failed.");
        }
        return ret;
    }

    // 解注册。
    Camera_ErrorCode UnregisterMacroStatusCallback(Camera_CaptureSession* captureSession)
    {
        Camera_ErrorCode ret = OH_CaptureSession_UnregisterMacroStatusChangeCallback(captureSession, MacroStatusCallback);
        if (ret != CAMERA_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_UnregisterMacroStatusChangeCallback failed.");
        }
        return ret;
    }

   ```