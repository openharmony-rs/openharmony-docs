# transformPoint

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## transformPoint

```TypeScript
function transformPoint(options: [number, number]): [number, number]
```

Applies the current transformation effect to a coordinate point.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [transformPoint](arkts-arkui-matrix4-matrix4transit-i.md#transformpoint)

<!--Device-matrix4-function transformPoint(options: [number, number]): [number, number]--><!--Device-matrix4-function transformPoint(options: [number, number]): [number, number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [number, number] | Yes | Point to be transformed. |

**Return value:**

| Type | Description |
| --- | --- |
| [number, number] | Coordinate point after matrix transformation, in the format [x, y]. |
