# CapsuleStyleOptions

```TypeScript
declare interface CapsuleStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

Capsule style options.

Inherits from [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** CapsuleStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface CapsuleStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions--><!--Device-unnamed-declare interface CapsuleStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor
```

Inner stroke color.

Default value:

API version 10: '#33006cde'

API version 11 and later: '#33007dff'

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-borderColor?: ResourceColor--><!--Device-CapsuleStyleOptions-borderColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Corner radius of the capsule progress bar (percentage setting not supported).

Value range: [0, component height/2]. Default value: component height/2.

An invalid value is handled as the default value.

**Type:** LengthMetrics

**Default:** min(width, height) / 2

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CapsuleStyleOptions-borderRadius?: LengthMetrics--><!--Device-CapsuleStyleOptions-borderRadius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

Inner stroke width.

Default value: 1vp

Value range: a value greater than or equal to 0. Percentage setting not supported.

A value out of range or an invalid value is handled as the default value.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-borderWidth?: Length--><!--Device-CapsuleStyleOptions-borderWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Text content, which can be customized by the application.

Pass this parameter when custom text needs to be displayed on the capsule progress bar. If it is not passed, no text is displayed (to display the percentage text, set showDefaultPercentage to true).

Since API version 20, the Resource type is supported.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-content?: ResourceStr--><!--Device-CapsuleStyleOptions-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Text style.

Default value:

Text size (percentage setting not supported): 12fp

Other text parameters follow the theme values of the [Text](arkts-arkui-text-comp.md) component.

**Type:** Font

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-font?: Font--><!--Device-CapsuleStyleOptions-font?: Font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Text color.

Default value: '#ff182431'

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-fontColor?: ResourceColor--><!--Device-CapsuleStyleOptions-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showDefaultPercentage

```TypeScript
showDefaultPercentage?: boolean
```

Whether to display the percentage text. When enabled, the progress bar displays the percentage of the current progress. This attribute does not take effect when the content attribute is set.

true: displays the percentage text; false: does not display the percentage text.

Default value: false

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CapsuleStyleOptions-showDefaultPercentage?: boolean--><!--Device-CapsuleStyleOptions-showDefaultPercentage?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
