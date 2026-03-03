# avmedia_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xushubo; @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

Defines the struct and enum of **AVMedia**.

**File to include**: <multimedia/player_framework/avmedia_base.h>

**Library**: libavmedia_base.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 23

**Related module**: [AVMediaBase](capi-avmediabase.md)

## Total

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVMedia_SeekMode](#oh_avmedia_seekmode) | OH_AVMedia_SeekMode | Enumerates the mappings between time points and frames.|

## Enum Description

### OH_AVMedia_SeekMode

```c
enum OH_AVMedia_SeekMode
```

**Description**

Enumerates the mappings between time points and frames.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| OH_AVMEDIA_SEEK_NEXT_SYNC = 0 | The key frame at or next to the specified time is selected.|
| OH_AVMEDIA_SEEK_PREVIOUS_SYNC = 1 | The key frame at or prior to the specified time is selected.|
| OH_AVMEDIA_SEEK_CLOSEST_SYNC = 2 | The key frame closest to the specified time is selected.|
| OH_AVMEDIA_SEEK_CLOSEST = 3 | The frame (not necessarily a key frame) closest to the specified time is selected.|
