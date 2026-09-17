# LinearGradientBlurOptions

Linear Gradient Blur Interface

**Since:** 12

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fractionStops

```TypeScript
fractionStops: FractionStop[]
```

Gradient blur stops. The value is a set of binary arrays, each of which indicates [blur degree, blur position] and consists of numbers ranging from 0 to 1 (those less than 0 are treated as **0**, and those greater than 1 are treated as **1**). The blur positions in the arrays must be in strict ascending order. Noncompliance will be logged. For the blur settings to take effect, the number of binary arrays must be greater than or equal to 2.

**Type:** [FractionStop](arkts-arkui-fractionstop-t.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
