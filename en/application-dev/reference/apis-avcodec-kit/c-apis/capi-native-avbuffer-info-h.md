# native_avbuffer_info.h

## Overview

The file declares the attribute definition of the media struct AVBuffer.

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-avcodec-kit-core.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OH_AVCodecBufferAttr](capi-core-oh-avcodecbufferattr.md) | The struct describes the description information about the buffer of an OH_AVCodec instance. |

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

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| AVCODEC_BUFFER_FLAGS_NONE = 0 | Common frame.<br>**Since**: 9 |
| AVCODEC_BUFFER_FLAGS_EOS = 1 << 0 | The buffer is an end-of-stream frame.<br>**Since**: 9 |
| AVCODEC_BUFFER_FLAGS_SYNC_FRAME = 1 << 1 | The buffer contains key frames.<br>**Since**: 9 |
| AVCODEC_BUFFER_FLAGS_INCOMPLETE_FRAME = 1 << 2 | The data in the buffer is only part of the frame.<br>**Since**: 9 |
| AVCODEC_BUFFER_FLAGS_CODEC_DATA = 1 << 3 | The buffer contains codec-specific data.<br>**Since**: 9 |
| AVCODEC_BUFFER_FLAGS_DISCARD = 1 << 4 | Flag is used to discard packets which are required to maintain valid decoder state but are not required for output and should be dropped after decoding.<br>**Since**: 12 |
| AVCODEC_BUFFER_FLAGS_DISPOSABLE = 1 << 5 | Flag is used to indicate packets that contain frames that can be discarded by the decoder, I.e. Non-reference frames.<br>**Since**: 12 |


