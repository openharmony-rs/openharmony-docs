# ArkUI_RotationOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_RotationOptions
```

## Overview

Defines the rotation effect object for a component during transition.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | X-component of the rotation vector.|
| float y | Y-component of the rotation vector.|
| float z | Z-component of the rotation vector.|
| float angle | Rotation angle.|
| float centerX | X-coordinate of the center point, in vp.|
| float centerY | Y-coordinate of the center point, in vp.|
| float centerZ | Z-component of the 3D rotation center point, in px.|
| float perspective | Viewing distance, that is, the distance from the viewpoint to the z=0 plane, in px.|
