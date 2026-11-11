# 低时延音频录制(C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API version 10开始支持低时延音频录制。

低时延音频录制是一种通过软硬芯协同设计实现的音频采集方案。其核心机制是通过减少buffer大小、优化读写数据架构，使该模式下音频录制具有更低的时延。

从API version 26.1.0开始，在低时延模式的基础上新增超低时延模式。该模式相比低时延模式，可以进一步降低录制时延，但是对应用处理时长和系统资源要求更高，可能会增加卡顿率，所以建议仅在下文描述的场景使用。该模式需在开发者网站申请ACL权限`ohos.permission.USE_ULTRA_FAST_AUDIO_STREAM`。

## 使用前提

- 支持低时延模式的音频输入设备。
- 可通过[OH_AudioCapturer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_getfaststatus)验证当前设备是否支持低时延模式。
- 使用超低时延模式还需满足：
  - 应用已申请超低时延音频流权限`ohos.permission.USE_ULTRA_FAST_AUDIO_STREAM`。
  - 设备支持超低时延录制，可通过[OH_AudioStreamManager_IsUltraFastRecordingSupported()](../../reference/apis-audio-kit/capi-native-audio-stream-manager-h.md#oh_audiostreammanager_isultrafastrecordingsupported)查询是否支持。
  - 超低时延模式的实际运行态可通过[OH_AudioCapturer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_getfaststatus)获取，同时可通过注册[状态变化回调](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerfaststatuschangecallback)监听获取能力变化时的通知。

## 开发指导

  以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC)。

### 简介

为使用低时延模式，开发者需要参考[推荐使用OHAudio开发音频录制功能(C/C++)](using-ohaudio-for-recording.md)进行音频开发。

当前OHAudio支持两种模式：普通模式（AUDIOSTREAM_LATENCY_MODE_NORMAL）和低时延模式（AUDIOSTREAM_LATENCY_MODE_FAST）。

### 设置低时延模式

开发者通过调用[OH_AudioStreamBuilder_SetLatencyMode()](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setlatencymode)，设置[OH_AudioStream_LatencyMode](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode)来决定音频流使用的模式。

设置低时延模式开发示例：

