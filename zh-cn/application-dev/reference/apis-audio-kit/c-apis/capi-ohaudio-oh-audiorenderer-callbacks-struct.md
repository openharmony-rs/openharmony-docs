# OH_AudioRenderer_Callbacks_Struct

```c
typedef struct OH_AudioRenderer_Callbacks_Struct {...} OH_AudioRenderer_Callbacks
```

## 概述

声明输出音频流的回调函数指针。<br>为了避免不可预期的行为，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化。<br>可参考{@link 推荐使用OHAudio开发音频播放功能(C/C++)}。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Use the callback type: OH_AudioRenderer_OnWriteDataCallback, OH_AudioRenderer_OutputDeviceChangeCallback,OH_AudioRenderer_OnInterruptEvent, OH_AudioRenderer_OnErrorCallback separately.

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)](#oh_audiorenderer_onwritedata) |  |
| [int32_t (\*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)](#oh_audiorenderer_onstreamevent) |  |
| [int32_t (\*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptevent) |  |
| [int32_t (\*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)](#oh_audiorenderer_onerror) |  |

## 成员函数说明

### OH_AudioRenderer_OnWriteData()

```c
int32_t (*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnWriteDataCallback.

### OH_AudioRenderer_OnStreamEvent()

```c
int32_t (*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OutputDeviceChangeCallback.

### OH_AudioRenderer_OnInterruptEvent()

```c
int32_t (*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnInterruptCallback.

### OH_AudioRenderer_OnError()

```c
int32_t (*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OnErrorCallback.


