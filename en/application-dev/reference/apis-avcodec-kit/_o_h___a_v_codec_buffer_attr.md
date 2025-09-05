# OH_AVCodecBufferAttr


## Overview

The struct describes the description information about the buffer of an OH_AVCodec instance.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](_core.md)

**Header file**: [native_avbuffer_info.h](native__avbuffer__info_8h.md)


## Summary


### Member Variables

| Name| Description| 
| -------- | -------- |
| int64_t [pts](#pts) | Display timestamp of the buffer, in microseconds.| 
| int32_t [size](#size) | Size of data contained in the buffer, in bytes.| 
| int32_t [offset](#offset) | Offset of valid data in the buffer.| 
| uint32_t [flags](#flags) | Flags of the buffer. For details, see [OH_AVCodecBufferFlags](_core.md#oh_avcodecbufferflags).| 


## Member Variable Description


### flags

```
uint32_t OH_AVCodecBufferAttr::flags
```

**Description**

Flags of the buffer. For details, see [OH_AVCodecBufferFlags](_core.md#oh_avcodecbufferflags).


### offset

```
int32_t OH_AVCodecBufferAttr::offset
```

**Description**

Offset of valid data in the buffer.


### pts

```
int64_t OH_AVCodecBufferAttr::pts
```

**Description**

Display timestamp of the buffer, in microseconds.


### size

```
int32_t OH_AVCodecBufferAttr::size
```

**Description**

Size of data contained in the buffer, in bytes.
