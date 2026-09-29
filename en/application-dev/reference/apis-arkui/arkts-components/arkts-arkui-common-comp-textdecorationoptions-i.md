# TextDecorationOptions

```TypeScript
declare interface TextDecorationOptions
```

Provides the text decoration options.

**Since:** 12

<!--Device-unnamed-declare interface TextDecorationOptions--><!--Device-unnamed-declare interface TextDecorationOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Sets the color of the text decoration line.

Default value: Color.Black.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDecorationOptions-color?: ResourceColor--><!--Device-TextDecorationOptions-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: TextDecorationStyle
```

Sets the style of the text decoration line.

Default value: TextDecorationStyle.SOLID.

**Type:** [TextDecorationStyle](../arkts-apis/arkts-arkui-textdecorationstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDecorationOptions-style?: TextDecorationStyle--><!--Device-TextDecorationOptions-style?: TextDecorationStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
thicknessScale?: number
```

Sets the thickness scaling ratio of the text decoration line.

Default value: 1.0

Value range: [0, +∞)

**Note:** Negative values are processed as the default value.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextDecorationOptions-thicknessScale?: number--><!--Device-TextDecorationOptions-thicknessScale?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TextDecorationType
```

Sets the text decoration line type.

**Type:** [TextDecorationType](../arkts-apis/arkts-arkui-textdecorationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextDecorationOptions-type: TextDecorationType--><!--Device-TextDecorationOptions-type: TextDecorationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
