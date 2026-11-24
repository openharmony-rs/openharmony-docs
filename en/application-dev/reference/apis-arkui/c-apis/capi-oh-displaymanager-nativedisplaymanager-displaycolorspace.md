# NativeDisplayManager_DisplayColorSpace

```c
typedef struct NativeDisplayManager_DisplayColorSpace {...} NativeDisplayManager_DisplayColorSpace
```

## Overview

The struct describes all the color spaces supported by a display.

<!--Device-typedef struct NativeDisplayManager_DisplayColorSpace {...} NativeDisplayManager_DisplayColorSpace--><!--Device-typedef struct NativeDisplayManager_DisplayColorSpace {...} NativeDisplayManager_DisplayColorSpace-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 14

**Related module**: [OH_DisplayManager](capi-arkui-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t colorSpaceLength | Number of color spaces supported by the display.<br><!--Device-uint32_t colorSpaceLength--><!--Device-uint32_t colorSpaceLength-End--> |
| uint32_t *colorSpaces | Data of the color spaces supported by the display.<br><!--Device-uint32_t *colorSpaces--><!--Device-uint32_t *colorSpaces-End--> |


