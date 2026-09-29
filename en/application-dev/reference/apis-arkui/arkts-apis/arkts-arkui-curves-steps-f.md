# steps

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## steps

```TypeScript
function steps(count: number, end: boolean): string
```

Constructs a step curve object, which divides the animation time into a specified number of intervals. The attribute value remains unchanged within each interval and changes at the interval boundaries.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [stepsCurve](arkts-arkui-curves-stepscurve-f.md)

<!--Device-curves-function steps(count: number, end: boolean): string--><!--Device-curves-function steps(count: number, end: boolean): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of steps. The value must be a positive integer.<br>Value range: [1, +∞) <br>**NOTE:** <br>A value less than 1 evaluates to the value **1**. |
| end | boolean | Yes | Whether the step change occurs at the start or end of each interval.<br>- **true**: The step change occurs at the end of each interval. <br>- **false**: The step change occurs at the start of each interval. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Steps curve object. |
