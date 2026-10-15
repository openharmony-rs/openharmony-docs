# native_audiostreambuilder.h

## 概述

本文件提供音频播放和录制流构造器接口。 <br>为便于扩展，音频系统采用建造者设计模式实现音频播放和录制流对象的构造。 <br>开发者必须设置音频流的核心参数，包括采样率、声道数或声道掩码、采样格式、编码类型和使用场景， 其他参数开发者可以按需设置。 <br>对于回调函数，播放和写入数据和录制和读取数据回调必须设置，因为这是应用与系统传递数据的唯一方式。 <br>在设置完所需的参数和回调函数后，调用[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer) 或 [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)即可完成播放流或录制流的构造。 在这一步骤，所有设置项才会真正被用于音频流配置，相关的参数支持范围和权限要求也会在此时进行校验。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)](#oh_audiostreambuilder_create) | 创建一个用于构造播放流或者录制流的音频流构造器。 <br>当构造器不再使用时，需要调用[OH_AudioStreamBuilder_Destroy](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy)销毁。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)](#oh_audiostreambuilder_destroy) | 销毁一个音频流构造器。 <br>当构造器不再使用时，需要调用该函数销毁。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)](#oh_audiostreambuilder_setsamplingrate) | 设置音频流的采样率属性，单位为Hz。 <br>当前支持的范围是8000Hz - 384000Hz。 <br>采样率为音频流核心参数，开发者必须正确设置。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)](#oh_audiostreambuilder_setchannelcount) | 设置音频流的声道数属性。 <br>不设置声道布局时，系统会将声道数映射为默认的声道布局，1对应单声道、2对应立体声、6对应5.1声道、8对应7.1声道等。 <br>声道信息为音频流核心参数，声道数和声道布局，开发者必须至少设置一个。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)](#oh_audiostreambuilder_setsampleformat) | 设置音频流的采样格式属性。 <br>当使用PCM类编码格式，采样格式为音频流核心参数，开发者必须正确设置。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)](#oh_audiostreambuilder_setencodingtype) | 设置音频流的编码类型属性。 <br>编码类型为音频流核心参数，开发者必须正确设置。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)](#oh_audiostreambuilder_setlatencymode) | 设置音频流的时延模式。 <br>默认模式为普通模式，本接口主要用于设置低时延模式，在游戏和K歌类应用开发场景使用。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)](#oh_audiostreambuilder_setchannellayout) | 设置音频流的声道布局。 <br>相比声道数，声道布局所表示的声道信息更具体，能描述每个声道所在的空间位置。 <br>声道信息为音频流核心参数，声道数和声道布局，开发者必须至少设置一个。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)](#oh_audiostreambuilder_setrendererinfo) | 设置音频播放流的使用场景。 <br>音频系统会基于使用场景确定音频流的处理策略，包括音量、音效、设备选择和中断策略等。 <br>使用场景为音频流核心参数，开发者必须正确设置。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)](#oh_audiostreambuilder_setcapturerinfo) | 设置音频录制流的使用场景。 <br>音频系统会基于使用场景确定音频流的处理策略，包括音效、设备选择和中断策略等。 <br>使用场景为音频流核心参数，开发者必须正确设置。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setrenderercallback) | 设置音频播放流的回调。 <br>可同时设置4个回调，包括写入音频数据、音频播放流事件、音频播放中断事件和音频播放错误回调函数。 <br>注意，在设置音频回调函数时，请确保每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。(API20废弃) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setrendereroutputdevicechangecallback) | 设置音频播放流设备变化的回调。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)](#oh_audiostreambuilder_setrendererprivacy) | 设置当前音频播放流的隐私类型。 <br>默认的隐私类型为公开类型，当音频流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)不是通话类型时， 允许被其他应用录制或进行屏幕投射。 <br>如果音频播放流内容包含隐私或专利版权内容，开发者可通过此接口调整隐私类型， 避免被其他应用通过内录（录制系统内部音频）录制。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)](#oh_audiostreambuilder_setcapturercallback) | 设置音频录制流的回调。 <br>可同时设置4个回调，包括读取音频数据、音频录制流事件、音频录制中断事件和音频录制错误回调函数。 <br>注意，在设置音频回调函数时，请确保每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。(API20废弃) |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)](#oh_audiostreambuilder_generaterenderer) | 创建音频播放流实例。 <br>创建的播放流会使用所有已设置的音频参数和回调函数，相关的参数支持范围和权限要求也会在此时进行校验。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)](#oh_audiostreambuilder_generatecapturer) | 创建音频录制流实例。 <br>创建的录制流会使用所有已设置的音频参数和回调函数，相关的参数支持范围和权限要求也会在此时进行校验。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)](#oh_audiostreambuilder_setframesizeincallback) | 设置音频播放流每次数据回调的帧长。 <br>此设置影响的回调函数包括[OH_AudioRenderer_OnWriteData](capi-ohaudio-oh-audiorenderer-callbacks-struct.md#oh_audiorenderer_onwritedata)，[OH_AudioRenderer_OnWriteDataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback) 和 [OH_AudioRenderer_OnWriteDataCallbackAdvanced](capi-native-audiorenderer-h.md#oh_audiorenderer_onwritedatacallbackadvanced) <br>不同播放通路可设置的范围如下： <br>低时延播放：frameSize可设置为5ms、10ms、15ms、20ms音频数据对应的帧长。 <br>普通通路播放：frameSize可设置为20ms-100ms音频数据对应的帧长。 <br>帧长的含义是音频帧的采样点数量。当采样率为48000Hz时，20ms音频数据对应的帧长为48000 * 0.02，即960个采样点。 而对应的回调内数据长度计算方式为帧长 * 声道数 * 采样位宽（字节数）。当声道为双声道， 采样格式为16bit（2个字节）时，960帧长对应数据长度为960 * 2 * 2 = 3840字节。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)](#oh_audiostreambuilder_setwritedatawithmetadatacallback) | 设置同时写入音频数据和元数据的回调。 <br>本接口主要用于含元数据的音频格式播放场景，如Audio Vivid格式的音频播放。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>使用本接口时，不应再设置其他音频播放写入数据回调。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)](#oh_audiostreambuilder_setrendererinterruptmode) | 设置音频播放流的中断模式。 <br>中断模式会影响同一个应用进程内不同音频播放流之间的中断策略。默认为共享模式， 应用的不同音频流之间不会相互打断，而是由开发者自行管理。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallback) | 设置写入音频播放数据的回调函数。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置写入音频数据回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)](#oh_audiostreambuilder_setrendererwritedatacallbackadvanced) | 设置写入音频播放数据的回调函数。与OH_AudioStreamBuilder_SetRendererWriteDataCallback不同， OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced设置的回调函数，允许应用每次传入可变长度的音频数据， 并通知系统写入的数据长度。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)设置写入音频数据回调类似， 建议开发者优先使用本接口。 如果同时设置该回调和OH_AudioStreamBuilder_SetRendererWriteDataCallback，只有最后一次设置的回调生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)](#oh_audiostreambuilder_setvolumemode) | 设置音频播放流音量模式。 <br>默认的音量模式是AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL，音频播放流会使用系统全局的音量大小进行播放。 当设置为AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL， 音频播放流的音量，还会受到所设置的应用级音量大小的影响。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setrendererinterruptcallback) | 设置音频播放流中断事件的回调函数。 <br>当音频播放流被其他音频业务打断，回调函数会触发。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置音频中断事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setrenderererrorcallback) | 设置音频播放流错误事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置音频错误事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerreaddatacallback) | 设置读取音频录制数据的回调函数。 <br>在音频录制流运行过程中，此回调函数会被周期性的触发，让调用者读取已录到的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置读取音频数据回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerdevicechangecallback) | 设置音频录制流设备变化的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置音频流状态变化事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)](#oh_audiostreambuilder_setcapturerinterruptcallback) | 设置音频录制流中断事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置录音流中断事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)](#oh_audiostreambuilder_setcapturererrorcallback) | 设置音频录制流错误事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置录音流错误事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)](#oh_audiostreambuilder_setcapturerwillmutewheninterrupted) | 设置音频录制流是否启用静音替代打断模式。 <br>根据音频系统的录音并发策略，正在运行的录音流可能会被其他高优先级的音频业务打断，比如通话业务。 一些应用开发者想让录音流在此场景下也能保持在运行状态， 用此接口开启静音替代打断模式后，系统会在原本需要打断录音流的场景下， 只将录音数据变成静音，而不直接打断录音流。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setrendererfaststatuschangecallback) | 设置音频播放过程中低时延状态变化事件的回调函数。 <br>当应用使用低时延音频播放功能，在多音频业务并发的场景下， 由于硬件能力限制，系统并不能确保音频流一直处于低时延运行状态下。 当存在高优先级业务时，系统可能会将音频流转换为普通运行状态。当高优先级业务结束， 系统也会在保障流畅性的前提下，将音频流恢复到低时延运行模式。每次状态切换，都会触发此接口设置的回调函数。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)](#oh_audiostreambuilder_setcapturerfaststatuschangecallback) | 设置音频录制过程中低时延状态变化事件的回调函数。 <br>当应用使用低时延音频录制功能，在多音频业务并发的场景下， 由于硬件能力限制，系统并不能确保音频流一直处于低时延运行状态下。 当存在高优先级业务时，系统可能会将音频流转换为普通运行状态。当高优先级业务结束， 系统也会在保障流畅性的前提下，将音频流恢复到低时延运行模式。每次状态切换，都会触发此接口设置的回调函数。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)](#oh_audiostreambuilder_setcapturerloopbackeffectenabled) | 设置音频录制流是否采集带音频混响效果的音频数据。 <br>当开发者使用AudioLoopback接口实现音频硬件返听功能， 并通过setReverbPreset设置混响效果后，同时使用低时延模式的录制流实现录音功能， 通过此接口设置，可以获取到具备混响效果的录音数据。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)](#oh_audiostreambuilder_setplaybackcapturemode) |  |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)](#oh_audiostreambuilder_setsensitiverecordpermitcallback) | 设置蜂窝通话下行录音风险提示语播放结束事件的回调函数。 <br>仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。 <br>此回调必须成功设置，否则录制流无法创建。 <br>音频录制流创建后，风险提示语将自动添加到发送给通话对方的语音数据中。 应用应等待回调结果后再启动录制流，否则[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)将返回错误。 <br>请确保音频录制流在蜂窝通话开始后创建，否则[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)将返回错误。 |
| [OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)](#oh_audiostreambuilder_setcellularrecordsecurityparams) | 设置蜂窝通话下行录音的电话号码和安全令牌。 <br>仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。 <br>电话号码和安全令牌将用于校验蜂窝通话下行录制流是否匹配对应的蜂窝通话，必须成功设置，否则录制流无法创建。 |

## 函数说明

### OH_AudioStreamBuilder_Create()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Create(OH_AudioStreamBuilder** builder, OH_AudioStream_Type type)
```

**描述：**

创建一个用于构造播放流或者录制流的音频流构造器。 <br>当构造器不再使用时，需要调用[OH_AudioStreamBuilder_Destroy](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_destroy)销毁。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)** builder | [out] 用于接收创建的构造器实例。 |
| [OH_AudioStream_Type](capi-native-audiostream-base-h.md#oh_audiostream_type) type | [in] 需要构造的音频流类型。 设置AUDIOSTREAM_TYPE_RENDERER构造播放流，设置AUDIOSTREAM_TYPE_CAPTURER构造录制流。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> </ul> |

### OH_AudioStreamBuilder_Destroy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_Destroy(OH_AudioStreamBuilder* builder)
```

**描述：**

销毁一个音频流构造器。 <br>当构造器不再使用时，需要调用该函数销毁。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioStreamBuilder_SetSamplingRate()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSamplingRate(OH_AudioStreamBuilder* builder, int32_t rate)
```

**描述：**

设置音频流的采样率属性，单位为Hz。 <br>当前支持的范围是8000Hz - 384000Hz。 <br>采样率为音频流核心参数，开发者必须正确设置。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t rate | [in] 音频流的采样率，单位为Hz。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数rate无效。</li> </ul> |

### OH_AudioStreamBuilder_SetChannelCount()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelCount(OH_AudioStreamBuilder* builder, int32_t channelCount)
```

**描述：**

设置音频流的声道数属性。 <br>不设置声道布局时，系统会将声道数映射为默认的声道布局，1对应单声道、2对应立体声、6对应5.1声道、8对应7.1声道等。 <br>声道信息为音频流核心参数，声道数和声道布局，开发者必须至少设置一个。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t channelCount | [in] 音频流的声道数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数channelCount无效。</li> </ul> |

### OH_AudioStreamBuilder_SetSampleFormat()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSampleFormat(OH_AudioStreamBuilder* builder, OH_AudioStream_SampleFormat format)
```

**描述：**

设置音频流的采样格式属性。 <br>当使用PCM类编码格式，采样格式为音频流核心参数，开发者必须正确设置。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) format | [in] 音频流的采样格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetEncodingType()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetEncodingType(OH_AudioStreamBuilder* builder, OH_AudioStream_EncodingType encodingType)
```

**描述：**

设置音频流的编码类型属性。 <br>编码类型为音频流核心参数，开发者必须正确设置。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | [in] 音频流编码类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetLatencyMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetLatencyMode(OH_AudioStreamBuilder* builder, OH_AudioStream_LatencyMode latencyMode)
```

**描述：**

设置音频流的时延模式。 <br>默认模式为普通模式，本接口主要用于设置低时延模式，在游戏和K歌类应用开发场景使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode) latencyMode | [in] 音频流的时延模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetChannelLayout()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetChannelLayout(OH_AudioStreamBuilder* builder, OH_AudioChannelLayout channelLayout)
```

**描述：**

设置音频流的声道布局。 <br>相比声道数，声道布局所表示的声道信息更具体，能描述每个声道所在的空间位置。 <br>声道信息为音频流核心参数，声道数和声道布局，开发者必须至少设置一个。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioChannelLayout channelLayout | [in] 音频流的声道布局。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_Usage usage)
```

**描述：**

设置音频播放流的使用场景。 <br>音频系统会基于使用场景确定音频流的处理策略，包括音量、音效、设备选择和中断策略等。 <br>使用场景为音频流核心参数，开发者必须正确设置。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流的使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数usage无效。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerInfo()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInfo(OH_AudioStreamBuilder* builder, OH_AudioStream_SourceType sourceType)
```

