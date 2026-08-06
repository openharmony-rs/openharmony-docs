# OH_AudioCaptureInfo

```c
typedef struct OH_AudioCaptureInfo {...} OH_AudioCaptureInfo
```

## 概述

音频采样信息。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t audioSampleRate | Audio capture sample rate info, in Hz |
| int32_t audioChannels | Audio capture channel info |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) audioSource | Audio capture source type |


