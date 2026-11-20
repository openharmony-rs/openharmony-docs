# NativeDisplayManager_DisplayColorSpace
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-18T09:05:05.019Z pushedAt=2026-11-20T01:48:26.314Z nl=1 -->

```c
typedef struct {...} NativeDisplayManager_DisplayColorSpace
```

## Overview

Describes the color spaces supported by a display.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t colorSpaceLength | Number of the color spaces supported by a display.|
| uint32_t* colorSpaces | Pointer to the color space array supported by a display. |