**描述：**

设置音频录制流的使用场景。 <br>音频系统会基于使用场景确定音频流的处理策略，包括音效、设备选择和中断策略等。 <br>使用场景为音频流核心参数，开发者必须正确设置。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | [in] 音频录制流的使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数sourceType无效。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_Callbacks callbacks, void* userData)
```

**描述：**

设置音频播放流的回调。 <br>可同时设置4个回调，包括写入音频数据、音频播放流事件、音频播放中断事件和音频播放错误回调函数。 <br>注意，在设置音频回调函数时，请确保每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Set the callback functions separately using OH_AudioStreamBuilder_SetRendererWriteDataCallback, OH_AudioStreamBuilder_SetRendererInterruptCallback, OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback and OH_AudioStreamBuilder_SetRendererErrorCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioRenderer_Callbacks callbacks | [in] 将被用来处理音频播放流相关事件的回调函数集合。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererOutputDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OutputDeviceChangeCallback callback, void* userData)
```

**描述：**

设置音频播放流设备变化的回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OutputDeviceChangeCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_outputdevicechangecallback) callback | [in] 当播放流设备变化时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererPrivacy(OH_AudioStreamBuilder* builder, OH_AudioStream_PrivacyType privacy)
```

**描述：**

设置当前音频播放流的隐私类型。 <br>默认的隐私类型为公开类型，当音频流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)不是通话类型时， 允许被其他应用录制或进行屏幕投射。 <br>如果音频播放流内容包含隐私或专利版权内容，开发者可通过此接口调整隐私类型， 避免被其他应用通过内录（录制系统内部音频）录制。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_PrivacyType](capi-native-audiostream-base-h.md#oh_audiostream_privacytype) privacy | [in] 音频播放流的隐私类型，会影响播放流是否会被其他应用录制或进行屏幕投射。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_Callbacks callbacks, void* userData)
```

