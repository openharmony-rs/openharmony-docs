# scale

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## scale

```TypeScript
function scale(options: ScaleOption): Matrix4Transit
```

Scales this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [scale](arkts-arkui-matrix4-matrix4transit-i.md#scale)

<!--Device-matrix4-function scale(options: ScaleOption): Matrix4Transit--><!--Device-matrix4-function scale(options: ScaleOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | Yes | Scaling options for setting the scale multiples of the x-axis, y-axis, and z-axis and the coordinates of the transform center point. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after scaling. |
