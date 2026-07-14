# OH_AudioBuffer

```c
typedef struct OH_AudioBuffer {...} OH_AudioBuffer
```

## 概述

定义了音频数据的大小、类型、时间戳等配置信息。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t *buf | Audio buffer memory block |
| int32_t size | Audio buffer memory block size |
| int64_t timestamp | Audio buffer timestamp info, in nanosecond |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Audio capture source type |


