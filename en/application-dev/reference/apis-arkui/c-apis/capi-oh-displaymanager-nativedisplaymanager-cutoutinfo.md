# NativeDisplayManager_CutoutInfo

```c
typedef struct NativeDisplayManager_CutoutInfo {...} NativeDisplayManager_CutoutInfo
```

## Overview

The struct describes the unusable area of a display, including punch hole, notch, and curved area of a waterfall display.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 12

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t boundingRectsLength | boundingRects length |
| [NativeDisplayManager_Rect](capi-oh-displaymanager-nativedisplaymanager-rect.md) *boundingRects | boundingRects info pointer |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-oh-displaymanager-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | waterfallDisplayAreaRects info |


