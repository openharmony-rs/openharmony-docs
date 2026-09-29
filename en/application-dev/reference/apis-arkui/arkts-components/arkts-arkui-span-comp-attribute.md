# Span properties/events

```TypeScript
declare class SpanAttribute extends BaseSpan<SpanAttribute>
```

Inherited from [BaseSpan](arkts-arkui-span-comp-basespan-c.md).

@extends CommonMethod&lt;SpanAttribute&gt; [since 7 - 10] @extends BaseSpan&lt;SpanAttribute&gt; [since 11]

**Inheritance/Implementation:** SpanAttribute extends BaseSpan<SpanAttribute>

**Since:** 7

<!--Device-unnamed-declare class SpanAttribute extends BaseSpan<SpanAttribute>--><!--Device-unnamed-declare class SpanAttribute extends BaseSpan<SpanAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration(value: DecorationStyleInterface)
```

Sets the text decoration line style and its color. If this API is not used, the default decoration line type is TextDecorationType.None (no decoration line), the color is Color.Black, and the style is TextDecorationStyle.SOLID (solid line).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-decoration(value: DecorationStyleInterface): SpanAttribute--><!--Device-SpanAttribute-decoration(value: DecorationStyleInterface): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md) | Yes | Text decoration line style object.<br>**Note:** <br>The style parameter does not support the card capability.<br>**Since:** 12 |

## font

```TypeScript
font(value: Font)
```

Sets the text style, covering the font size, font width, Font family, and font style.

> **NOTE:** 
> 
> If fontWeight is set too large, the text may be truncated under different fonts.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SpanAttribute-font(value: Font): SpanAttribute--><!--Device-SpanAttribute-font(value: Font): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style, including the font size, font weight, font family, and font style. |

<a id="font-1"></a>

## font

```TypeScript
font(value: Font, fontConfigs?: FontConfigs)
```

Sets the text style.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-SpanAttribute-font(value: Font, fontConfigs?: FontConfigs): SpanAttribute--><!--Device-SpanAttribute-font(value: Font, fontConfigs?: FontConfigs): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Font | Yes | Text style, including the font size, font weight, font family, and font style. |
| fontConfigs | [FontConfigs](../arkts-apis/arkts-arkui-fontconfigs-i.md) | No | Font configuration, used to customize the font rendering behavior (for example, configuring variable font attributes). Pass this parameter when advanced font configuration is required. If it is not passed, the default configuration of [FontConfigs](../arkts-apis/arkts-arkui-fontconfigs-i.md) is inherited. |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

Sets the font color. If this API is not used, the default font color is '#FF182431' (dark gray), and on Wearable devices, the default is '#C5FFFFFF' (white with an opacity of about 77%).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-fontColor(value: ResourceColor): SpanAttribute--><!--Device-SpanAttribute-fontColor(value: ResourceColor): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Font color. |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

Sets the font list. If this API is not used, the default font is 'HarmonyOS Sans'.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-fontFamily(value: string | Resource): SpanAttribute--><!--Device-SpanAttribute-fontFamily(value: string | Resource): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font list.<br>When multiple fonts are used, separate them with commas ','. The priority of the fonts takes effect in order. For example: 'Arial,HarmonyOS Sans'. |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

Sets the font size. If this API is not used, the default font size is 16fp, and on Wearable devices, the default is 15fp.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-fontSize(value: number | string | Resource): SpanAttribute--><!--Device-SpanAttribute-fontSize(value: number | string | Resource): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Font size. When fontSize is of the number type, the unit fp is used. The string type supports the string form of a number type value, which can carry a unit, for example, "10" or "10fp". Percentage strings are not supported.<br>Since API version 20, the Resource type is supported. |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

Sets the font style. If this API is not used, the default font style is FontStyle.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-fontStyle(value: FontStyle): SpanAttribute--><!--Device-SpanAttribute-fontStyle(value: FontStyle): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md) | Yes | Font style. |

## fontVariations

```TypeScript
fontVariations(fontVariations: Array<FontVariation>)
```

Sets the attributes of a variable font. This is applicable to scenarios where variable dimension parameters such as font weight and width need to be dynamically adjusted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.1.

<!--Device-SpanAttribute-fontVariations(fontVariations: Array<FontVariation>): SpanAttribute--><!--Device-SpanAttribute-fontVariations(fontVariations: Array<FontVariation>): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontVariations | Array&lt;[FontVariation](../arkts-apis/arkts-arkui-fontvariation-t.md)&gt; | Yes | Array of variable font attributes. Each array element contains two fields: axis (attribute axis name) and value (attribute value). The fontVariations attribute has a higher priority than [fontWeight](#fontweight). |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

Sets the font weight of the text. If the value is too large, the text may be clipped depending on the font. If this API is not used, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

> **NOTE:** 
> 
> When the [fontVariations attribute](#fontvariations) is set at the same time, the
> fontVariations attribute takes precedence.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-fontWeight(value: number | FontWeight | ResourceStr): SpanAttribute--><!--Device-SpanAttribute-fontWeight(value: number | FontWeight | ResourceStr): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text.<br>For the number type, the value ranges from [100, 900], at an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enumvalues in FontWeight. If the value is set too large, the font may be truncated under different fonts. If a value outside the value range or not meeting the interval requirement is passed in, the default value is used. <br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

<a id="fontweight-1"></a>

## fontWeight

```TypeScript
fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