**描述：**

设置音频录制流的回调。 <br>可同时设置4个回调，包括读取音频数据、音频录制流事件、音频录制中断事件和音频录制错误回调函数。 <br>注意，在设置音频回调函数时，请确保每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Set the callback functions separately using OH_AudioStreamBuilder_SetCapturerReadDataCallback, OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback, OH_AudioStreamBuilder_SetCapturerInterruptCallback and OH_AudioStreamBuilder_SetCapturerErrorCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| OH_AudioCapturer_Callbacks callbacks | [in] 将被用来处理音频录制流相关事件的回调函数集合。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是录制流类型。</li> </ul> |

### OH_AudioStreamBuilder_GenerateRenderer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateRenderer(OH_AudioStreamBuilder* builder, OH_AudioRenderer** audioRenderer)
```

**描述：**

创建音频播放流实例。 <br>创建的播放流会使用所有已设置的音频参数和回调函数，相关的参数支持范围和权限要求也会在此时进行校验。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)** audioRenderer | [out] 用来接收创建的音频播放流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型；3. 创建OHAudioRenderer失败，可能是音频服务异常或系统资源不足。</li> </ul> |

### OH_AudioStreamBuilder_GenerateCapturer()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_GenerateCapturer(OH_AudioStreamBuilder* builder, OH_AudioCapturer** audioCapturer)
```

**描述：**

创建音频录制流实例。 <br>创建的录制流会使用所有已设置的音频参数和回调函数，相关的参数支持范围和权限要求也会在此时进行校验。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)** audioCapturer | [out] 指向音频录制流实例的指针，将被用来接收函数创建的结果。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是录制流类型；3. 创建OHAudioCapturer失败，可能是音频服务异常、系统资源不足或权限不足。</li> </ul> |

### OH_AudioStreamBuilder_SetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetFrameSizeInCallback(OH_AudioStreamBuilder* builder, int32_t frameSize)
```

**描述：**

设置音频播放流每次数据回调的帧长。 <br>此设置影响的回调函数包括[OH_AudioRenderer_OnWriteData](capi-ohaudio-oh-audiorenderer-callbacks-struct.md#oh_audiorenderer_onwritedata)，[OH_AudioRenderer_OnWriteDataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback) 和 [OH_AudioRenderer_OnWriteDataCallbackAdvanced](capi-native-audiorenderer-h.md#oh_audiorenderer_onwritedatacallbackadvanced) <br>不同播放通路可设置的范围如下： <br>低时延播放：frameSize可设置为5ms、10ms、15ms、20ms音频数据对应的帧长。 <br>普通通路播放：frameSize可设置为20ms-100ms音频数据对应的帧长。 <br>帧长的含义是音频帧的采样点数量。当采样率为48000Hz时，20ms音频数据对应的帧长为48000 * 0.02，即960个采样点。 而对应的回调内数据长度计算方式为帧长 * 声道数 * 采样位宽（字节数）。当声道为双声道， 采样格式为16bit（2个字节）时，960帧长对应数据长度为960 * 2 * 2 = 3840字节。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| int32_t frameSize |  [in] 音频数据回调的帧长，单位为采样点数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetWriteDataWithMetadataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_WriteDataWithMetadataCallback callback, void* userData)
```

