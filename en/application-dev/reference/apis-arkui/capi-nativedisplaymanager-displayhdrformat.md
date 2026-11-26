# NativeDisplayManager_DisplayHdrFormat
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-11-25T10:40:05.512Z pushedAt=2026-11-26T03:49:31.117Z nl=1 -->

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
| uint32_t hdrFormatLength | Number of the HDR formats supported by a display.|
| uint32_t* hdrFormats | Pointer to the HDR format array supported by a display. |


