# native_avbuffer_info.h

## Overview

The file declares the attribute definition of the media struct AVBuffer.

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-core.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCodecBufferAttr](capi-core-oh-avcodecbufferattr.md) | OH_AVCodecBufferAttr | The struct describes the description information about the buffer of an OH_AVCodec instance. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCodecBufferFlags](#oh_avcodecbufferflags) | OH_AVCodecBufferFlags | Enumerates the flags for the buffer of an OH_AVCodec instance. |

## Enum type description

### OH_AVCodecBufferFlags

```c
enum OH_AVCodecBufferFlags
```

**Description**

Enumerates the flags for the buffer of an OH_AVCodec instance.

**Since**: 9

| Enum item | Description |
| -- | -- |
| AVCODEC_BUFFER_FLAGS_NONE = 0 |  |
| AVCODEC_BUFFER_FLAGS_EOS = 1 << 0 |  |
| AVCODEC_BUFFER_FLAGS_SYNC_FRAME = 1 << 1 |  |
| AVCODEC_BUFFER_FLAGS_INCOMPLETE_FRAME = 1 << 2 |  |
| AVCODEC_BUFFER_FLAGS_CODEC_DATA = 1 << 3 |  |
| AVCODEC_BUFFER_FLAGS_DISCARD = 1 << 4 |  |
| AVCODEC_BUFFER_FLAGS_DISPOSABLE = 1 << 5 |  |


