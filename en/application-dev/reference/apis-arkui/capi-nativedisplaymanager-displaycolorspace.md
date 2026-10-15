# NativeDisplayManager_DisplayColorSpace
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-10T10:23:28.457Z pushedAt=2026-10-15T01:37:30.764Z -->

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


