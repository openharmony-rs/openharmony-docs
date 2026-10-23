# NativeDisplayManager_DisplayHdrFormat
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-10T10:27:23.379Z pushedAt=2026-10-15T01:38:27.174Z -->

```c
typedef struct {...} NativeDisplayManager_DisplayHdrFormat
```

## Overview

Describes all the HDR formats supported by a display.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t hdrFormatLength | Number of HDR formats supported by a display.|
| uint32_t* hdrFormats | Pointer to the HDR format array supported by a display. |


