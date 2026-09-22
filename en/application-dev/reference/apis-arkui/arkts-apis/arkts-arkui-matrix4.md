# @ohos.matrix4(Matrix Transformation)

Provides matrix transformation capabilities for components, including translation, rotation, and scaling. For details, see Transformation.

**Matrix4** can be used in the following scenarios:

In Transformation, the [transform](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#transform-1) API uses the **Matrix4** object to display the matrix transformation in two-dimensional transformation, and the [transform3D](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#transform3d) API uses the **Matrix4** object to set the three-dimensional transformation matrix for a component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [combine](arkts-arkui-matrix4-combine-f.md) | Combines the effects of two matrices to generate a new matrix object. |
| [copy](arkts-arkui-matrix4-copy-f.md) | Copies this matrix object. |
| [identity](arkts-arkui-matrix4-identity-f.md) | Constructs an identity matrix. |
| [init](arkts-arkui-matrix4-init-f.md) | Matrix constructor, which is used to create a 4 x 4 matrix with the input parameters. Column-major order is used. |
| [invert](arkts-arkui-matrix4-invert-f.md) | Inverts this matrix object. |
| [rotate](arkts-arkui-matrix4-rotate-f.md) | Rotates this matrix object along the x, y, and z axes. |
| [scale](arkts-arkui-matrix4-scale-f.md) | Scales this matrix object along the x, y, and z axes. |
| [transformPoint](arkts-arkui-matrix4-transformpoint-f.md) | Applies the current transformation effect to a coordinate point. |
| [translate](arkts-arkui-matrix4-translate-f.md) | Translates this matrix object along the x, y, and z axes. |

### Interfaces

| Name | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Implements a **Matrix4Transit** object. |
| [Point](arkts-arkui-matrix4-point-i.md) | Defines the data structure of a coordinate point. |
| [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | Describes the configuration options for polygon-to-polygon transformation mapping. |
| [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | Describes the rotation parameters. |
| [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | Describes the scale parameters. |
| [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | Describes the translation parameters. |
