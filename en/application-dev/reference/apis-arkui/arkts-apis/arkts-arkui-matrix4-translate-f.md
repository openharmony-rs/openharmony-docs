# translate

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## translate

```TypeScript
function translate(options: TranslateOption): Matrix4Transit
```

Translates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [translate](arkts-arkui-matrix4-matrix4transit-i.md#translate)

<!--Device-matrix4-function translate(options: TranslateOption): Matrix4Transit--><!--Device-matrix4-function translate(options: TranslateOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | Yes | Translation options for setting the translation distance on the x-axis, y- axis, and z-axis. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after translation. |