<!-- @[latencyMode_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStream_LatencyMode latencyMode = AUDIOSTREAM_LATENCY_MODE_FAST;
OH_AudioStreamBuilder_SetLatencyMode(builder, latencyMode);
```

### 设置超低时延模式

从API version 26.1.0开始，开发者可按以下流程使用超低时延模式进行录制：

1. 起流前，通过[OH_AudioStreamManager_IsUltraFastRecordingSupported()](../../reference/apis-audio-kit/capi-native-audio-stream-manager-h.md#oh_audiostreammanager_isultrafastrecordingsupported)查询当前设备及流参数是否支持超低时延录制。
2. 将[OH_AudioStream_LatencyMode](../../reference/apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode)设置为AUDIOSTREAM_LATENCY_MODE_ULTRA_FAST，并创建录制流。
3. 起流后，通过[OH_AudioCapturer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_getfaststatus)获取录制流的实际运行能力。
4. 通过注册状态变化回调，获取实际运行能力变化时的通知。

设置超低时延模式开发示例：

<!-- @[latencyMode_UltraFast_Capture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStreamBuilder_SetLatencyMode(builder, AUDIOSTREAM_LATENCY_MODE_ULTRA_FAST);
```

超低时延状态变化回调开发示例：

<!-- @[OnUltraFastStatusChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
void MyOnUltraFastStatusChange(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status)
{
    // 通过状态变化回调记录录制流当前的实际运行状态
    g_ultraFastStatus.store(status);
}
```

注册超低时延状态变化回调开发示例：

<!-- @[SetCapturerFastStatusChangeCallback_UltraFast](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(builder, MyOnUltraFastStatusChange, nullptr);
```

针对OHAudio开发音频录制，有以下相关实例可供参考：

- [OHAudio录制和播放](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/OHAudio)。

## 注意事项

### 低时延模式限制
在以下场景中，即使设置了低时延模式，系统仍会使用普通模式。
- 当前设备不支持低时延模式。
- 当前流格式不支持低时延模式。
- 系统低时延资源已被全部占用。
- 当前系统中存在更高优先级流（如：VOIP通话）。

超低时延模式与上述低时延模式存在类似限制，超出限制时系统会回落到低时延模式或普通模式。开发者可通过[OH_AudioCapturer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_getfaststatus)查询实际工作状态：返回AUDIOSTREAM_FASTSTATUS_ULTRA_FAST表示正处于超低时延模式，返回AUDIOSTREAM_FASTSTATUS_FAST或AUDIOSTREAM_FASTSTATUS_NORMAL表示发生了回落。

从API version 20开始，支持低时延相关查询接口。
- 开发者通过调用[OH_AudioCapturer_GetFastStatus()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_getfaststatus)来获取音频录制流是否正在低时延状态下工作。
- 在部分特殊场景（如：存在更高优先级流、当前连接设备不支持等）下，开发者可以通过调用[OH_AudioCapturer_OnFastStatusChange()](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_onfaststatuschange)来获取低时延状态改变事件。


### 使用低时延流的场景
- k歌、直播等对时延要求较高的场景，建议使用低时延模式。
- 如果使用低时延模式后，时延指标依然无法满足用户体验要求，并且与目标时延差距在10ms左右时，可以考虑使用超低时延模式，如K歌实时耳返场景（需要注意该模式的性能要求和功耗影响高于低时延模式，从而可能带来音频卡顿风险和功耗的升高，建议应用做好完备的评估和验证后再使用）。
- 该模式仅推荐在连续音频录制场景使用，不要使用在短音频的场景，否则可能会带来不好的用户体验。
- 普通录音、录像、录屏等没有实时要求的场景，不建议使用低时延模式或超低时延模式。

### 确保数据及时读入
低时延模式下，应用读取数据的频次比普通录制模式高，如果获取数据不及时可能导致杂音等问题。开发者应避免在数据回调线程中做耗时操作，确保数据回调线程可以及时返回。

### 数据回调线程
音频录制的音频数据需要通过回调接口读入。开发者要实现回调接口，使用[OH_AudioStreamBuilder_SetCapturerReadDataCallback](../../reference/apis-audio-kit/capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturerreaddatacallback)设置回调函数，在设置音频回调函数时，回调函数[OH_AudioCapturer_OnReadDataCallback](../../reference/apis-audio-kit/capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback)（从API version 12开始支持）用于读取音频数据。

开发音频录制功能的示例代码请参考：[推荐使用OHAudio开发音频录制功能(C/C++)](using-ohaudio-for-recording.md)。

设置数据回调函数示例：

<!-- @[SetCapturerReadDataCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCapturerSampleC/entry/src/main/cpp/AudioCapture.cpp) -->

``` C++
int32_t MyOnReadData_Legacy(
    OH_AudioCapturer* capturer,
    void* userData,
    void* buffer,
    int32_t length)
{
    // 从buffer中取出length长度的录音数据。
    return 0;
}
// ...
    // 配置读入音频数据回调函数。
    OH_AudioCapturer_OnReadDataCallback readDataCb = MyOnReadData_NewAPI;
    OH_AudioStreamBuilder_SetCapturerReadDataCallback(builder, readDataCb, nullptr);
```

- 为避免音频卡顿，禁止在回调方法OH_AudioCapturer_OnReadData中执行耗时操作。
- 为保证OH_AudioCapturer_OnReadData与流状态控制逻辑独立正常运行，禁止在OH_AudioCapturer_OnReadData回调方法中调用音频流控制接口。
  
    | 音频流控制接口                                                    | 说明         |
    | ------------------------------------------------------------ | ------------ |
    | OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer) | 开始录制。     |
    | OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer) | 暂停录制。     |
    | OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer) | 停止录制。     |
    | OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer) | 释放缓存数据。 |
    | OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer) | 释放录制实例。 |

    > **注意：**
    >
    > 音频流控制接口执行会有耗时（例如OH_AudioCapturer_Stop接口单次执行普遍超过50ms），应避免在主线程中直接调用，以免造成界面显示卡顿。

