# OH_AudioRenderer_Callbacks_Struct

```c
struct OH_AudioRenderer_Callbacks_Struct {...}
```

## 概述

声明用于同时设置音频渲染器的4个回调函数的结构体， 包括写入音频数据、音频播放流事件、音频播放中断事件和音频播放错误回调函数。 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口会用此结构体设置回调。 <br>注意，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。可参考开发指南-推荐使用OHAudio开发音频播放功能(C/C++)。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Use the callback type: OH_AudioRenderer_OnWriteDataCallback, OH_AudioRenderer_OutputDeviceChangeCallback, OH_AudioRenderer_OnInterruptCallback, OH_AudioRenderer_OnErrorCallback separately.

**相关模块：** [OHAudio](capi-others-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)](#oh_audiorenderer_onwritedata) | - | 指向用于写入音频数据的回调函数。当渲染器处于运行状态，此回调会周期性地触发，让开发者持续写入播放数据。 由于系统会将buffer内的全部数据用于播放，开发者需确保每次写入音频数据都填满buffer， 否则会因播放未初始化的数据导致不可预期的行为。 回调函数每次执行完成后，音频系统会将buffer数据暂时放入内部队列中等待处理， 因此请勿在回调函数返回后修改buffer指向的数据，否则会导致播放出现杂音。 注意，回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer的状态切换接口，避免引起死锁问题。 请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。 |
| [int32_t (\*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)](#oh_audiorenderer_onstreamevent) | - | 指向用于处理音频播放流事件的回调函数，但当前版本此回调不会被触发。 请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。 从API version 11开始，开发者如果需要监听音频设备变化， 可直接使用[OH_AudioRenderer_OutputDeviceChangeCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_outputdevicechangecallback)替代。 |
| [int32_t (\*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptevent) | - | 指向用于处理音频播放中断事件的回调函数。当播放流被系统中其他高优先级音频打断，会触发此回调。 请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。 |
| [int32_t (\*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)](#oh_audiorenderer_onerror) | - | 指向用于处理音频播放错误结果的回调函数。当播放流在使用过程中出现错误情况，会触发此回调。 请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。 |

## 成员函数说明

### OH_AudioRenderer_OnWriteData()

```c
int32_t (*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)
```

**描述：**

指向用于写入音频数据的回调函数。当渲染器处于运行状态，此回调会周期性地触发，让开发者持续写入播放数据。由于系统会将buffer内的全部数据用于播放，开发者需确保每次写入音频数据都填满buffer，否则会因播放未初始化的数据导致不可预期的行为。回调函数每次执行完成后，音频系统会将buffer数据暂时放入内部队列中等待处理，因此请勿在回调函数返回后修改buffer指向的数据，否则会导致播放出现杂音。注意，回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer的状态切换接口，避免引起死锁问题。请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnWriteDataCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口传入的userdata数据。 |
| void* buffer | 指向播放数据存储区域，开发者可从此buffer写入播放数据。 每次写入都需要填满buffer，否则会因播放未初始化的数据导致不可预期的行为。 |
| int32_t length | buffer的长度，单位为字节(Byte)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioRenderer_OnStreamEvent()

```c
int32_t (*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)
```

**描述：**

指向用于处理音频播放流事件的回调函数，但当前版本此回调不会被触发。请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。从API version 11开始，开发者如果需要监听音频设备变化，可直接使用[OH_AudioRenderer_OutputDeviceChangeCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_outputdevicechangecallback)替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OutputDeviceChangeCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口传入的userdata数据。 |
| [OH_AudioStream_Event](capi-native-audiostream-base-h.md#oh_audiostream_event) event | 音频播放流状态变化事件类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioRenderer_OnInterruptEvent()

```c
int32_t (*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**描述：**

指向用于处理音频播放中断事件的回调函数。当播放流被系统中其他高优先级音频打断，会触发此回调。请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnInterruptCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口传入的userdata数据。 |
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | 音频中断强制类型。 |
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | 音频中断提示类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |

### OH_AudioRenderer_OnError()

```c
int32_t (*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)
```

**描述：**

指向用于处理音频播放错误结果的回调函数。当播放流在使用过程中出现错误情况，会触发此回调。请确保该结构体成员变量被自定义的回调函数或空指针初始化，避免未初始化的回调函数被系统调用，引起不可预知的行为。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnErrorCallback.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| void* userData | 指向开发者在[OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口传入的userdata数据。 |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | 音频播放错误类型，常见错误包括： <br>AUDIOSTREAM_ERROR_INVALID_PARAM（入参错误，请检查输入参数类型和有效范围） <br>AUDIOSTREAM_ERROR_ILLEGAL_STATE（非法状态，请检查当前状态是否允许执行该操作） <br>AUDIOSTREAM_ERROR_SYSTEM（系统通用错误，请检查系统状态或重试） |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 回调函数返回值，当前版本系统并不处理，建议返回0。 |