**描述：**

设置同时写入音频数据和元数据的回调。 <br>本接口主要用于含元数据的音频格式播放场景，如Audio Vivid格式的音频播放。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>使用本接口时，不应再设置其他音频播放写入数据回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_WriteDataWithMetadataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_writedatawithmetadatacallback) callback | [in] 当音频系统请求音频播放数据和元数据时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererInterruptMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptMode(OH_AudioStreamBuilder* builder, OH_AudioInterrupt_Mode mode)
```

**描述：**

设置音频播放流的中断模式。 <br>中断模式会影响同一个应用进程内不同音频播放流之间的中断策略。默认为共享模式， 应用的不同音频流之间不会相互打断，而是由开发者自行管理。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioInterrupt_Mode](capi-native-audiostream-base-h.md#oh_audiointerrupt_mode) mode | [in] 音频中断模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数mode无效；3. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererWriteDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallback callback, void* userData)
```

**描述：**

设置写入音频播放数据的回调函数。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置写入音频数据回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnWriteDataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback) callback | [in] 当音频系统请求音频播放数据时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. builder不是播放流类型。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnWriteDataCallbackAdvanced callback, void* userData)
```

**描述：**

设置写入音频播放数据的回调函数。与OH_AudioStreamBuilder_SetRendererWriteDataCallback不同， OH_AudioStreamBuilder_SetRendererWriteDataCallbackAdvanced设置的回调函数，允许应用每次传入可变长度的音频数据， 并通知系统写入的数据长度。 <br>在音频播放流运行过程中，此回调函数会被周期性的触发，让调用者写入要播放的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererWriteDataCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrendererwritedatacallback)设置写入音频数据回调类似， 建议开发者优先使用本接口。 如果同时设置该回调和OH_AudioStreamBuilder_SetRendererWriteDataCallback，只有最后一次设置的回调生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnWriteDataCallbackAdvanced](capi-native-audiorenderer-h.md#oh_audiorenderer_onwritedatacallbackadvanced) callback | [in] 当音频系统请求音频播放数据时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数非法，比如builder为空指针，等等。</li> </ul> |

### OH_AudioStreamBuilder_SetVolumeMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetVolumeMode(OH_AudioStreamBuilder* builder, OH_AudioStream_VolumeMode volumeMode)
```

