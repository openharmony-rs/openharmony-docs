# NativeDisplayManager_DisplayColorSpace
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @logn; @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=61ff202ad259a75c2a093f9146121145c100be77 translatedAt=2026-08-27T08:35:17.874Z pushedAt=2026-08-27T11:46:43.487Z -->

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


