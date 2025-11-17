# Macro Photography Settings (C/C++)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Starting from API version 19, you can configure macro photography. This feature allows the camera to focus closely and capture detailed images of small objects through optimized optical design and algorithms.

## How to Develop

Read [Camera](../../reference/apis-camera-kit/capi-oh-camera.md) for the API reference.

1. Import the NDK.  

   ```c++
   // Include the NDK header files.
   #include "hilog/log.h"
   #include "ohcamera/camera.h"
   #include "ohcamera/camera_input.h"
   #include "ohcamera/capture_session.h"
   #include "ohcamera/camera_manager.h"
   ```

2. Link the dynamic libraries in the CMake script.

    ```txt
    target_link_libraries(entry PUBLIC
        libace_napi.z.so
        libohcamera.so
        libhilog_ndk.z.so
    )
    ```

3. Call [OH_CaptureSession_IsMacroSupported()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_ismacrosupported) to check whether the current device supports macro photography.

   ```c++
   bool IsMacroSupported(Camera_CaptureSession* captureSession)
   {
        // Check whether the device supports macro photography.
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

4. Call [OH_CaptureSession_EnableMacro()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_enablemacro) to enable or disable macro photography.

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


## Status Listening

Starting from API version 20, you can listen for macro photography status changes.

Call [OH_CaptureSession_RegisterMacroStatusChangeCallback()](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_registermacrostatuschangecallback) to register a callback for listening.

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

    // Register a callback.
    Camera_ErrorCode RegisterMacroStatusCallback(Camera_CaptureSession* captureSession)
    {
        Camera_ErrorCode ret = OH_CaptureSession_RegisterMacroStatusChangeCallback(captureSession, MacroStatusCallback);
        if (ret != CAMERA_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_RegisterMacroStatusChangeCallback failed.");
        }
        return ret;
    }

    // Stop the listening.
    Camera_ErrorCode UnregisterMacroStatusCallback(Camera_CaptureSession* captureSession)
    {
        Camera_ErrorCode ret = OH_CaptureSession_UnregisterMacroStatusChangeCallback(captureSession, MacroStatusCallback);
        if (ret != CAMERA_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_CaptureSession_UnregisterMacroStatusChangeCallback failed.");
        }
        return ret;
    }

   ```
