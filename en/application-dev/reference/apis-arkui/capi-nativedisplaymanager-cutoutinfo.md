# NativeDisplayManager_CutoutInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

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
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)* boundingRects | Pointer to the boundary rectangle array of the unusable areas on a display, including a punch hole and a notch.|
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | Curved area on a waterfall display.|
