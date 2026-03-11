# ArkUI_ScaleOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_ScaleOptions
```

## Overview

Defines the scaling effect object for component transitions.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | Scale factor along the x-axis.|
| float y | Scale factor along the y-axis.|
| float z | Scale factor along the z-axis (not effective for the current 2D graphics).|
| float centerX | X-coordinate of the center point, in vp.|
| float centerY | Y-coordinate of the center point, in vp.|
