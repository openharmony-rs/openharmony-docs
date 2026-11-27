# NativeDisplayManager_DisplayColorSpace
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-11-25T10:38:11.532Z pushedAt=2026-11-26T03:49:27.409Z nl=1 -->

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


