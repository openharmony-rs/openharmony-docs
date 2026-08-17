# native_audiostreambuilder.h

## 概述

Declare audio stream builder related interfaces.

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)](#oh_audiostreambuilder_create) | 创建一个输入或者输出类型的音频流构造器。<br>当构造器不再使用时，需要调用[OH_AudioStreamBuilder_Destroy](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy)销毁。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)](#oh_audiostreambuilder_destroy) | 销毁一个音频流构造器。<br>当构造器不再使用时，需要调用该函数销毁。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)](#oh_audiostreambuilder_setsamplingrate) | 设置音频流的采样率属性。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)](#oh_audiostreambuilder_setchannelcount) | 设置音频流的通道数属性。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)](#oh_audiostreambuilder_setsampleformat) | 设置音频流的采样格式属性。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)](#oh_audiostreambuilder_setencodingtype) | 设置音频流的编码类型属性。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)](#oh_audiostreambuilder_setlatencymode) | 设置音频流的时延模式。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)](#oh_audiostreambuilder_setchannellayout) | 设置音频流的声道布局。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)](#oh_audiostreambuilder_setrendererinfo) | 设置输出音频流的工作场景。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)](#oh_audiostreambuilder_setcapturerinfo) | 设置输入音频流的工作场景。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setrenderercallback) | 设置输出音频流的回调。(API20废弃) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setrendereroutputdevicechangecallback) | 设置输出音频流设备变更的回调。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)](#oh_audiostreambuilder_setrendererprivacy) | Set the privacy of audio render. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setcapturercallback) | Set the callbacks for the capturer client(API20废弃) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)](#oh_audiostreambuilder_generaterenderer) | Create the audio renderer client.The AudioRenderer instance is used to play streaming audio data.When using AudioRenderer apis, there are many instructions for applicationto achieve better performance and lower power consumption:In music or audiobook background playback situation, you can have low powerconsumption by following this best practices document **Low-Power Rules in Music Playback Scenarios**.And for navigation situation, you can follow **Low-Power Rules in Navigation and Positioning Scenarios**.Application developer should also be careful when app goes to background, please check if your audio playbackis still needed, see **Audio Resources** in best practices document.And avoiding to send silence audio data continuously to waste system resources, otherwise system will takecontrol measures when this behavior is detected, see **Audio Playback** in best practices document.If you want to use AudioRenderer api to implement a music playback application, there are also many interactivescenes to consider, see **Developing an Audio Application** in best practices document. |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)](#oh_audiostreambuilder_generatecapturer) | 创建输入音频流实例。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)](#oh_audiostreambuilder_setframesizeincallback) | 用于播放时设置每次回调的帧长，帧长至少为音频硬件一次处理的数据大小，并且小于内部缓冲容量的一半。<br>低时延播放：frameSize可设置为5ms、10ms、15ms、20ms音频数据对应的帧长。<br>普通通路播放：frameSize可设置为20ms-100ms音频数据对应的帧长。例如，当采样率48000Hz时，20ms音频数据对应的帧长计算方式为：frameSize = 48000 * 0.02，即960个采样点数。当frameSize为960时，对应的数据回调的长度为960 * 声道数 * 采样位宽（字节数）。比如双声道16bit时，length为960 * 2 * 2 = 3840。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)](#oh_audiostreambuilder_setwritedatawithmetadatacallback) | 设置同时写入音频数据和元数据的回调。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)](#oh_audiostreambuilder_setrendererinterruptmode) | 设置流客户端的中断模式。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallback) | 设置写入音频数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallbackadvanced) | 设置写入音频数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)类似。<br>如果同时设置该回调和OH_AudioStreamBuilder_SetRendererWriteDataCallback，只有最后一次设置的回调生效。<br>与OH_AudioStreamBuilder_SetRendererWriteDataCallback不同，OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced设置的回调函数，允许应用传入可变长度的音频数据，并通知系统写入的数据长度。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)](#oh_audiostreambuilder_setvolumemode) | 设置音频流音量模式。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setrendererinterruptcallback) | 设置输出音频流中断事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setrenderererrorcallback) | 设置输出音频流错误事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerreaddatacallback) | 设置输入音频流读取数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerdevicechangecallback) | 设置输入音频流设备变更的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerinterruptcallback) | 设置输入音频流中断事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setcapturererrorcallback) | 设置输入音频流错误事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)](#oh_audiostreambuilder_setcapturerwillmutewheninterrupted) | 设置输入音频流是否启用静音打断模式。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setrendererfaststatuschangecallback) | 设置音频播放过程中低时延状态改变事件的回调函数。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setcapturerfaststatuschangecallback) | 设置音频录制过程中低时延状态改变事件的回调函数。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)](#oh_audiostreambuilder_setcapturerloopbackeffectenabled) | 设置音频录制流是否采集带音频混响效果的音频数据。当音频环回设置为硬件模式并启用混响效果时，低时延模式的采集器可以获取到具备混响效果的录音数据。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)](#oh_audiostreambuilder_setplaybackcapturemode) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)](#oh_audiostreambuilder_setsensitiverecordpermitcallback) | 设置蜂窝通话下行录音风险提示语播放结束的回调函数。仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype).AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。此回调必须成功设置，否则采集器无法创建。音频采集器创建后，风险提示语将自动添加到发送给通话对方的语音数据中。应用应等待回调结果后再启动采集器，否则[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)将返回错误。请确保音频采集器在蜂窝通话开始后创建，否则[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)将返回错误。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)](#oh_audiostreambuilder_setcellularrecordsecurityparams) | 设置蜂窝通话下行录音的电话号码和安全令牌。仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype).AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。电话号码和安全令牌将用于校验蜂窝通话下行采集器是否匹配对应的蜂窝通话，必须成功设置，否则采集器无法创建。 |

## 函数说明

### OH_AudioStreamBuilder_Create()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)
```

**描述**

创建一个输入或者输出类型的音频流构造器。<br>当构造器不再使用时，需要调用[OH_AudioStreamBuilder_Destroy](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy)销毁。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)** builder | 用于接收创建的构造器实例。 |
| [OH_AudioStream_Type](capi-native-audiostream-base-h.md#oh_audiostream_type) type | 构造器的流类型。AUDIOSTREAM_TYPE_RENDERER或AUDIOSTREAM_TYPE_CAPTURER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         </ul> |

### OH_AudioStreamBuilder_Destroy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)
```

**描述**

销毁一个音频流构造器。<br>当构造器不再使用时，需要调用该函数销毁。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) Execution status exception.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetSamplingRate()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)
```

**描述**

设置音频流的采样率属性。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t rate | 音频流采样率。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.The param of rate invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetChannelCount()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)
```

