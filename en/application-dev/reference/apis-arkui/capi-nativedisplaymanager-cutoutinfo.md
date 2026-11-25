# NativeDisplayManager_CutoutInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-18T09:03:51.727Z pushedAt=2026-11-20T01:48:20.916Z nl=1 -->

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


