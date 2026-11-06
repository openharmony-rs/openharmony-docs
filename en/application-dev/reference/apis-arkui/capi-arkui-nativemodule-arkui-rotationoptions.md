# ArkUI_RotationOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bdfa874a4b1a414190d4f3f309d53e78218cd5fb translatedAt=2026-08-21T01:42:53.274Z pushedAt=2026-08-21T02:11:09.438Z -->

```c
typedef struct {...} ArkUI_RotationOptions
```

## Overview

Defines the rotation options for component transition.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | X-component of the rotation vector, which jointly defines the rotation axis direction with the y axis and z axis. Value range: (-∞, +∞). |
| float y | Y-component of the rotation vector, which jointly defines the rotation axis direction with the x axis and z axis. Value range: (-∞, +∞). |
| float z | Z-component of the rotation vector, which jointly defines the rotation axis direction with the x axis and y axis. Value range: (-∞, +∞). |
| float angle | Rotation angle, in degrees (°). Value range: (-∞, +∞). A positive value indicates clockwise rotation along the rotation axis direction determined by (x, y, z), and a negative value indicates counterclockwise rotation along that direction. |
| float centerX | X-component of the 3D rotation center point, in percentage. **0** indicates the left edge of the component, **1** indicates the right edge of the component, and **0.5** indicates the horizontal center of the component. Value range: (-∞, +∞). |
| float centerY | Y-component of the 3D rotation center point, in percentage. **0** indicates the top edge of the component, **1** indicates the bottom edge of the component, and **0.5** indicates the vertical center of the component. Value range: (-∞, +∞). |
| float centerZ | Z-component of the 3D rotation center point, in percentage. **0** indicates the plane where the component is located, a positive value indicates that the rotation center is offset toward the observer, and a negative value indicates that the rotation center is offset away from the observer. The presentation of the 3D rotation effect is affected by the **perspective** parameter. |
| float perspective | Viewing distance, that is, the distance from the viewpoint to the z=0 plane, which is the z-coordinate where the camera is placed, in px. The value indicates the viewing distance, that is, the distance from the camera to the z=0 plane. The sign of the value determines the direction in which the camera observes. When **perspective** is set to **0**, the system automatically calculates a suitable z-axis position for the camera, which is a negative value. |