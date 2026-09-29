# rotate

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## rotate

```TypeScript
function rotate(options: RotateOption): Matrix4Transit
```

Rotates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [rotate](arkts-arkui-matrix4-matrix4transit-i.md#rotate)

<!--Device-matrix4-function rotate(options: RotateOption): Matrix4Transit--><!--Device-matrix4-function rotate(options: RotateOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | Yes | Rotation options for setting the rotation axis vector (x/y/z), rotation angle, and transform center point offset. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after rotation. |
