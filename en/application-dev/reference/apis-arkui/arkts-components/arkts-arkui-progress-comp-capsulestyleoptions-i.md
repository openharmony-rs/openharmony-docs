# CapsuleStyleOptions

```TypeScript
declare interface CapsuleStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

Capsule style options.

Inherits from [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md) and [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** CapsuleStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor
```

Border color.

Default value:

API version 10: **'#33006cde'**

API version 11 or later: **'#33007dff'**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Border radius. Percentage values are not supported.

Value range: [0, min(width, height)/2]

Default value: min(width, height)/2

If an invalid value is set, the default value is used.

**Type:** LengthMetrics

**Default:** min(width, height) / 2

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

Border width. Percentage values are not supported.

Default value: **1vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Text content, which can be customized.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Text style.

Default value:

Font size (percentage values are not supported): **12fp**

Other text parameters are subject to the theme values of the [Text](arkts-arkui-text-comp.md#text) component.

**Type:** Font

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color.

Default value: **'#ff182431'**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showDefaultPercentage

```TypeScript
showDefaultPercentage?: boolean
```

Whether to display the percentage text. After this feature is enabled, the progress percentage is displayed on the progress indicator. This property does not take effect when **content** is set.

**true**: The percentage text is displayed. **false**: The percentage text is not displayed.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
