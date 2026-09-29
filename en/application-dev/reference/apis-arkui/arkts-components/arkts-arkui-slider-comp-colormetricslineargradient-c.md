# ColorMetricsLinearGradient

```TypeScript
declare class ColorMetricsLinearGradient
```

Sets the linear gradient background color of the track.

**Since:** 23

<!--Device-unnamed-declare class ColorMetricsLinearGradient--><!--Device-unnamed-declare class ColorMetricsLinearGradient-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(colorStops: ColorMetricsStop[])
```

Constructor of **ColorMetricsLinearGradient**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ColorMetricsLinearGradient-constructor(colorStops: ColorMetricsStop[])--><!--Device-ColorMetricsLinearGradient-constructor(colorStops: ColorMetricsStop[])-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorStops | [ColorMetricsStop](arkts-arkui-slider-comp-colormetricsstop-i.md)[] | Yes | Array of color stops for the linear gradient. Each element describes a color and its stop value in the gradient. |
