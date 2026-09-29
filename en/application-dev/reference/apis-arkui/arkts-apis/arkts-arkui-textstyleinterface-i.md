# TextStyleInterface

```TypeScript
declare interface TextStyleInterface
```

TextStyleInterface

**Since:** 12

<!--Device-unnamed-declare interface TextStyleInterface--><!--Device-unnamed-declare interface TextStyleInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color.

The default value is the theme color.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextStyleInterface-fontColor?: ResourceColor--><!--Device-TextStyleInterface-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontConfigs

```TypeScript
fontConfigs?: FontConfigs
```

Font configuration. The default value inherits [FontConfigs](arkts-arkui-fontconfigs-i.md).

**Type:** [FontConfigs](arkts-arkui-fontconfigs-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-TextStyleInterface-fontConfigs?: FontConfigs--><!--Device-TextStyleInterface-fontConfigs?: FontConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

Text font.

The default value is the theme font.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextStyleInterface-fontFamily?: ResourceStr--><!--Device-TextStyleInterface-fontFamily?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size.

The default font size is 16fp.

If the unit value of LengthMetrics is PERCENT, the current setting does not take effect and is processed as **16fp**.

Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextStyleInterface-fontSize?: LengthMetrics--><!--Device-TextStyleInterface-fontSize?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

Font style.

Default value: **FontStyle.Normal**

**Type:** [FontStyle](arkts-arkui-fontstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextStyleInterface-fontStyle?: FontStyle--><!--Device-TextStyleInterface-fontStyle?: FontStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontVariations

```TypeScript
fontVariations?: Array<FontVariation>
```

Attribute of the variable font. indicating that the attribute of the variable font is not set. The **fontVariations** attribute has a higher priority than **fontWeight**. Default value: **undefined**.

**Type:** Array&lt;[FontVariation](arkts-arkui-fontvariation-t.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextStyleInterface-fontVariations?: Array<FontVariation>--><!--Device-TextStyleInterface-fontVariations?: Array<FontVariation>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

Font weight.

For the number type, the value ranges from 100 to 900 at an interval of 100. The default value is 400. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in **FontWeight**. An excessively large value may be truncated in different fonts. If the value passed in is out of the value range or does not meet the interval requirement, the default value is used.

Default value: **FontWeight.Normal**

**Type:** number &#124; [FontWeight](arkts-arkui-fontweight-e.md) &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextStyleInterface-fontWeight?: number | FontWeight | string--><!--Device-TextStyleInterface-fontWeight?: number | FontWeight | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

Text stroke color.

The default value is the font color. If an abnormal value is set, the font color is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextStyleInterface-strokeColor?: ResourceColor--><!--Device-TextStyleInterface-strokeColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

Text stroke join style. For details about the enum values and their descriptions, see **StrokeJoinStyle**.

Default value: **StrokeJoinStyle.MITER_JOIN**, indicating a miter join with a sharp corner.

**Type:** [StrokeJoinStyle](arkts-arkui-strokejoinstyle-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextStyleInterface-strokeJoinStyle?: StrokeJoinStyle--><!--Device-TextStyleInterface-strokeJoinStyle?: StrokeJoinStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

Text stroke width. If the unit value of **LengthMetrics** is **PERCENT**, the current setting does not take effect and is processed as 0.

If the value is less than 0, the text is solid; if the value is greater than 0, the text is hollow.

The default value is **0**.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextStyleInterface-strokeWidth?: LengthMetrics--><!--Device-TextStyleInterface-strokeWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## superscript

```TypeScript
superscript?: SuperscriptStyle
```

Text superscript and subscript.

Default value: **SuperscriptStyle.NORMAL**

**Type:** [SuperscriptStyle](arkts-arkui-superscriptstyle-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextStyleInterface-superscript?: SuperscriptStyle--><!--Device-TextStyleInterface-superscript?: SuperscriptStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
