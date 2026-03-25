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
| float x | Scaling factor along the x-axis. x > 1: The object is scaled up along the x-axis. 0<x<1: The object is scaled down along the x-axis. x = 0: The object is scaled down to 0 along the x-axis. x = 1: The object is scaled along the x-axis at a scale factor of 1. x < 0: The object is scaled in the reverse direction along the x-axis.|
| float y | Scaling factor along the y-axis. y > 1: The object is scaled up along the y-axis. 0<y<1: The object is scaled down along the y-axis. y = 0: The object is scaled down to 0 along the y-axis. y = 1: The object is scaled along the y-axis at a scale factor of 1. y < 0: The object is scaled in the reverse direction along the y-axis.|
| float z | Scale factor along the z-axis (not effective for the current 2D graphics).|
| float centerX | X-coordinate of the transformation center point. X-coordinate of the transformation center point (anchor point) of the component, in vp.|
| float centerY | Y-coordinate of the transformation center point. Y-coordinate of the transformation center point (anchor point) of the component, in vp.|
