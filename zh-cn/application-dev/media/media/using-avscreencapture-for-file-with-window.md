# 使用AVScreenCapture窗口级录屏写文件(C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yxc2-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->


从API version 10开始，开发者可通过AVScreenCapture模块的C API接口实现窗口/屏幕录制，采集麦克风和设备音视频源数据。

本开发指导将以完成一次指定窗口录制的过程为例，向开发者讲解如何使用AVScreenCapture模块的C API接口进行指定窗口录屏。

- 录制某个指定窗口，需要设置指定窗口ID。该场景下，启动录屏后，会弹出选择共享内容弹窗。详细的API声明请参考[OH_CaptureMode](../../reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturemode)中的OH_CAPTURE_SPECIFIED_WINDOW模式。
- 推荐使用系统Picker列表弹窗，选择期望录制的窗口。使用[OH_AVScreenCapture_StrategyForPickerPopUp](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpickerpopup)设置是否弹出屏幕捕获Picker。从API version 20开始，支持在PC/2in1设备上设置弹出屏幕捕获Picker；从API version 23开始，支持在Phone/Tablet设备上设置弹出屏幕捕获Picker。

## 申请权限

在开发此功能前，开发者应根据实际需求申请相关权限：
- 如果配置了采集麦克风音频数据，需[向用户申请授权](../../security/AccessToken/request-user-authorization.md)配置麦克风权限**ohos.permission.MICROPHONE**和申请[长时任务(ArkTS)](../../task-management/continuous-task.md)。
- 从API version 22开始，在PC/2in1设备上对应用进行录屏时，可通过申请权限**ohos.permission.TIMEOUT_SCREENOFF_DISABLE_LOCK**，实现在屏幕熄灭但不锁屏的场景下，继续保持录制的效果。配置方式请参见[声明权限](../../security/AccessToken/declare-permissions.md)。
- 从API version 22开始，在PC/2in1设备上对应用进行录屏时，可通过申请权限**ohos.permission.CUSTOM_SCREEN_RECORDING**，实现在录制屏幕时不再弹出隐私告警弹窗。配置方式请参见[受限开放权限](../../security/AccessToken/restricted-permissions.md)。

## 开发步骤及注意事项

使用AVScreenCapture时要明确其状态的变化，在创建实例后，调用对应的方法可以进入指定的状态实现对应的行为。

在确定的状态下执行不合适的方法会导致AVScreenCapture发生错误，调用状态转换方法前需检查当前状态，避免程序运行异常。

**在CMake脚本中链接动态库**

```c++
target_link_libraries(entry PUBLIC libnative_avscreen_capture.so)
```

1. 添加头文件。

   ```c++
   #include "napi/native_api.h"
   #include <multimedia/player_framework/native_avscreen_capture.h>
   #include <multimedia/player_framework/native_avscreen_capture_base.h>
   #include <multimedia/player_framework/native_avscreen_capture_errors.h>
   #include <fcntl.h>
   #include <string>
   #include <unistd.h>
   ```

2. 调用[OH_AVScreenCapture_Create](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_create)方法创建AVScreenCapture实例capture。

   ```c++
   OH_AVScreenCapture* capture = OH_AVScreenCapture_Create();
   ```

3. 调用[OH_AVScreenCapture_Init](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_init)方法配置屏幕录制参数。

   创建AVScreenCapture实例capture后，可以设置屏幕录制所需要的参数。

   ```c++
   // 录屏时获取麦克风或者内录，内录参数为必填。如果同时设置了内录和麦克风，则两者的参数设置需要一致。
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

   // 录屏音频输出规格配置。audioBitrate保证输出文件的比特率为设置的预期比特率，和audioSampleRate无强关联。
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
       .dataType = OH_CAPTURE_FILE,
       .audioInfo = audioInfo,
       .videoInfo = videoInfo
   };
   ```

   方式一：需传入期望录制的窗口ID进行录屏。

   ```c++
   // 如果期望录制单个窗口，需传入单个窗口ID；如果期望同时录制多个窗口，需传入期望录制的窗口ID列表。
   std::vector<int32_t> missionIds = {88}; // 指定录制的窗口ID。
   config.videoInfo.videoCapInfo.missionIDs = missionIds.data();
   config.videoInfo.videoCapInfo.missionIDsLen = static_cast<int32_t>(missionIds.size());
   config.captureMode = OH_CAPTURE_SPECIFIED_WINDOW; // 设置录屏模式为录制指定窗口。

   // 设置为false，代表录屏启动后不弹出系统Picker，弹出隐私保护弹窗。
   OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, false);
   OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);

   OH_AVScreenCapture_Init(capture, config);
   ```

   方式二（推荐）：通过弹出屏幕捕获Picker列表方式，选择已打开的应用窗口进行窗口级录屏。

   ```c++
   // 通过弹出屏幕捕获Picker列表方式，选择已打开的应用窗口进行窗口级录屏。
   OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
   OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
   OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);

   OH_AVScreenCapture_Init(capture, config);
   ```

