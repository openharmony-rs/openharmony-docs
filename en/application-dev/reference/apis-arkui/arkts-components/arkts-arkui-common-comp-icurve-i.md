# ICurve

```TypeScript
interface ICurve
```

Interface for curve object.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

Calculates the interpolated value along the curve at the specified normalized time point.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fraction | number | Yes | Current normalized time.<br>Value range: [0, 1].<br>**NOTE:** <br>A value less than 0 is treated as **0**. A value greater than 1 is treated as **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Curve interpolation corresponding to the normalized time point. |
