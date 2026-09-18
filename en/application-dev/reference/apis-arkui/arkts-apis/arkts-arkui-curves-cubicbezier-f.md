# cubicBezier

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## cubicBezier

```TypeScript
function cubicBezier(x1: number, y1: number, x2: number, y2: number): string
```

Creates a cubic Bézier curve. The curve values must be between 0 and 1.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | Value range [0, 1]. Note: If the value is less than 0, 0 is used. If the value is greater than 1, 1 is used. |
| y1 | number | Yes | Value range (-∞, +∞). |
| x2 | number | Yes | Value range [0, 1]. Note: If the value is less than 0, 0 is used. If the value is greater than 1, 1 is used. |
| y2 | number | Yes | Value range (-∞, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Cubic Bézier curve object. |