**描述：**

设置音频播放流音量模式。 <br>默认的音量模式是AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL，音频播放流会使用系统全局的音量大小进行播放。 当设置为AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL， 音频播放流的音量，还会受到所设置的应用级音量大小的影响。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioStream_VolumeMode](capi-native-audiostream-base-h.md#oh_audiostream_volumemode) volumeMode | [in] 音频播放流的音量模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数builder为空指针；2. 参数volumeMode无效。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnInterruptCallback callback, void* userData)
```

**描述：**

设置音频播放流中断事件的回调函数。 <br>当音频播放流被其他音频业务打断，回调函数会触发。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置音频中断事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnInterruptCallback](capi-native-audiorenderer-h.md#oh_audiorenderer_oninterruptcallback) callback | [in] 当音频播放流被其他音频业务打断，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnErrorCallback callback, void* userData)
```

**描述：**

设置音频播放流错误事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)设置音频错误事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnErrorCallback](capi-native-audiorenderer-h.md#oh_audiorenderer_onerrorcallback) callback | [in] 当音频播放出现错误，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerReadDataCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerReadDataCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnReadDataCallback callback, void* userData)
```

**描述：**

设置读取音频录制数据的回调函数。 <br>在音频录制流运行过程中，此回调函数会被周期性的触发，让调用者读取已录到的音频数据。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置读取音频数据回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_OnReadDataCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback) callback | [in] 当音频系统录制到数据时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerDeviceChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnDeviceChangeCallback callback, void* userData)
```

**描述：**

设置音频录制流设备变化的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置音频流状态变化事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_OnDeviceChangeCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_ondevicechangecallback) callback | [in] 当音频录制流设备变化时，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerInterruptCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerInterruptCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnInterruptCallback callback, void* userData)
```

**描述：**

设置音频录制流中断事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置录音流中断事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_OnInterruptCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_oninterruptcallback) callback | [in] 当音频录制流被其他音频业务打断，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerErrorCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerErrorCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnErrorCallback callback, void* userData)
```

**描述：**

设置音频录制流错误事件的回调函数。 <br>此接口功能与通过[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)设置录音流错误事件回调类似， 建议开发者优先使用本接口。如果同时使用 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)和本接口，只有最后一次设置的回调才生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_OnErrorCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onerrorcallback) callback | [in] 当音频录制出现错误，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerWillMuteWhenInterrupted(OH_AudioStreamBuilder* builder, bool muteWhenInterrupted)
```

**描述：**

设置音频录制流是否启用静音替代打断模式。 <br>根据音频系统的录音并发策略，正在运行的录音流可能会被其他高优先级的音频业务打断，比如通话业务。 一些应用开发者想让录音流在此场景下也能保持在运行状态， 用此接口开启静音替代打断模式后，系统会在原本需要打断录音流的场景下， 只将录音数据变成静音，而不直接打断录音流。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| bool muteWhenInterrupted | [in] 设置当前录制音频流是否启用静音替代打断模式。 true表示启用；false表示不启用，默认为打断模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetRendererFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioRenderer_OnFastStatusChange callback, void* userData)
```

**描述：**

