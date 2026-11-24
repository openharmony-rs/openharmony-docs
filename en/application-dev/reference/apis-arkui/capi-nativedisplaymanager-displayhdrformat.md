# NativeDisplayManager_DisplayHdrFormat
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-18T09:09:03.731Z pushedAt=2026-11-20T01:48:30.835Z nl=1 -->

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


