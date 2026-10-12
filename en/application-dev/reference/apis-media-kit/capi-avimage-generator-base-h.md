# avimage_generator_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=769b8c31cfa3599a0a76dd1ed00c9c2f90dfde04 translatedAt=2026-09-15T15:43:09.195Z pushedAt=2026-09-22T06:07:04.652Z -->

## Overview

Defines the enums of the AVImageGenerator.

**File to include**: <multimedia/player_framework/avimage_generator_base.h>

**Library**: libavimage_generator.so

**System capability**: SystemCapability.Multimedia.Media.AVImageGenerator

**Since**: 18

**Related module**: [AVImageGenerator](capi-avimagegenerator.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVImageGenerator_QueryOptions](#oh_avimagegenerator_queryoptions) | OH_AVImageGenerator_QueryOptions | Enumerates the mappings between time points and frames during video frame query. |

## Enum Description

### OH_AVImageGenerator_QueryOptions

```c
enum OH_AVImageGenerator_QueryOptions
```

**Description**

Enumerates the mappings between time points and frames during video frame query.

**System capability**: SystemCapability.Multimedia.Media.AVImageGenerator

**Since**: 18

| Enum Item| Description|
| -- | -- |
| OH_AVIMAGE_GENERATOR_QUERY_NEXT_SYNC = 0 | The key frame at or next to the specified time is selected. |
| OH_AVIMAGE_GENERATOR_QUERY_PREVIOUS_SYNC = 1 | The key frame at or prior to the specified time is selected. |
| OH_AVIMAGE_GENERATOR_QUERY_CLOSEST_SYNC = 2 | The key frame closest to the specified time is selected. |
| OH_AVIMAGE_GENERATOR_QUERY_CLOSEST = 3 | The frame (not necessarily a key frame) closest to the specified time is selected. |
