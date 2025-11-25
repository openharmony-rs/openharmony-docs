# Using AVScreenCapture to Capture Screens and Write Them to Files (C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

Screen capture is mainly used to record the main screen.

You can call the C APIs of the [AVScreenCapture](media-kit-intro.md#avscreencapture) module to record the screen and collect audio and video source data output by the device and microphone. You can call the APIs to obtain audio and video files and transfer the files to other modules for playback or processing. In this way, screen content can be shared in the form of files.

The AVScreenCapture, Window, and Graphics modules together implement the entire video capture process.

The full-screen capture process involves creating an AVScreenCapture instance, configuring audio and video capture parameters, starting and stopping screen capture, and releasing the instance.

If you are in a call when screen capture starts or a call is coming during screen capture, screen capture automatically stops, and the **OH_SCREEN_CAPTURE_STATE_STOPPED_BY_CALL** status is reported.

Screen capture automatically stops upon system user switching, and **OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER_SWITCHES** is reported.

This topic describes how to use the AVScreenCapture APIs to carry out one-time screen capture. For details about the API reference, see [AVScreenCapture](../../reference/apis-media-kit/capi-avscreencapture.md).

If microphone data collection is configured, configure the permission ohos.permission.MICROPHONE and request a continuous task. For details, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md) and [Continuous Task](../../task-management/continuous-task.md).

