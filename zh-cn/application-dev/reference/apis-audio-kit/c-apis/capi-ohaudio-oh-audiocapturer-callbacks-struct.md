# OH_AudioCapturer_Callbacks_Struct

```c
typedef struct OH_AudioCapturer_Callbacks_Struct {...} OH_AudioCapturer_Callbacks
```

## 概述

声明用于音频采集器的回调函数指针。<br>为了避免不可预期的行为，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调方法或空指针初始化。可参考{@link 推荐使用OHAudio开发音频录制功能(C/C++)}。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** Use the callback type: OH_AudioCapturer_OnReadDataCallback, OH_AudioCapturer_OnDeviceChangeCallback,OH_AudioCapturer_OnInterruptCallback and OH_AudioCapturer_OnErrorCallback separately.

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)](#oh_audiocapturer_onreaddata) |  |
| [int32_t (\*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)](#oh_audiocapturer_onstreamevent) |  |
| [int32_t (\*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptevent) |  |
| [int32_t (\*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)](#oh_audiocapturer_onerror) |  |

## 成员函数说明

### OH_AudioCapturer_OnReadData()

```c
int32_t (*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnReadDataCallback

### OH_AudioCapturer_OnStreamEvent()

```c
int32_t (*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnDeviceChangeCallback

### OH_AudioCapturer_OnInterruptEvent()

```c
int32_t (*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnInterruptCallback

### OH_AudioCapturer_OnError()

```c
int32_t (*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)
```

**描述**

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioCapturer_OnErrorCallback


