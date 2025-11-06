# 低时延音频播放(C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 10开始支持低时延音频播放。

低时延音频播放是一种通过软硬芯协同设计实现的音频渲染方案。其核心机制是通过减少buffer大小、优化读写数据架构，使该模式下音频播放具有更低的时延。

## 使用前提

- 支持低时延模式的音频输出设备。
- 可通过[OH_AudioRenderer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getfaststatus)验证当前设备是否支持低时延模式。

## 开发指导

### 简介

为使用低时延模式，开发者需要参考[使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)进行音频开发。

当前OHAudio支持两种模式：普通模式（AUDIOSTREAM_LATENCY_MODE_NORMAL）和低时延模式（AUDIOSTREAM_LATENCY_MODE_FAST）。

### 设置低时延模式

开发者通过调用[OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode)，设置[OH_AudioStream_LatencyMode()](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode)来决定音频流使用的模式。

设置低时延模式开发示例：
```cpp
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
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

从API version 20开始，支持低时延相关查询接口。
- 开发者通过调用[OH_AudioRenderer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getfaststatus)来获取音频播放流是否正在低时延状态下工作。
- 在部分特殊场景（如：存在更高优先级流、当前连接设备不支持等）下，开发者可以通过调用[OH_AudioRenderer_OnFastStatusChange()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_onfaststatuschange)来获取低时延状态改变事件。


### 使用低时延流的场景
- 游戏、k歌、直播等对时延要求较高的场景，建议使用低时延模式。
- 视频播放、音乐播放等没有实时要求的场景，不建议使用低时延模式。

### 确保数据及时提供
低时延模式下，应用提供数据的频次比普通播放模式高，如果传送数据不及时可能导致杂音等问题。开发者应避免在数据回调线程中做耗时操作，确保数据回调线程可以及时返回。

### 数据回调线程
播放的音频数据需要通过回调接口写入。开发者要实现回调接口，使用[OH_AudioStreamBuilder_SetRendererWriteDataCallback](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)设置写入音频数据的回调函数，在设置音频回调函数时，回调函数[OH_AudioRenderer_OnWriteDataCallback](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback)（从API version 12开始支持）用于写入音频数据。

开发音频播放功能的示例代码请参考：[使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)。

设置数据回调函数示例：
```cpp
// 自定义写入数据函数。
static OH_AudioData_Callback_Result MyOnWriteData(
    OH_AudioRenderer* renderer,
    void* userData,
    void* audioData,
    int32_t audioDataSize)
{
    // 将待播放的数据，按audioDataSize长度写入audioData。
    // 如果开发者不希望播放某段audioData，返回AUDIO_DATA_CALLBACK_RESULT_INVALID即可。
    return AUDIO_DATA_CALLBACK_RESULT_VALID;
}
// 配置写入音频数据回调函数。
OH_AudioRenderer_OnWriteDataCallback writeDataCb = MyOnWriteData;
OH_AudioStreamBuilder_SetRendererWriteDataCallback(builder, writeDataCb, nullptr);
```
- 为避免音频卡顿，禁止在回调方法OH_AudioRenderer_OnWriteData中执行耗时操作。
- 为保证OH_AudioRenderer_OnWriteData与流状态控制逻辑独立正常运行，禁止在OH_AudioRenderer_OnWriteData回调方法中调用音频流控制接口。

    | 音频流控制接口                                                    | 说明         |
    | ------------------------------------------------------------ | ------------ |
    | OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer) | 开始播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer) | 暂停播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer) | 停止播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer) | 释放缓存数据。 |
    | OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer) | 释放播放实例。 |