Sets the font weight of the text. If this API is not used, the default font weight is FontWeight.Normal (normal weight, corresponding to the value 400).

> **NOTE:** 
> 
> When the fontVariations attribute is set at the same time, the fontVariations attribute takes precedence.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-SpanAttribute-fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SpanAttribute--><!--Device-SpanAttribute-fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weight | number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Font weight of the text.<br>For the number type, the value ranges from 100 to 900, with an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enumvalues in FontWeight. If the value is set too large, the text may be truncated under different fonts. <br>If the value passed in is out of the value range, the default value is used. If the value passed in does not meet the interval requirement, the passed-in value is used when enableVariableFontWeight of fontWeightConfigs is set to true; otherwise, the default value is used. |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | No | Font weight configuration object, used to configure options such as the variable font weight. The default value inherits [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md). |

## letterSpacing

```TypeScript
letterSpacing(value: number | ResourceStr)
```

Sets the text character spacing. If the value is less than 0, the characters gather and overlap. If the value is greater than 0, the character spacing increases as the value increases, resulting in a sparse distribution. It is suitable for scenarios such as title layout and label text where the compactness or sparseness of characters needs to be adjusted. The string type supports the string form of a number value and can carry a unit, for example, "10"and "10fp".

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-letterSpacing(value: number | ResourceStr): SpanAttribute--><!--Device-SpanAttribute-letterSpacing(value: number | ResourceStr): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Text character spacing. <br>Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units) <br>Since API version 20, the Resource type is supported.<br>**Since:** 20 |

## lineHeight

```TypeScript
lineHeight(value: Length)
```

Sets the line height for the text. If this API is not used, the line height is automatically calculated by the system based on the font size.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SpanAttribute-lineHeight(value: Length): SpanAttribute--><!--Device-SpanAttribute-lineHeight(value: Length): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Text line height.<br> The unit is fp when the value is of the number type. When the value is of the string type, the string form of a number type value is supported, and a unit can be attached, for example, "10" and "10fp". Percentage strings are not supported. |

## textCase

```TypeScript
textCase(value: TextCase)
```

Sets the text case. If this API is not used, the default text case is TextCase.Normal.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SpanAttribute-textCase(value: TextCase): SpanAttribute--><!--Device-SpanAttribute-textCase(value: TextCase): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextCase](../arkts-apis/arkts-arkui-textcase-e.md) | Yes | Text case. |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

Sets the text shadow effect. This API supports an array as the input parameter to implement multiple text shadows. The **fill** field and the smart color picking mode are not supported.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SpanAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): SpanAttribute--><!--Device-SpanAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): SpanAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt; | Yes | Text shadow effect. You can set parameters such as the blur radius, color, and offset (offsetX/offsetY) of the shadow, and multiple shadows are supported in array form. |