**描述**

设置音频流的通道数属性。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t channelCount | 音频流通道数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.The param of channelCount invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetSampleFormat()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)
```

**描述**

设置音频流的采样格式属性。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) format | 音频流采样格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetEncodingType()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)
```

**描述**

设置音频流的编码类型属性。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | 音频流编码类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetLatencyMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)
```

**描述**

设置音频流的时延模式。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode) latencyMode | 音频流时延模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetChannelLayout()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)
```

**描述**

设置音频流的声道布局。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioChannelLayout](../AVCodecKit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频流声道布局。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetRendererInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)
```

**描述**

设置输出音频流的工作场景。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | 输出音频流的使用场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.The param of usage invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetCapturerInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)
```

**描述**

设置输入音频流的工作场景。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | 输入音频流的使用场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.The param of sourceType invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetRendererCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)
```

**描述**

设置输出音频流的回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Set the callback functions separately using OH_AudioStreamBuilder_SetRendererWriteDataCallback,OH_AudioStreamBuilder_SetRendererInterruptCallback, OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallbackand OH_AudioStreamBuilder_SetRendererErrorCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_Callbacks](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) callbacks | 将被用来处理输出音频流相关事件的回调函数。 |
| void* userData | 指向通过回调函数传递的应用数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：<br>     <br>1. 参数builder为nullptr；<br>     <br>2. StreamType无效。 |

### OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)
```

**描述**

设置输出音频流设备变更的回调。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OutputDeviceChangeCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_outputdevicechangecallback) callback | 将被用来处理输出流设备变更相关事件的回调函数。 |
| void* userData | 指向通过回调函数传递的应用数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：<br>     <br>1. 参数builder为nullptr；<br>     <br>2. StreamType无效。 |

### OH_AudioStreamBuilder_SetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)
```

**描述**

Set the privacy of audio render.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | Builder provided by OH_AudioStreamBuilder_Create() |
| [OH_AudioStream_PrivacyType](capi-native-audiostream-base-h.md#oh_audiostream_privacytype) privacy | Privacy type. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.StreamType invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetCapturerCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)
```

**描述**