4. 调用[OH_AVScreenCapture_StartScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_startscreenrecording)方法开始进行窗口级录制。

   ```c++
   OH_AVScreenCapture_StartScreenRecording(capture);
   ```

5. 调用[OH_AVScreenCapture_StopScreenRecording](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_stopscreenrecording)方法停止录制。

   ```c++
   OH_AVScreenCapture_StopScreenRecording(capture);
   ```

6. 调用[OH_AVScreenCapture_Release](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_release)方法销毁实例，释放资源。

   ```c++
   OH_AVScreenCapture_Release(capture);
   ```

## 完整示例

下面展示了使用AVScreenCapture窗口级录屏写文件的完整示例代码。

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
        // 处理状态变更。
    }
    if (stateCode == OH_SCREEN_CAPTURE_STATE_STOPPED_BY_CALL ||
        stateCode == OH_SCREEN_CAPTURE_STATE_STOPPED_BY_USER_SWITCHES) {
        // 录屏中断状态处理。
    }
    if (stateCode == OH_SCREEN_CAPTURE_STATE_INTERRUPTED_BY_OTHER) {
        // 处理状态变更。
    }
    (void)userData;
}

// 录屏内容变更回调函数OnCaptureContentChanged()。
void OnCaptureContentChanged(struct OH_AVScreenCapture *capture, OH_AVScreenCaptureContentChangedEvent event, OH_Rect *area, void *userData) {
    (void)capture;
    if (event == OH_SCREEN_CAPTURE_CONTENT_HIDE) {
        // 处理录屏内容变为隐藏。
    }
    if (event == OH_SCREEN_CAPTURE_CONTENT_VISIBLE) {
        // 处理录屏内容变为可见。
        // 录屏内容变为可见时，可通过回调回传的area参数，获取窗口的位置信息。
    }
    if (event == OH_SCREEN_CAPTURE_CONTENT_UNAVAILABLE) {
        // 处理录屏内容变为不可用，如录屏窗口关闭。
    }
    (void)area;
    (void)userData;
}

// 确认用户选择结果的回调函数OnUserSelected()。
void OnUserSelected(OH_AVScreenCapture* capture, OH_AVScreenCapture_UserSelectionInfo* selections, void *userData) {
    (void)capture;
    (void)userData;
    int selectType = -1;
    uint64_t displayId = 1000;

    // 通过获取接口，拿到对应的选择类型和屏幕ID。OH_AVScreenCapture_UserSelectionInfo* selections仅在OnUserSelected回调中有效。
    OH_AVSCREEN_CAPTURE_ErrCode errorSelectType = OH_AVScreenCapture_GetCaptureTypeSelected(selections, &selectType);
    OH_AVSCREEN_CAPTURE_ErrCode errorDisplayId = OH_AVScreenCapture_GetDisplayIdSelected(selections, &displayId);
}

