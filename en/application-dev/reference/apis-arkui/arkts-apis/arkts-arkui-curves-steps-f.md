# steps

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## steps

```TypeScript
function steps(count: number, end: boolean): string
```

Creates a step curve.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [stepsCurve](arkts-arkui-curves-stepscurve-f.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of steps. The value must be a positive integer. |
| end | boolean | Yes | Whether the step change occurs at the start or end of each interval.<br>- **true**: The step change occurs at the end of each interval.<br>- **false**: The step change occurs at the start of each interval. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Steps curve object. |