Set the callbacks for the capturer client

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Set the callback functions separately using OH_AudioStreamBuilder_SetCapturerReadDataCallback,OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback, OH_AudioStreamBuilder_SetCapturerInterruptCallbackand OH_AudioStreamBuilder_SetCapturerErrorCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder |  |
| [OH_AudioCapturer_Callbacks](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) callbacks |  |
| [OH_AudioCapturer_Callbacks](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) callbacks | Callbacks to the functions that will process capturer stream. |
| void* userData |  |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | @return |

### OH_AudioStreamBuilder_GenerateRenderer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)
```

**描述**

Create the audio renderer client.The AudioRenderer instance is used to play streaming audio data.When using AudioRenderer apis, there are many instructions for applicationto achieve better performance and lower power consumption:In music or audiobook background playback situation, you can have low powerconsumption by following this best practices document **Low-Power Rules in Music Playback Scenarios**.And for navigation situation, you can follow **Low-Power Rules in Navigation and Positioning Scenarios**.Application developer should also be careful when app goes to background, please check if your audio playbackis still needed, see **Audio Resources** in best practices document.And avoiding to send silence audio data continuously to waste system resources, otherwise system will takecontrol measures when this behavior is detected, see **Audio Playback** in best practices document.If you want to use AudioRenderer api to implement a music playback application, there are also many interactivescenes to consider, see **Developing an Audio Application** in best practices document.

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | Reference provided by OH_AudioStreamBuilder_Create() |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)** audioRenderer | Pointer to a variable to receive the stream client. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.StreamType invalid;<br>                                                 3.Create OHAudioRenderer failed.</li><br>         </ul> |

### OH_AudioStreamBuilder_GenerateCapturer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)
```

**描述**

创建输入音频流实例。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)** audioCapturer | 指向输入音频流实例的指针，将被用来接收函数创建的结果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.StreamType invalid;<br>                                                 3.Create OHAudioCapturer failed.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)
```

**描述**

用于播放时设置每次回调的帧长，帧长至少为音频硬件一次处理的数据大小，并且小于内部缓冲容量的一半。<br>低时延播放：frameSize可设置为5ms、10ms、15ms、20ms音频数据对应的帧长。<br>普通通路播放：frameSize可设置为20ms-100ms音频数据对应的帧长。例如，当采样率48000Hz时，20ms音频数据对应的帧长计算方式为：frameSize = 48000 * 0.02，即960个采样点数。当frameSize为960时，对应的数据回调的长度为960 * 声道数 * 采样位宽（字节数）。比如双声道16bit时，length为960 * 2 * 2 = 3840。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t frameSize |  要设置音频数据的帧长。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) The param of builder is nullptr.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)
```

**描述**

设置同时写入音频数据和元数据的回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_WriteDataWithMetadataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_writedatawithmetadatacallback) callback | 将被用来同时写入音频数据和元数据的回调函数。 |
| void* userData | 指向通过回调函数传递的应用数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.StreamType invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetRendererInterruptMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)
```

**描述**

设置流客户端的中断模式。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioInterrupt_Mode](capi-native-audiostream-base-h.md#oh_audiointerrupt_mode) mode | 音频中断模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>         <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) If the execution is successful.</li><br>         <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result):<br>                                                 1.The param of builder is nullptr;<br>                                                 2.The param of mode invalid;<br>                                                 3.StreamType invalid.</li><br>         </ul> |

### OH_AudioStreamBuilder_SetRendererWriteDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)
```

**描述**

设置写入音频数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnWriteDataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback) callback | 将被用来写入音频数据的回调函数。 |
| void* userData | 指向通过回调函数传递的应用数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：<br>     <br>1. 参数builder为nullptr；<br>     <br>2. StreamType无效。 |

### OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)
```

**描述**

设置写入音频数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)类似。<br>如果同时设置该回调和OH_AudioStreamBuilder_SetRendererWriteDataCallback，只有最后一次设置的回调生效。<br>与OH_AudioStreamBuilder_SetRendererWriteDataCallback不同，OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced设置的回调函数，允许应用传入可变长度的音频数据，并通知系统写入的数据长度。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioRenderer_OnWriteDataCallbackAdvanced callback | 将被用来写入音频数据的回调函数。 |
| void* userData | 指向通过回调函数传递的应用数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数非法，比如builder为空指针，等等。 |

### OH_AudioStreamBuilder_SetVolumeMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)
```

**描述**

