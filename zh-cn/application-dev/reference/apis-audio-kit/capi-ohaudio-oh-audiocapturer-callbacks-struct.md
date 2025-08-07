# OH_AudioCapturer_Callbacks_Struct
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--SE: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--TSE: @Filger-->

## 概述

声明输入音频流的回调函数指针。

为了避免不可预期的行为，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调方法或空指针初始化。可参考[使用OHAudio开发音频录制功能](../../media/audio/using-ohaudio-for-recording.md)。

**起始版本：** 10

**废弃版本：** 20

**替代接口：**

请分别使用以下回调类型替代：

[OH_AudioCapturer_OnReadDataCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback)、 [OH_AudioCapturer_OnDeviceChangeCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_ondevicechangecallback)、 [OH_AudioCapturer_OnInterruptCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_oninterruptcallback) 以及 [OH_AudioCapturer_OnErrorCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onerrorcallback)。

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)](#oh_audiocapturer_onreaddata) | 该函数指针将指向用于读取音频数据的回调函数。 |
| [int32_t (\*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)](#oh_audiocapturer_onstreamevent) | 该函数指针将指向用于处理音频录制流事件的回调函数。 |
| [int32_t (\*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptevent) | 该函数指针将指向用于处理音频录制中断事件的回调函数。 |
| [int32_t (\*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)](#oh_audiocapturer_onerror)| 该函数指针将指向用于处理音频录制错误结果的回调函数。 |

## 成员函数说明

> **说明：**
> 以下回调接口的返回值没有枚举定义，当前版本实现并不按返回值区分处理，但为保证后续版本可扩展，默认使用0。

### OH_AudioCapturer_OnReadData()

```
int32_t (*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)
```

**描述**

该函数指针将指向用于读取音频数据的回调函数。

回调函数仅用来读取音频数据，请勿在回调函数中调用AudioCapturer相关接口。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [OH_AudioCapturer_OnReadDataCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onreaddatacallback)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向应用自定义的数据存储区域。     |
| void* buffer | 指向播放数据存储区域，用于应用填充播放数据。      |
| int32_t length | buffer的长度。     |

### OH_AudioCapturer_OnStreamEvent()

```
int32_t (*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)
```

**描述**

该函数指针将指向用于处理音频录制流事件的回调函数。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [OH_AudioCapturer_OnDeviceChangeCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_ondevicechangecallback)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向应用自定义的数据存储区域。 |
| [OH_AudioStream_Event](capi-native-audiostream-base-h.md#oh_audiostream_event) event | 音频事件。 |

### OH_AudioCapturer_OnInterruptEvent()

```
int32_t (*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**描述**

该函数指针将指向用于处理音频录制中断事件的回调函数。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [OH_AudioCapturer_OnInterruptCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_oninterruptcallback)

**参数：**

| 参数项  | 描述 |
|--| -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向应用自定义的数据存储区域。 |
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | 音频中断类型。 |
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | 音频中断提示类型。 |


### OH_AudioCapturer_OnError()

```
int32_t (*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)
```

**描述**

该函数指针将指向用于处理音频录制错误结果的回调函数。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** [OH_AudioCapturer_OnErrorCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onerrorcallback)

**参数：**

| 参数项  | 描述 |
|--| -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向应用自定义的数据存储区域。 |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | 音频录制错误结果，可能为AUDIOSTREAM_ERROR_INVALID_PARAM、AUDIOSTREAM_ERROR_ILLEGAL_STATE或者 AUDIOSTREAM_ERROR_SYSTEM。 |

