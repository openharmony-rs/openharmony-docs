# cubicBezierCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## cubicBezierCurve

```TypeScript
function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve
```

Creates a cubic Bézier curve object. The x-coordinates (x1 and x2) of the two control points of the curve must be from 0 to 1.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-curves-function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve--><!--Device-curves-function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | X coordinate of the first point on the Bezier curve.<br>Value range: [0, 1] <br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| y1 | number | Yes | Y coordinate of the first point on the Bezier curve.<br>Value range: (-∞, +∞) <br>**NOTE:** <br>If the value is within the range of [0, 1], the curve does not exceed the start and end values of the animation. If the value is not within the range of [0, 1], the curve exceeds the start and end values during the animation. |
| x2 | number | Yes | X coordinate of the second point on the Bezier curve.<br>Value range: [0, 1] <br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| y2 | number | Yes | Y coordinate of the second point on the Bezier curve.<br>Value range: (-∞, +∞) <br>**NOTE:** <br>If the value is within the range of [0, 1], the curve does not exceed the start and end values of the animation. If the value is not within the range of [0, 1], the curve exceeds the start and end values during the animation. |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation object of the curve. You can use the **interpolate** method to obtain the interpolation at a specified normalized time point. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.cubicBezierCurve(0.1, 0.0, 0.1, 1.0); // Create a cubic Bézier curve.
```