// 开始录屏时调用StartScreenCapture。
static napi_value StartScreenCapture(napi_env env, napi_callback_info info) {
    // 初始化录屏参数，传入配置信息OH_AVScreenCaptureConfig。
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
        .videoSource = OH_VIDEO_SOURCE_SURFACE_RGBA,
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

    // 实例化ScreenCapture。
    capture = OH_AVScreenCapture_Create();

    OH_RecorderInfo recorderInfo;
    const std::string SCREEN_CAPTURE_ROOT = "/data/storage/el2/base/files/";
    outputFd = open((SCREEN_CAPTURE_ROOT + "screen01.mp4").c_str(), O_RDWR | O_CREAT, 0777);

    // 处理打开失败或创建失败的情况，返回报错结果。
    if (outputFd == -1) {
        napi_value errCode;
        napi_create_double(env, AV_SCREEN_CAPTURE_ERR_IO, &errCode);
        return errCode;
    }

    std::string fileUrl = "fd://" + std::to_string(outputFd);
    recorderInfo.url = const_cast<char *>(fileUrl.c_str());
    recorderInfo.fileFormat = OH_ContainerFormatType::CFT_MPEG_4;
    config.recorderInfo = recorderInfo;

    // 设置状态回调。
    OH_AVScreenCapture_SetStateCallback(capture, OnStateChange, nullptr);

    // 可选，设置录屏内容变化回调。
    OH_Rect* area = nullptr;
    OH_AVScreenCapture_SetCaptureContentChangedCallback(capture, OnCaptureContentChanged, area);

    // 推荐使用系统Picker列表弹窗，选择期望录制的窗口。
    OH_AVScreenCapture_CaptureStrategy* strategy = OH_AVScreenCapture_CreateCaptureStrategy();
    OH_AVScreenCapture_StrategyForPickerPopUp(strategy, true);
    OH_AVScreenCapture_SetCaptureStrategy(capture, strategy);

    // 可选，设置确认用户选择结果的回调函数，必须在开始录屏前调用。
    OH_AVScreenCapture_SetSelectionCallback(capture, OnUserSelected, nullptr);

    // 可选，设置光标显示开关，开始录屏前后均可调用。
    OH_AVScreenCapture_ShowCursor(capture, false);

    // 进行初始化操作。
    int32_t retInit = OH_AVScreenCapture_Init(capture, config);

    // 开始录屏。
    int32_t retStart = OH_AVScreenCapture_StartScreenRecording(capture);

    // 开始录屏失败的情况处理，返回报错结果。
    if (retStart != AV_SCREEN_CAPTURE_ERR_OK) {
        napi_value errCode;
        napi_create_double(env, retStart, &errCode);
        return errCode;
    }

    // 结束录屏参见StopScreenCapture。
    
    // 返回调用结果，示例仅返回示例值。
    napi_value code;
    napi_create_double(env, AV_SCREEN_CAPTURE_ERR_OK, &code);

    return code;
}

// 结束录屏时调用StopScreenCapture。
static napi_value StopScreenCapture(napi_env env, napi_callback_info info) {
    if (capture != nullptr) {
        // 结束录屏。
        int32_t retStop = OH_AVScreenCapture_StopScreenRecording(capture);

        // 关闭文件访问。
        close(outputFd);

        // 结束录屏失败的情况处理，返回报错结果。
        if (retStop != AV_SCREEN_CAPTURE_ERR_OK) {
            napi_value errCode;
            napi_create_double(env, retStop, &errCode);
            return errCode;
        }

        // 释放ScreenCapture。
        int32_t retRelease = OH_AVScreenCapture_Release(capture);

        // 释放ScreenCapture失败情况下处理，返回报错结果。
        if (retRelease != AV_SCREEN_CAPTURE_ERR_OK) {
            napi_value errCode;
            napi_create_double(env, retRelease, &errCode);
            return errCode;
        }

        capture = nullptr;
    }

    // 返回成功结果。
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
## 运行完整示例
 
1. 新建工程，下载[示例工程](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/ScreenCapture/ScreenCaptureSample)，并将示例工程的以下资源复制到对应目录。

   ```txt
   AVPlayerNDKVideo
   entry/src/main/ets/
   └── pages
       └── Index.ets (录屏主界面)
   entry/src/main/
   ├── cpp
   │   ├── types
   │   │   └── libentry
   │   │       └── Index.d.ts (NDK函数对应的js映射)
   │   ├── CMakeLists.txt (CMake脚本)
   │   └── napi_init.cpp  (NDK函数)
   └── resources
       ├── base
       │   ├── element
       │   │   ├── color.json
       │   │   ├── float.json
       │   │   └── string.json
       │   │── media
       │   └── profile  
       │       ├── backup_config.json
       │       └── main_pages.json
       └── dark
           └── element
               └── color.json
   ```
2. 编译新建工程并运行。
