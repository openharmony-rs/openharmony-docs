# ICurve

Represents a curve object. Different types of curve objects can be created using APIs in this module, including [curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md) and [curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md). The curve object provides interpolation functionality through its member method [interpolate](#interpolate).

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

Calculates the interpolated value along the curve at the specified normalized time point.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fraction | number | Yes | Current normalized time.<br>Value range: [0, 1].<br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Curve interpolation corresponding to the normalized time point. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI'
let curveValue = curves.initCurve(Curve.EaseIn); // Create an ease-in curve.
let interpolatedValue: number = curveValue.interpolate(0.5); // Calculate the interpolation for half of the time.
```
