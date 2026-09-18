# avmedia_base.h

## Overview

Defines the struct and enum of **AVMedia**.

**Library**: libavmedia_base.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 23

**Related module**: [AVMediaBase](capi-avmediabase.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMedia_SeekMode](#oh_avmedia_seekmode) | OH_AVMedia_SeekMode | Enumerates the mappings between time points and frames. |

## Enum type description

### OH_AVMedia_SeekMode

```c
enum OH_AVMedia_SeekMode
```

**Description**

Enumerates the mappings between time points and frames.

**Since**: 23

| Enum item | Description |
| -- | -- |
| OH_AVMEDIA_SEEK_NEXT_SYNC = 0 | The key frame at or next to the specified time is selected. |
| OH_AVMEDIA_SEEK_PREVIOUS_SYNC = 1 | The key frame at or prior to the specified time is selected. |
| OH_AVMEDIA_SEEK_CLOSEST_SYNC = 2 | The key frame closest to the specified time is selected. |
| OH_AVMEDIA_SEEK_CLOSEST = 3 | The frame (not necessarily a key frame) closest to the specified time is selected. |