Starting from API version 22, when you perform screen capture for an application on a PC/2-in-1 device, you can request the ohos.permission.TIMEOUT_SCREENOFF_DISABLE_LOCK permission to maintain capture even when the screen is off but not locked. For details about the configuration, [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

Starting from API version 22, when you perform screen capture for an application on a PC/2-in-1 device, you can request the ohos.permission.CUSTOM_SCREEN_RECORDING permission to prevent the privacy protection pop-up from being displayed during screen capture. For details about how to request the permission, see [Requesting Restricted Permissions](../../security/AccessToken/restricted-permissions.md).
## How to Develop

After an AVScreenCapture instance is created, different APIs can be called to switch the AVScreenCapture to different states and trigger the required behavior.
If an API is called when the AVScreenCapture is not in the given state, the system may throw an exception or generate other undefined behavior. Therefore, you are advised to check the AVScreenCapture state before triggering state transition.

**Linking the Dynamic Libraries in the CMake Script**

```c++
target_link_libraries(entry PUBLIC libnative_avscreen_capture.so)
```

1. Add the header files.

    ```c++
    #include "napi/native_api.h"
    #include <multimedia/player_framework/native_avscreen_capture.h>
    #include <multimedia/player_framework/native_avscreen_capture_base.h>
    #include <multimedia/player_framework/native_avscreen_capture_errors.h>
    #include <fcntl.h>
    #include <string>
    #include <unistd.h>
    ```

2. Create an AVScreenCapture instance, named **capture** in this example.

    ```c++
    OH_AVScreenCapture* capture = OH_AVScreenCapture_Create();
    ```

3. Set screen capture parameters.

    After creating the capture instance, you can set the parameters required for screen capture.

    By default, internal capture is used when captured files need to be stored. The microphone, which can be dynamically turned on or off, can be used for both internal capture and external capture.

    A callback function must be set to listen for the capture status when captured files need to be stored.

    ```c++
    // Obtain the external capture (using microphones) or internal capture information. The internal capture parameters are mandatory. If both parameters are set, the parameter settings for internal capture and external capture must be the same.
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
        .videoFrameWidth = 768,
        .videoFrameHeight = 1280,
        .videoSource = OH_VIDEO_SOURCE_SURFACE_RGBA
    };

    OH_VideoEncInfo videoEncInfo = {
        .videoCodec = OH_H264,
        .videoBitrate = 2000000,
        .videoFrameRate = 30
    };

    OH_AudioInfo audioInfo = {
        .innerCapInfo = innerCapInfo,
        .audioEncInfo = audioEncInfo
    };

    OH_VideoInfo videoInfo = {
        .videoCapInfo = videoCapInfo,
        .videoEncInfo = videoEncInfo
    };

    config = {
        .captureMode = OH_CAPTURE_HOME_SCREEN,
        .dataType = OH_CAPTURE_FILE,
        .audioInfo = audioInfo,
        .videoInfo = videoInfo,
    };

    OH_AVScreenCapture_Init(capture, config);
    ```

4. Call **StartScreenRecording()** to start screen recording.

    ```c++
    OH_AVScreenCapture_StartScreenRecording(capture);
    ```

5. Call **StopScreenRecording()** to stop screen recording.

    ```c++
    OH_AVScreenCapture_StopScreenRecording(capture);
    ```

6. Call **Release()** to release the instance.

    ```c++
    OH_AVScreenCapture_Release(capture);
    ```

## Complete Sample Code

Refer to the sample code below to implement captured file storage using AVScreenCapture.

```c++
#include "napi/native_api.h"
#include <multimedia/player_framework/native_avscreen_capture.h>
#include <multimedia/player_framework/native_avscreen_capture_base.h>
#include <multimedia/player_framework/native_avscreen_capture_errors.h>
#include <fcntl.h>
#include <string>
#include <unistd.h>

int32_t outputFd;
struct OH_AVScreenCapture* capture;

void OnStateChange(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureStateCode stateCode, void *userData) {
    (void)capture;
    
    if (stateCode == OH_SCREEN_CAPTURE_STATE_STARTED) {
        // Process the state change.
    }
    if (stateCode == OH_SCREEN_CAPTURE_STATE_STOPPED_BY_CALL ||
        stateCode == OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER_SWITCHES) {
        // Process screen capture interruption.
    }
    if (stateCode == OH_SCREEN_CAPTURE_STATE_INTERRUPTED_BY_OTHER) {
        // Process the state change.
    }
    (void)userData;
}

// The callback OnDisplaySelected() is invoked to obtain the display ID.
void OnDisplaySelected(struct OH_AVScreenCapture *capture, uint64_t displayId, void *userData) {
    (void)capture;
    (void)displayId;
    (void)userData;
}

// OnCaptureContentChanged(), a callback function invoked when screen capture content changes.
void OnCaptureContentChanged(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect *area, void *userData) {
    (void)capture;
    if (event == OH_SCREEN_CAPTURE_CONTENT_HIDE) {
        // Process the event indicating that screen capture content is hidden.
    }
    if (event == OH_SCREEN_CAPTURE_CONTENT_VISIBLE) {
        // Process the event indicating that screen capture content is visible.
        // Obtain the window area information from the area parameter returned by the callback function when the screen capture content becomes visible.
    }
    if (event == OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE) {
        // Process the event indicating that screen capture content becomes unavailable, for example, the screen capture window is closed.
    }
    (void)area;
    (void)userData;
}

// The callback OnUserSelected() is invoked to handle user selection results on the manual confirmation UI.
void OnUserSelected(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData) {
    (void)capture;
    (void)userData;
    int* selectType = new int;
    uint64_t* displayId = new uint64_t;

    // Obtain the selection type and display ID through the API. OH_AVScreenCapture_UserSelectionInfo* selections is valid only in the OnUserSelected callback.
    OH_AVSCREEN_CAPTURE_ErrCode errorSelectType = OH_AVScreenCapture_GetCaptureTypeSelected(selections, selectType);
    OH_AVSCREEN_CAPTURE_ErrCode errorDisplayId = OH_AVScreenCapture_GetDisplayIdSelected(selections, displayId);

    // Release the allocated memory after use.
    delete selectType, displayId;
}

// Call StartScreenCapture to start screen capture.
static napi_value StartScreenCapture(napi_env env, napi_callback_info info) {
    OH_AVScreenCaptureConfig config;
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
        .audioCodecformat = OH_AudioCodecFormat::OH_AAC_LC
    };

    OH_VideoCaptureInfo videoCapInfo = {
        .videoFrameWidth = 768, 
        .videoFrameHeight = 1280, 
        .videoSource = OH_VIDEO_SOURCE_SURFACE_RGBA
    };

    OH_VideoEncInfo videoEncInfo = {
        .videoCodec = OH_VideoCodecFormat::OH_H264, 
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
        .dataType = OH_CAPTURE_FILE,
        .audioInfo = audioInfo,
        .videoInfo = videoInfo,
    };

    // Instantiate AVScreenCapture.
    capture = OH_AVScreenCapture_Create();

    // Initialize the screen capture parameters and pass in an OH_AVScreenRecorderConfig struct.
    OH_RecorderInfo recorderInfo;
    const std::string SCREEN_CAPTURE_ROOT = "/data/storage/el2/base/files/";
    outputFd = open((SCREEN_CAPTURE_ROOT + "screen01.mp4").c_str(), O_RDWR | O_CREAT, 0777);

    // If opening or creation fails, handle the failure and return the error information.
    if (outputFd == -1) {
        napi_value errCode;
        napi_create_double(env, AV_SCREEN_CAPTURE_ERR_IO, &errCode);
        return errCode;
    }

    std::string fileUrl = "fd://" + std::to_string(outputFd);
    recorderInfo.url = const_cast<char *>(fileUrl.c_str());
    recorderInfo.fileFormat = OH_ContainerFormatType::CFT_MPEG_4;
    config.recorderInfo = recorderInfo;

    // Set a callback to respond to state changes.
    OH_AVScreenCapture_SetStateCallback(capture, OnStateChange, nullptr);

    // (Optional) Set a callback for screen capture content changes.
    OH_Rect* area = nullptr;
    OH_AVScreenCapture_SetCaptureContentChangedCallback(capture, OnCaptureContentChanged, area);

    // (Optional) Set the privacy window masking mode.
    int value = 0;
    OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
    OH_AVScreenCapture_StrategyForPrivacyMaskMode(strategy, value);
    OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);

    // (Optional) Set a callback to obtain the display ID. This operation must be performed before screen capture starts.
    OH_AVScreenCapture_SetDisplayCallback(capture, OnDisplaySelected, nullptr);

    // (Optional) Set a callback to handle user selection results on the manual confirmation UI. This operation must be performed before screen capture starts.
    OH_AVScreenCapture_SetSelectionCallback(capture, OnUserSelected, nullptr);

    // (Optional) Set the cursor display switch. This operation can be performed before or after screen capture starts.
    OH_AVScreenCapture_ShowCursor(capture, false);

    // Initialize AVScreenCapture.
    int32_t retInit = OH_AVScreenCapture_Init(capture, config);

    // Optional (supported since API version 20) Set the coordinates and size of the area to capture. The example below creates a 100 px * 100 px rectangle area starting at (0, 0). This API can also be set after screen capture starts.
    OH_Rect* region = new OH_Rect;
    region->x = 0;
    region->y = 0;
    region->width = 100;
    region->height = 100;
    uint64_t regionDisplayId = 0; // ID of the display where the rectangle area is located.
    OH_AVScreenCapture_SetCaptureArea(capture, regionDisplayId, region);
    
    // Release the allocated memory.
    delete region;

    // Start screen capture.
    int32_t retStart = OH_AVScreenCapture_StartScreenRecording(capture);

    // If starting screen capture fails, handle the failure and return the error information.
    if (retStart != AV_SCREEN_CAPTURE_ERR_OK) {
        napi_value errCode;
        napi_create_double(env, retStart, &errCode);
        return errCode;
    }

    // Call StopScreenCapture to stop screen capture.
    
    // Return the call result. In the example, only a random number is returned.
    napi_value code;
    napi_create_double(env, AV_SCREEN_CAPTURE_ERR_OK, &code);

    return code;
}

// Call StopScreenCapture to stop screen capture.
static napi_value StopScreenCapture(napi_env env, napi_callback_info info) {
    if (capture != nullptr) {
        // Stop screen capture.
        int32_t retStop = OH_AVScreenCapture_StopScreenRecording(capture);

        // Close the file access.
        close(outputFd);

        // If stopping screen capture fails, handle the failure and return the error information.
        if (retStop != AV_SCREEN_CAPTURE_ERR_OK) {
            napi_value errCode;
            napi_create_double(env, retStop, &errCode);
            return errCode;
        }

        // Release the AVScreenCapture instance.
        int32_t retRelease = OH_AVScreenCapture_Release(capture);

        // If releasing the AVScreenCapture instance fails, handle the failure and return the error information.
        if (retRelease != AV_SCREEN_CAPTURE_ERR_OK) {
            napi_value errCode;
            napi_create_double(env, retRelease, &errCode);
            return errCode;
        }

        capture = nullptr;
    }

    // Return a success message.
    napi_value code;
    napi_create_double(env, AV_SCREEN_CAPTURE_ERR_OK, &code);

    return code;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports) {
    napi_property_descriptor desc[] = {
        {"startScreenCapture", nullptr, StartScreenCapture, nullptr, nullptr, nullptr, napi_default, nullptr},
        {"stopScreenCapture", nullptr, StopScreenCapture, nullptr, nullptr, nullptr, napi_default, nullptr}};
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END

static napi_module demoModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = ((void *)0),
    .reserved = {0},
};

extern "C" __attribute__((constructor)) void RegisterEntryModule(void) { napi_module_register(&demoModule); }
```
