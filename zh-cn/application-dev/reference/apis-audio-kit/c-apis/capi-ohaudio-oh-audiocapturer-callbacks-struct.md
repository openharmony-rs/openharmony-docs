# OH_AudioCapturer_Callbacks_Struct

```c
struct OH_AudioCapturer_Callbacks_Struct {...}
```

## 概述

声明用于同时设置音频采集器的4个回调函数的结构体， 包括读取音频数据、音频录制流事件、音频录制中断事件和音频录制错误回调函数。 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口会用此结构体设置回调。 <br>注意，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。可参考开发指南-推荐使用OHAudio开发音频录制功能(C/C++)。<br> 说明，以下回调接口的返回值均没有对应枚举定义，当前版本系统并不处理返回值， 但考虑到后续系统版本的可扩展性，建议使用0作为返回值。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Use the callback type: OH_AudioCapturer_OnReadDataCallback, OH_AudioCapturer_OnDeviceChangeCallback, OH_AudioCapturer_OnInterruptCallback and OH_AudioCapturer_OnErrorCallback separately.

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*OH_AudioCapturer_OnReadData)( OH_AudioCapturer* capturer, void* userData, void* buffer, int32_t length)](#oh_audiocapturer_onreaddata) | - |  |
| [int32_t (\*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)](#oh_audiocapturer_onstreamevent) | - |  |
| [int32_t (\*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptevent) | - |  |
| [int32_t (\*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)](#oh_audiocapturer_onerror) | - |  |

## 成员函数说明

### OH_AudioCapturer_OnReadData()

```c
int32_t (*OH_AudioCapturer_OnReadData)( OH_AudioCapturer* capturer, void* userData, void* buffer, int32_t length)
```

**描述：**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnReadDataCallback

**参数：**

| 参数项 | 描述 |
| -- | -- |
|  [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
|  void* userData | 指向开发者在[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口传入的userdata数据。 |
|  void* buffer | 指向录音数据存储区域，开发者可从此buffer读取录音数据。系统会将录音数据填满buffer。 |
|  int32_t length | buffer的长度，单位为字节(Byte)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioCapturer_OnStreamEvent()

```c
int32_t (*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)
```

**描述：**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnDeviceChangeCallback

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口传入的userdata数据。 |
| [OH_AudioStream_Event](capi-native-audiostream-base-h.md#oh_audiostream_event) event | 音频录制流状态变化事件类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioCapturer_OnInterruptEvent()

```c
int32_t (*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**描述：**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnInterruptCallback

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口传入的userdata数据。 |
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | 音频中断强制类型。 |
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | 音频中断提示类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioCapturer_OnError()

```c
int32_t (*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)
```

**描述：**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnErrorCallback

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口传入的userdata数据。 |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | 音频录制错误类型，常见错误包括： <br>AUDIOSTREAM_ERROR_INVALID_PARAM（入参错误，请检查输入参数类型和有效范围） <br>AUDIOSTREAM_ERROR_ILLEGAL_STATE（非法状态，请检查当前状态是否允许执行该操作） <br>AUDIOSTREAM_ERROR_SYSTEM（系统通用错误，请检查系统状态或重试） |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |


