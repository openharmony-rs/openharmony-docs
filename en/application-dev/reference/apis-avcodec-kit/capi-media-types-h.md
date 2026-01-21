# media_types.h

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the common media types.

**File to include**: <multimedia/player_framework/media_types.h>

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 18

**Related module**: [Core](capi-core.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Core_HdrType](#oh_core_hdrtype) | OH_Core_HdrType | Enumerates the HDR types.|

## Enum Description

### OH_Core_HdrType

```c
enum OH_Core_HdrType
```

**Description**

Enumerates the HDR types.

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 18

| Value| Description|
| -- | -- |
| OH_CORE_HDR_TYPE_NONE = 0 | Non-HDR type.|
| OH_CORE_HDR_TYPE_VIVID = 1 | HDR Vivid type.|