设置音频流音量模式。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_VolumeMode](capi-native-audiostream-base-h.md#oh_audiostream_volumemode) volumeMode | 要设置的音频流音量模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：<br>     <br>1. 参数builder为nullptr；<br>     <br>2. 参数volumeMode无效。 |

### OH_AudioStreamBuilder_SetRendererInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)
```

**描述**

设置输出音频流中断事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioRenderer_OnInterruptCallback callback | 用于接收中断事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetRendererErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)
```

**描述**

设置输出音频流错误事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioRenderer_OnErrorCallback callback | 用于接收错误事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerReadDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)
```

**描述**

设置输入音频流读取数据的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_OnReadDataCallback callback | 用于接收读取数据事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)
```

**描述**

设置输入音频流设备变更的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_OnDeviceChangeCallback callback | 用于接收设备变更事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)
```

**描述**

设置输入音频流中断事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_OnInterruptCallback callback | 用于接收中断事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)
```

**描述**

设置输入音频流错误事件的回调函数。<br>此函数与[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)类似。如果同时使用[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)或者本函数，那么只有最后一次设置的回调才生效，其它回调不会生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_OnErrorCallback callback | 用于接收错误事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)
```

**描述**

设置输入音频流是否启用静音打断模式。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| bool muteWhenInterrupted | 设置当前录制音频流是否启用静音打断模式。true表示启用；false表示不启用，保持为默认打断模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)
```

**描述**

设置音频播放过程中低时延状态改变事件的回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioRenderer_OnFastStatusChange callback | 用于接收播放低时延状态改变事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)
```

**描述**

设置音频录制过程中低时延状态改变事件的回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_OnFastStatusChange callback | 用于接收录制低时延状态改变事件的回调函数。 |
| void* userData | 指向应用程序数据结构的指针，该结构将传递给回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效，比如，builder为空指针。 |

### OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)
```

**描述**

设置音频录制流是否采集带音频混响效果的音频数据。当音频环回设置为硬件模式并启用混响效果时，低时延模式的采集器可以获取到具备混响效果的录音数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| bool enabled | 设置应用程序是否采集带混响效果的音频数据。true表示采集，false表示不采集。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效。如builder为空指针。 |

### OH_AudioStreamBuilder_SetPlaybackCaptureMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)
```

**描述**

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| uint32_t mode | 要设置的内录模式，可为[OH_AudioStream_PlaybackCaptureMode](capi-native-audiostream-base-h.md#oh_audiostream_playbackcapturemode)中多个值的组合。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | AUDIOSTREAM_SUCCESS：函数执行成功。<br>     <br>AUDIOSTREAM_ERROR_INVALID_PARAM：参数无效。例如，builder为空指针或mode值无效。 |

### OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)
```

**描述**

设置蜂窝通话下行录音风险提示语播放结束的回调函数。仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype).AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。此回调必须成功设置，否则采集器无法创建。音频采集器创建后，风险提示语将自动添加到发送给通话对方的语音数据中。应用应等待回调结果后再启动采集器，否则[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)将返回错误。请确保音频采集器在蜂窝通话开始后创建，否则[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)将返回错误。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_SensitiveRecordPermitCallback callback | 用于接收风险提示语播放结束的回调函数，不允许为空指针。 |
| void* userData | 用户数据指针，将在回调中回传给应用。若无需传递数据，可传入空指针。若数据不为空指针，调用方应在收到回调时确认数据是否仍然有效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>     <br><li>AUDIOSTREAM_SUCCESS：函数执行成功。</li><br>     <br><li>AUDIOSTREAM_ERROR_INVALID_PARAM：参数builder或callback为空指针。</li><br>     <br></ul> |

### OH_AudioStreamBuilder_SetCellularRecordSecurityParams()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)
```

**描述**

设置蜂窝通话下行录音的电话号码和安全令牌。仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype).AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。电话号码和安全令牌将用于校验蜂窝通话下行采集器是否匹配对应的蜂窝通话，必须成功设置，否则采集器无法创建。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilderstruct.md)* builder | 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| const char* cellularRecordPhoneNum | 目标蜂窝通话的电话号码，用于makeCallWithToken()中，不允许为空指针。 |
| const char* cellularRecordToken | 目标蜂窝通话的安全令牌，可通过通话管理的makeCallWithToken()函数获取，不允许为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul><br>     <br><li>AUDIOSTREAM_SUCCESS：函数执行成功。</li><br>     <br><li>AUDIOSTREAM_ERROR_INVALID_PARAM：参数builder、cellularRecordPhoneNum或cellularRecordToken为空指针。</li><br>     <br></ul> |