设置音频播放过程中低时延状态变化事件的回调函数。 <br>当应用使用低时延音频播放功能，在多音频业务并发的场景下， 由于硬件能力限制，系统并不能确保音频流一直处于低时延运行状态下。 当存在高优先级业务时，系统可能会将音频流转换为普通运行状态。当高优先级业务结束， 系统也会在保障流畅性的前提下，将音频流恢复到低时延运行模式。每次状态切换，都会触发此接口设置的回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioRenderer_OnFastStatusChange](capi-native-audiorenderer-h.md#oh_audiorenderer_onfaststatuschange) callback | [in] 当音频播放流低时延状态变化，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerFastStatusChangeCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_OnFastStatusChange callback, void* userData)
```

**描述：**

设置音频录制过程中低时延状态变化事件的回调函数。 <br>当应用使用低时延音频录制功能，在多音频业务并发的场景下， 由于硬件能力限制，系统并不能确保音频流一直处于低时延运行状态下。 当存在高优先级业务时，系统可能会将音频流转换为普通运行状态。当高优先级业务结束， 系统也会在保障流畅性的前提下，将音频流恢复到低时延运行模式。每次状态切换，都会触发此接口设置的回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_OnFastStatusChange](capi-native-audiocapturer-h.md#oh_audiocapturer_onfaststatuschange) callback | [in] 当音频录制流低时延状态变化，此回调函数会触发。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效，比如，builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCapturerLoopbackEffectEnabled(OH_AudioStreamBuilder* builder, bool enabled)
```

**描述：**

设置音频录制流是否采集带音频混响效果的音频数据。 <br>当开发者使用AudioLoopback接口实现音频硬件返听功能， 并通过setReverbPreset设置混响效果后，同时使用低时延模式的录制流实现录音功能， 通过此接口设置，可以获取到具备混响效果的录音数据。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| bool enabled | [in] 设置录制流是否采集有混响效果的音频数据。true表示有混响效果，false表示没有。默认为没有混响效果。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效。如builder为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetPlaybackCaptureMode()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetPlaybackCaptureMode(OH_AudioStreamBuilder* builder, uint32_t mode)
```

**描述：**

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| uint32_t mode | [in] 要设置的内录模式，可以是单个[OH_AudioStream_PlaybackCaptureMode](capi-native-audiostream-base-h.md#oh_audiostream_playbackcapturemode)，或多个枚举或运算的结果。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数无效。例如，builder为空指针或mode值无效。</li> </ul> |

### OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback(OH_AudioStreamBuilder* builder, OH_AudioCapturer_SensitiveRecordPermitCallback callback, void* userData)
```

**描述：**

设置蜂窝通话下行录音风险提示语播放结束事件的回调函数。 <br>仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。 <br>此回调必须成功设置，否则录制流无法创建。 <br>音频录制流创建后，风险提示语将自动添加到发送给通话对方的语音数据中。 应用应等待回调结果后再启动录制流，否则[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)将返回错误。 <br>请确保音频录制流在蜂窝通话开始后创建，否则[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)将返回错误。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| [OH_AudioCapturer_SensitiveRecordPermitCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_sensitiverecordpermitcallback) callback | [in] 当风险提示语播放结束，此回调函数会触发。不允许为空指针。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>AUDIOSTREAM_SUCCESS：函数执行成功。</li> <li>AUDIOSTREAM_ERROR_INVALID_PARAM：参数builder或callback为空指针。</li> </ul> |

### OH_AudioStreamBuilder_SetCellularRecordSecurityParams()

```c
OH_AudioStream_Result OH_AudioStreamBuilder_SetCellularRecordSecurityParams(OH_AudioStreamBuilder* builder, const char* cellularRecordPhoneNum, const char* cellularRecordToken)
```

**描述：**

设置蜂窝通话下行录音的电话号码和安全令牌。 <br>仅在使用[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK录制时需要设置此函数。 <br>电话号码和安全令牌将用于校验蜂窝通话下行录制流是否匹配对应的蜂窝通话，必须成功设置，否则录制流无法创建。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md)* builder | [in] 指向[OH_AudioStreamBuilder_Create](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_create)创建的构造器实例。 |
| const char* cellularRecordPhoneNum | [in] 目标蜂窝通话的电话号码，用于makeCallWithToken()中，不允许为空指针。 |
| const char* cellularRecordToken | [in] 目标蜂窝通话的安全令牌，可通过通话管理的makeCallWithToken()函数获取，不允许为空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>AUDIOSTREAM_SUCCESS：函数执行成功。</li> <li>AUDIOSTREAM_ERROR_INVALID_PARAM：参数builder、cellularRecordPhoneNum或cellularRecordToken为空指针。</li> </ul> |


