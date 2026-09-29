# combine

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## combine

```TypeScript
function combine(options: Matrix4Transit): Matrix4Transit
```

Combines the effects of two matrices to generate a new matrix object. The matrix that calls this API will be changed.

> **NOTE:** 
> 
> The transformation results of **matrixA.combine(matrixB)** and **matrixB.combine(matrixA)** are different. The
> call order of **combine()** determines the order in which the transformations are combined. For example,
> translating first and then scaling produces a different transformation effect from scaling first and then
> translating. Select the correct call order based on the expected transformation effect. To keep the original
> matrix unchanged, call **copy()** before calling **combine()**, for example, **matrixA.copy().combine(matrixB)**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [combine](arkts-arkui-matrix4-matrix4transit-i.md#combine)

<!--Device-matrix4-function combine(options: Matrix4Transit): Matrix4Transit--><!--Device-matrix4-function combine(options: Matrix4Transit): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Yes | Matrix object to be combined. Its transformation effect will be combined with the identity matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after combination. |
