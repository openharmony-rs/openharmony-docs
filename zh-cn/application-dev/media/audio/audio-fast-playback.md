# 低时延音频播放
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 10开始支持低时延音频播放。

低时延音频播放是一种通过软硬芯协同设计实现的音频渲染方案。其核心机制是通过减少buffer大小、优化读写数据架构，使该模式下音频播放具有更低的时延。

## 使用前提

- 设备支持低时延模式的音频输出设备。
- 芯片平台支持。

## 开发指导

### 简介

为使用低时延模式，开发者需要参考[使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)进行音频开发。

当前OHAudio支持两种模式：普通模式（AUDIOSTREAM_LATENCY_MODE_NORMAL）和低时延模式（AUDIOSTREAM_LATENCY_MODE_FAST）。

### 设置低时延模式

开发者通过调用[OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode)，设置[OH_AudioStream_LatencyMode()](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode)，来决定音频流使用哪种模式。

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
- 开发者通过调用[OH_AudioRenderer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_getfaststatus)来获取音频播放流是否在低时延状态下工作。
- 切换到部分特殊场景（如：更高优先级流创建、新连接设备不支持等）时，开发者通过调用[OH_AudioRenderer_OnFastStatusChange()](../../reference/apis-audio-kit/capi-native-audiorenderer-h.md#oh_audiorenderer_onfaststatuschange)来获取低时延状态改变事件。


### 使用低时延流的场景
- 游戏、k歌、直播等对时延要求较高的场景，建议使用低时延模式。
- 视频播放、音乐播放等没有实时要求的场景，不需要使用低时延模式。

### 确保数据及时提供
低时延模式下，应用提供数据的频次比普通播放模式高，如果传送数据不及时可能导致杂音等问题。

### 数据回调线程
[使用OHAudio开发音频播放功能(C/C++)](using-ohaudio-for-playback.md)提供了开发音频播放功能的示例代码。在设置回调函数时，开发者需要将OH_AudioRenderer_Callbacks对象设置给系统侧，系统侧会有频率的调用OH_AudioRenderer_Callbacks对象的OH_AudioRenderer_OnWriteData方法，向应用请求数据。回调函数的声明请查看[OH_AudioRenderer_Callbacks](../../reference/apis-audio-kit/capi-ohaudio-oh-audiorenderer-callbacks-struct.md)。
- 为避免音频卡顿，禁止在回调方法OH_AudioRenderer_OnWriteData中执行耗时操作。
- 为保证OH_AudioRenderer_OnWriteData与流状态控制逻辑独立正常运行，禁止在OH_AudioRenderer_OnWriteData回调方法中调用音频流控制接口。

    | 音频流控制接口                                                    | 说明         |
    | ------------------------------------------------------------ | ------------ |
    | OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer) | 开始播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer) | 暂停播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer) | 停止播放。     |
    | OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer) | 释放缓存数据。 |
    | OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer) | 释放播放实例。 |

