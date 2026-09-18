# initCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## initCurve

```TypeScript
function initCurve(curve?: Curve): ICurve
```

Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curve | [Curve](arkts-arkui-curves-curve-e.md) | No | Curve type.<br>Default value: **Curve.Linear** |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation curve. |
