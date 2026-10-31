# NativeDisplayManager_CutoutInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @logn; @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9ff629abb1f77c36b24792690e916ea8f7bdd366 translatedAt=2026-08-27T08:35:14.351Z pushedAt=2026-08-27T11:44:12.142Z -->

```c
typedef struct {...} NativeDisplayManager_CutoutInfo
```

## Overview

Describes the unusable area of a display, including a punch hole, a notch, and the curved area of a waterfall display.

**Since**: 12

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t boundingRectsLength | Number of the unusable areas on a display, including a punch hole and a notch.|
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)* boundingRects | Bounding rectangles of the unusable areas on a display, including a punch hole and a notch. |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | Curved area on a waterfall display.|


