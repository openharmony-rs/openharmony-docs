# OH_AVCodecBufferAttr

```c
struct OH_AVCodecBufferAttr {...}
```

## Overview

The struct describes the description information about the buffer of an OH_AVCodec instance.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-others-core.md)

**Header file**: [native_avbuffer_info.h](capi-native-avbuffer-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t pts | Display timestamp of the buffer, in microseconds.<br>**Since**: 9 |
| int32_t size | Size of data contained in the buffer, in bytes.<br>**Since**: 9 |
| int32_t offset | Offset of valid data in the buffer.<br>**Since**: 9 |
| uint32_t flags | Flags of the buffer. For details, see [OH_AVCodecBufferFlags](capi-native-avbuffer-info-h.md#oh_avcodecbufferflags).<br>**Since**: 9 |


