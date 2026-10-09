# ArkUI_ScaleOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bdfa874a4b1a414190d4f3f309d53e78218cd5fb translatedAt=2026-08-21T01:42:46.553Z pushedAt=2026-08-21T02:10:34.964Z -->

```c
typedef struct {...} ArkUI_ScaleOptions
```

## Overview

Defines the scale options for component transition.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type_visual.h](capi-native-type-visual-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | Scale factor along the x-axis. The default value is **1.0**. x > 1: The component is scaled up along the x-axis. 0 < x < 1: The component is scaled down along the x-axis. x < 0: The component is scaled in the reversed direction along the x-axis, with the scale factor being \|x\|. The scaling is performed with **centerX** as the anchor point. Note: when x = 0, the component completely disappears along the x-axis. Pay attention to the impact of this special value when using it. |
| float y | Scale factor along the y-axis. The default value is **1.0**. y > 1: The component is scaled up along the y-axis. 0 < y < 1: The component is scaled down along the y-axis. y < 0: The component is scaled in the reversed direction along the y-axis, with the scale factor being \|y\|. Note: when y = 0, the component completely disappears along the y-axis. Pay attention to the impact of this special value when using it. |
| float z | Scale factor along the z-axis. The default value is **1.0**. In 2D display mode, this parameter does not take effect. |
| float centerX | X-coordinate of the component transformation center point (that is, the anchor point), in percentage. **0** indicates the left edge of the component, **1** indicates the right edge of the component, and **0.5** indicates the horizontal center of the component. The default value is **0.5**. The scaling effect along the x-axis is performed with this point as the anchor point. Different **centerX** values determine the x-direction positions of the scaling anchor point. When the value is **0**, the scaling is performed from the left edge of the component; when the value is **0.5**, the scaling is performed from the horizontal center; when the value is **1**, the scaling is performed from the right edge. |
| float centerY | Y-coordinate of the component transformation center point (that is, the anchor point), in percentage. **0** indicates the top edge of the component, **1** indicates the bottom edge of the component, and **0.5** indicates the vertical center of the component. The default value is **0.5**. The scaling effect along the y-axis is performed with this point as the anchor point. Different **centerY** values determine the y-direction positions of the scaling anchor point. When the value is **0**, the scaling is performed from the top edge of the component; when the value is **0.5**, the scaling is performed from the vertical center; when the value is **1**, the scaling is performed from the bottom edge. |