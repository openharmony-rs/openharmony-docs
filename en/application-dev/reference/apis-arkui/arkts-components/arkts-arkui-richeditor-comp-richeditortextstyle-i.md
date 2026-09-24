# RichEditorTextStyle

```TypeScript
declare interface RichEditorTextStyle
```

Provides text style information.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

Style, color, and thickness of text decoration.

Default value of **type**: **TextDecorationType.None**

Default value of **color**: same as the font color

Default value of **style**: **TextDecorationStyle.SOLID**

Default value of **thicknessScale**: **1.0**

**Type:** [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Text color.

Default value: $r('sys.color.font_primary'). When [shaderStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md) is also set, shaderStyle takes precedence over fontColor.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

Sets the font list. Currently, the 'HarmonyOS Sans' font and [registered custom fonts](../arkts-apis/arkts-arkui-font.md) are supported. Default font: 'HarmonyOS Sans'.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

Sets the font feature, for example, monospaced digits. If this parameter is not specified, proportional digits are used by default. Invalid characters are disregarded, and the default is preserved.

Format: normal | &lt;feature-tag-value&gt;

Format of **&lt;feature-tag-value&gt;**: &lt;string&gt; [ &lt;integer&gt; | on | off ]

There can be multiple **&lt;feature-tag-value&gt;** values, which are separated by commas (,).

For example, the input format for monospaced clock fonts is "ss01" on.

For details about the supported font features, see [Font Feature List](arkts-arkui-text-comp-attribute.md#fontfeature).

Font features are advanced typographic features, such as ligatures and monospace, for OpenType fonts. They are typically used in custom fonts and require the support of the font itself.

For more information about the font features, visit [font-feature-settings property](https://www.w3.org/TR/css-fonts-3/#font-feature-settings-prop) and [OpenType Features](https://sparanoid.com/lab/opentype-features/).

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Length | number
```

Sets the font size. When Length is of the number type, the unit fp is used. Value range of the number type: (0, +∞). If the value is set to 0 or a negative value, the default value is used. The default font size is 16fp. Percentage strings are not supported.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

Font style.

Default value: **FontStyle.Normal**

**Type:** [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

Font weight.

For the number type, the value ranges from 100 to 900, at an interval of 100. The default value is 400. A larger value indicates a heavier font. If the value is out of range, the default value 400 is used.

For the string type, only the string form of the number type value is supported, for example, "400". In addition, "bold", "bolder", "lighter", "regular", and "medium" correspond to the respective enum values in FontWeight.

Default value: FontWeight.Normal.

**Type:** number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## halfLeading

```TypeScript
halfLeading?: boolean
```

Whether half leading is enabled.

**true**: Half leading is enabled. **false**: Half leading is not enabled.

Default value: **false**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

Sets the character spacing of the text. The default unit is fp. Default value: 0. When the value is negative, the text is compressed.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

Sets the line height of the text.

Default value: if not set, the line height adapts to the font size.

Value range of the number type: (0, +∞). If the value is not greater than 0, the line height is not limited and adapts to the font size. For the number type, the unit is fp. Percentage strings are not supported. When the lineHeight value is smaller than the actual rendered height of the text at the current font size, the [fallbackLineSpacing](arkts-arkui-richeditor-comp-attribute.md#fallbacklinespacing) attribute takes effect.

**Type:** number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

Text stroke color.

Default value: follows the font color.

When the value is invalid, it follows the font color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

Text stroke join style.

Default value: StrokeJoinStyle.MITER_JOIN.

**Type:** [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics | number
```

Text stroke width. If the unit value of LengthMetrics is [PERCENT](../arkts-apis/arkts-arkui-graphics-lengthunit-e.md), the current setting does not take effect and is treated as 0.

If the value is less than 0, the text is rendered as solid; if greater than 0, the text is rendered as outline; if equal to 0, no stroke effect is applied.

Default value: 0.

Unit: follows LengthMetrics when the type is LengthMetrics, and is vp when the type is number.

Value range: (-∞, +∞)

When set together with [shaderStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md), shaderStyle does not take effect.

**Type:** LengthMetrics &#124; number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

Text background style.

Default value:

{

color: Color.Transparent,

radius: 0

}

**Type:** [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: ShadowOptions | Array<ShadowOptions>
```

Sets the text shadow effect.

Default value: undefined, which means no text shadow effect is set.

This API supports an array as the input parameter to implement multiple text shadows.

**Note:** 

Only the shadow blur radius, color, and offset can be set. Smart color picking is not supported.

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
