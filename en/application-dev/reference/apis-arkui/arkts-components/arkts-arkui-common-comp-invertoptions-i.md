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

Value used when the grayscale value of the background color is less than the threshold range.

Value range: [0, 1]. If a value less than 0 is set, the value 0 is used. If a value greater than 1 is set, the value 1 is used.

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

Value used when the grayscale value of the background color is greater than the threshold range.

Value range: [0, 1]. If a value less than 0 is set, the value 0 is used. If a value greater than 1 is set, the value 1 is used.

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

Grayscale threshold. Used together with thresholdRange. The threshold range is formed by offsetting the grayscale threshold upward and downward by thresholdRange.

Value range: [0, 1]

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

Threshold range.

Value range: [0, 1]. If a value less than 0 is set, the value 0 is used; if a value greater than 1 is set, the value 1 is used.

**Note:** 

The threshold range is formed by offsetting the grayscale threshold upward and downward by thresholdRange. Within this range, the value of the background color grayscale transitions linearly from high to low.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InvertOptions-thresholdRange: number--><!--Device-InvertOptions-thresholdRange: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
