# stepsCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## stepsCurve

```TypeScript
function stepsCurve(count: number, end: boolean): ICurve
```

Constructs a step curve object, which divides the animation process into several equal intervals, with a step change occurring at the start or end of each interval.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-curves-function stepsCurve(count: number, end: boolean): ICurve--><!--Device-curves-function stepsCurve(count: number, end: boolean): ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of steps. The value must be a positive integer.<br>Value range: [1, +∞) <br>**NOTE:** <br>If a value less than 1 is set, the value **1** is used. If a non-integer value is passed, the value is rounded down. |
| end | boolean | Yes | Whether the step change occurs at the start or end of each interval.<br>- **true**: The step change occurs at the end of each interval. <br>- **false**: The step change occurs at the start of each interval. |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation object of the curve. You can use the **interpolate** method to obtain the interpolation at a specified normalized time point. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.stepsCurve(9, true);  // Create a step curve.
```
