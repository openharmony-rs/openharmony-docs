# ICurve

```TypeScript
interface ICurve
```

Represents a curve object. Different types of curve objects can be created using APIs in this module, including [curves.initCurve](arkts-arkui-curves-initcurve-f.md), [curves.stepsCurve](arkts-arkui-curves-stepscurve-f.md), [curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md), [curves.springCurve](arkts-arkui-curves-springcurve-f.md), [curves.springMotion](arkts-arkui-curves-springmotion-f.md), [curves.responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md), [curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md), and [curves.customCurve](arkts-arkui-curves-customcurve-f.md). You can invoke the member method [interpolate](#interpolate) through the curve object. The spring animation curves created by **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** are physical curves. The time cannot be normalized, and the interpolation cannot be obtained using the **interpolate** function.

**Since:** 9

<!--Device-curves-interface ICurve--><!--Device-curves-interface ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

Calculates the interpolation value along the curve at the specified normalized time point. For physical curves created by **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring**, the time cannot be normalized, and no valid interpolation value can be obtained by calling the **interpolate** function.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ICurve-interpolate(fraction : number) : number--><!--Device-ICurve-interpolate(fraction : number) : number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fraction | number | Yes | Current normalized time.<br>Value range: [0, 1]. <br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. <br>For spring animation curves created by **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring**, the time cannot be normalized. In this case, this parameter is meaningless, and no valid interpolation can be obtained using the **interpolate** function. |

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
