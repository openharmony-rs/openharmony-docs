# NativeDisplayManager_CutoutInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-10T10:22:16.595Z pushedAt=2026-10-15T01:37:21.693Z -->

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
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)* boundingRects | Pointer to the array of bounding rectangles of the unusable areas on a display, including a punch hole and a notch. |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | Curved area on a waterfall display.|


