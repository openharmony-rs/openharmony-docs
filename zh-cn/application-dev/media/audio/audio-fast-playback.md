# 低时延音频播放(C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 10开始支持低时延音频播放。

从API version 26开始支持超低时延音频播放。

低时延音频播放是一种通过软硬芯协同设计实现的音频渲染方案。其核心机制是通过减少buffer大小、优化读写数据架构，使该模式下音频播放具有更低的时延。


## 使用前提

### 低时延模式使用前提

- 支持低时延模式的音频输出设备。
- 可通过[OH_AudioRenderer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getfaststatus)验证当前设备是否支持低时延模式。

### 超低时延模式使用前提

- 申请权限`ohos.permission.USE_ULTRA_FAST_AUDIO_STREAM`，申请方式请参考[声明权限](../../security/AccessToken/declare-permissions.md)。
- 支持超低时延模式的音频输出设备。当前支持扬声器、听筒、USB耳机和USB ARM耳机，具体以设备实际配置为准。
- 非系统应用仅在USB ARM耳机上可使用超低时延模式。
- 可通过[OH_AudioStreamManager_IsUltraFastPlaybackSupported()](../../reference/apis-audio-kit/capi-native-audio-stream-manager-h.md#oh_audiostreammanager_isultrafastplaybacksupported)查询当前流类型对应的输出设备是否支持超低时延模式。

## 开发指导

  以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleC)。

### 简介

为使用低时延模式，开发者需要参考[推荐使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)进行音频开发。

当前OHAudio支持三种模式：普通模式（AUDIOSTREAM_LATENCY_MODE_NORMAL）、低时延模式（AUDIOSTREAM_LATENCY_MODE_FAST）和超低时延模式（AUDIOSTREAM_LATENCY_MODE_ULTRA_FAST）。

### 设置低时延模式

开发者通过调用[OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode)，设置[OH_AudioStream_LatencyMode](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode)来决定音频流使用的模式。

设置低时延模式开发示例：

<!-- @[OH_AudioStreamBuilder_SetLatencyMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```

设置超低时延模式开发示例：
<!-- @[OH_AudioStreamBuilder_SetLatencyMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->

``` C++
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_ULTRA_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```

针对OHAudio开发音频播放，有以下相关实例可供参考：

- [OHAudio录制和播放](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/OHAudio)。

## 注意事项

### 低时延模式限制
在以下场景中，即使设置了低时延模式，系统仍会使用普通模式。
- 当前设备不支持低时延模式。
- 当前流格式不支持低时延模式。
- 系统低时延资源已被全部占用。
- 当前系统中存在更高优先级流（如：蜂窝通话）。

### 超低时延模式限制
创建播放实例时，若应用未申请`ohos.permission.USE_ULTRA_FAST_AUDIO_STREAM`权限，或当前系统不支持超低时延能力，接口会直接返回错误码，不会创建播放实例。

创建成功后，在以下场景中，即使设置了超低时延模式，系统仍会使用低时延模式或普通模式。
- 非系统应用且当前输出设备不是USB ARM耳机，降级为低时延模式。
- 当前输出设备不支持超低时延模式，降级为低时延模式。
- 系统中超低时延流数量已达到上限（2条），新增的流降级为低时延模式。
- 系统中低时延类流（含超低时延流）数量已达到上限（6条），新增的流降级为普通模式。
- 当前系统中存在更高优先级流（如：蜂窝通话），新增的流降级为普通模式。

从API version 20开始，支持时延状态查询接口。
- 可通过[OH_AudioRenderer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getfaststatus)来获取音频播放流是否正在低时延状态下工作。
- 在部分特殊场景（如：存在更高优先级流、当前连接设备不支持等）下，开发者可以通过调用[OH_AudioRenderer_OnFastStatusChange()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_onfaststatuschange)来获取低时延状态改变事件。

> **注意：**
>
> 低时延模式下，不支持调整播放速度。<br>
> 超低时延模式下，不支持调整播放速度，也不支持设置响度增益。


### 使用低时延流的场景
- 游戏、K歌、直播等对时延要求较高的场景，建议使用低时延模式。
- 视频播放、音乐播放等对时延要求不敏感的场景，不建议使用低时延模式。
- 超低时延通路资源有限，仅建议在关键业务流上使用。

### 确保数据及时提供
低时延模式下，应用提供数据的频次比普通播放模式高，如果传送数据不及时可能导致杂音等问题。开发者应避免在数据回调线程中做耗时操作，确保数据回调线程可以及时返回。

### 数据回调线程
播放的音频数据需要通过回调接口写入。开发者要实现回调接口，使用[OH_AudioStreamBuilder_SetRendererWriteDataCallback](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)设置写入音频数据的回调函数，在设置音频回调函数时，回调函数[OH_AudioRenderer_OnWriteDataCallback](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback)（从API version 12开始支持）用于写入音频数据。

开发音频播放功能的示例代码请参考：[推荐使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。

设置数据回调函数示例：

<!-- @[Render_SetRendererWriteDataCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleC/entry/src/main/cpp/renderer.cpp) -->  

``` C++
// 自定义写入数据函数。
static OH_AudioData_Callback_Result MyOnWriteData_New(
    OH_AudioRenderer* renderer,
    void* userData,
    void* audioData,
    int32_t audioDataSize)
{
    // 将待播放的数据，按audioDataSize长度写入audioData。
    // 如果开发者不希望播放某段audioData，返回AUDIO_DATA_CALLBACK_RESULT_INVALID即可。
    size_t readCount = fread(audioData, audioDataSize, 1, g_fp);
    if (readCount == 0) {
        return AUDIO_DATA_CALLBACK_RESULT_INVALID;
    }
    if (feof(g_fp)) {
        fseek(g_fp, 0, SEEK_SET);
    }
    return AUDIO_DATA_CALLBACK_RESULT_VALID;
}
// ...
    // 配置写入音频数据回调函数。
    OH_AudioRenderer_OnWriteDataCallback writeDataCb = MyOnWriteData_New;
    OH_AudioStreamBuilder_SetRendererWriteDataCallback(builder, writeDataCb, nullptr);
```

- 为避免音频卡顿，禁止在回调函数OH_AudioRenderer_OnWriteDataCallback中执行耗时操作。
- 为保证OH_AudioRenderer_OnWriteDataCallback与流状态控制逻辑独立正常运行，禁止在OH_AudioRenderer_OnWriteDataCallback回调函数中调用音频流控制接口。

    | 音频流控制接口                                                    | 说明         |
    | ------------------------------------------------------------ | ------------ |
    | OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer) | 开始播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer) | 暂停播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer) | 停止播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer) | 释放缓存数据。 |
    | OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer) | 释放播放实例。 |

    > **注意：**
    >
    > 音频流控制接口执行存在耗时（例如OH_AudioRenderer_Stop接口需要播完缓存，单次执行普遍超过50ms），应避免在主线程中直接调用，以免造成界面显示卡顿。

