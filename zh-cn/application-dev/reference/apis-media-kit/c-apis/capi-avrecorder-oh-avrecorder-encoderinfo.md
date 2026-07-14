# OH_AVRecorder_EncoderInfo

```c
typedef struct OH_AVRecorder_EncoderInfo {...} OH_AVRecorder_EncoderInfo
```

## 概述

提供编码器信息。

**起始版本：** 18

**相关模块：** [AVRecorder](capi-avrecorder.md)

**所在头文件：** [avrecorder_base.h](capi-avrecorder-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) mimeType | encoder format MIME |
| char *type | encoder type, audio or video |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) bitRate | audio or video encoder bitRate range |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) frameRate | video encoder frame rate range |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) width | video encoder width range |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) height | video encoder height range |
| [OH_AVRecorder_Range](capi-avrecorder-oh-avrecorder-range.md) channels | audio encoder channel range |
| int32_t *sampleRate | audio encoder sample rate collection |
| int32_t sampleRateLen | length of sampleRate list |


