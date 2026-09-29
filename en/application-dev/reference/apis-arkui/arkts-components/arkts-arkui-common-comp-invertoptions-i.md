# InvertOptions

```TypeScript
declare interface InvertOptions
```

Describes the options for inverting the foreground color.

**Since:** 11

<!--Device-unnamed-declare interface InvertOptions--><!--Device-unnamed-declare interface InvertOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## high

```TypeScript
high: number
```

Value when the background color is less than the grayscale threshold.

Value range: [0, 1].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InvertOptions-high: number--><!--Device-InvertOptions-high: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## low

```TypeScript
low: number
```

Value when the background color is greater than the grayscale threshold.

Value range: [0, 1].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InvertOptions-low: number--><!--Device-InvertOptions-low: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## threshold

```TypeScript
threshold: number
```

Grayscale threshold.

Value range: [0, 1].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InvertOptions-threshold: number--><!--Device-InvertOptions-threshold: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thresholdRange

```TypeScript
thresholdRange: number
```

Threshold value range.

Value range: [0, 1].

**NOTE:** 

This range defines the upper and lower bounds of the grayscale threshold. The grayscale value changes linearly from high to low within the range.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InvertOptions-thresholdRange: number--><!--Device-InvertOptions-thresholdRange: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
