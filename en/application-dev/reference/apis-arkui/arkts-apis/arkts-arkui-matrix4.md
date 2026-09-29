# @ohos.matrix4(Matrix Transformation)

Provides matrix transformation capabilities for components, including translation, rotation, and scaling. For details, see [Transformation](../arkts-components/arkts-arkui-common-comp.md).

**Matrix4** can be used in the following scenarios:

In [Transformation](../arkts-components/arkts-arkui-common-comp.md), the [transform](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#transform-1) API uses the **Matrix4** object to set the two -dimensional transformation matrix for a component, and the [transform3D](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#transform3d) API uses the **Matrix4** object to set the three-dimensional transformation matrix for a component.

**Since:** 7

<!--Device-unnamed-declare namespace matrix4--><!--Device-unnamed-declare namespace matrix4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [combine](arkts-arkui-matrix4-combine-f.md) | Combines the effects of two matrices to generate a new matrix object. The matrix that calls this API will be changed. |
| [copy](arkts-arkui-matrix4-copy-f.md) | Copies this matrix object. |
| [identity](arkts-arkui-matrix4-identity-f.md) | Initializes a matrix and returns an identity matrix object, which can serve as the basis for subsequent matrix transformation operations. |
| [init](arkts-arkui-matrix4-init-f.md) | Constructor of **Matrix4**. It is used to create a 4 x 4 matrix based on the input parameters. The matrix is column -major, that is, the 16 values in the input array are filled into the matrix column by column: array[0] to array[3] form the first column, array[4] to array[7] form the second column, array[8] to array[11] form the third column, and array[12] to array[15] form the fourth column. When only an identity matrix is required, you are advised to use **matrix4.identity()**. |
| [invert](arkts-arkui-matrix4-invert-f.md) | Inverts this matrix object. The matrix that calls this API will be changed. |
| [rotate](arkts-arkui-matrix4-rotate-f.md) | Rotates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed. |
| [scale](arkts-arkui-matrix4-scale-f.md) | Scales this matrix object along the x, y, and z axes. The matrix that calls this API will be changed. |
| [transformPoint](arkts-arkui-matrix4-transformpoint-f.md) | Applies the current transformation effect to a coordinate point. |
| [translate](arkts-arkui-matrix4-translate-f.md) | Translates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed. |

### Interfaces

| Name | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Implements a matrix object. It supports combining multiple transformation effects by chained calls of the **translate**, **scale**, **rotate**, and **skew** APIs. |
| [Point](arkts-arkui-matrix4-point-i.md) | Defines the data structure of a coordinate point. |
| [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | Describes the configuration options for polygon-to-polygon transformation mapping. |
| [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | Describes the rotation parameters. |
| [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | Describes the scale parameters. |
| [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | Describes the translation parameters. |
