# LinearGradientBlurOptions

```TypeScript
declare interface LinearGradientBlurOptions
```

Linear Gradient Blur Interface

**Since:** 12

<!--Device-unnamed-declare interface LinearGradientBlurOptions--><!--Device-unnamed-declare interface LinearGradientBlurOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: GradientDirection
```

Gradient blur direction.

Default value:

GradientDirection.Bottom

**Type:** [GradientDirection](../arkts-apis/arkts-arkui-gradientdirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LinearGradientBlurOptions-direction: GradientDirection--><!--Device-LinearGradientBlurOptions-direction: GradientDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fractionStops

```TypeScript
fractionStops: FractionStop[]
```

Each binary array stored in the array (value from 0 to 1; values less than 0 are treated as 0, and values greater than 1 are treated as 1) represents [blur fraction, blur position]. The blur positions must be strictly increasing. If the data passed in by the developer does not comply with the specification, a log is recorded. The number of binary arrays in the gradient blur array must be greater than or equal to 2; otherwise, the gradient blur does not take effect.

**Type:** [FractionStop](arkts-arkui-common-comp-fractionstop-t.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LinearGradientBlurOptions-fractionStops: FractionStop[]--><!--Device-LinearGradientBlurOptions-fractionStops: FractionStop[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
