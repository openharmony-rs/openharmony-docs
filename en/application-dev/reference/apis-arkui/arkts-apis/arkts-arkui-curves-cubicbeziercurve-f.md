# cubicBezierCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## cubicBezierCurve

```TypeScript
function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve
```

Creates a cubic Bezier curve, with x-coordinates automatically normalized between 0 and 1.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | X coordinate of the first point on the Bezier curve.<br>Value range: [0, 1]<br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| y1 | number | Yes | Y coordinate of the first point on the Bezier curve.<br>Value range: (-∞, +∞) |
| x2 | number | Yes | X coordinate of the second point on the Bezier curve.<br>Value range: [0, 1]<br>**NOTE:** <br> A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |
| y2 | number | Yes | Y coordinate of the second point on the Bezier curve.<br>Value range: (-∞, +∞) |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation curve. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.cubicBezierCurve(0.1, 0.0, 0.1, 1.0); // Create a cubic Bézier curve.
```
