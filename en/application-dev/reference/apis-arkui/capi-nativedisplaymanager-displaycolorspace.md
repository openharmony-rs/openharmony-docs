# NativeDisplayManager_DisplayColorSpace
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} NativeDisplayManager_DisplayColorSpace
```

## Overview

Describes all the color spaces supported by a display.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t colorSpaceLength | Number of the color spaces supported by a display.|
| uint32_t* colorSpaces | Pointer to the color space array supported by a display.|
