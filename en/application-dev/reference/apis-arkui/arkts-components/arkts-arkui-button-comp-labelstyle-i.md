# LabelStyle

```TypeScript
declare interface LabelStyle
```

Label text and font style of the button.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Font of the label text.

Default value:

{

size:'16.0fp',

weight:FontWeight.Medium,

style:FontStyle.Normal,

family:'HarmonyOS Sans'

}

**Type:** Font

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

How the adaptive height is determined for the label text.

Default value: **TextHeightAdaptivePolicy.MAX_LINES_FIRST**

**Type:** [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

Maximum font size of the label text. For the setting to take effect, this attribute must be used together with **minFontSize**, **maxLines**, or layout constraint settings.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines in the label text. If this attribute is specified, the text will not exceed the specified number of lines. If there is extra text, you can use **overflow** to specify how it is displayed.

Default value: **1**

**NOTE:** 

If this parameter is set to a value less than or equal to 0, the default value is used.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

Minimum font size of the label text. For the setting to take effect, this attribute must be used together with **maxFontSize**, **maxLines**, or layout constraint settings.

**NOTE:** 

If the value of **minFontSize** is less than or equal to 0, the adaptive font size does not take effect.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Display mode when the label text is too long. Text is clipped at the transition between words. To clip text in the middle of a word, add zero-width spaces between characters.

Default value: **TextOverflow.Ellipsis**

**Type:** [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Horizontal alignment of the label text. This attribute does not take effect when the **Text** component of the child node is used to set the label. The actual text alignment mode is determined by the **textAlign** attribute of the **Text** component of the child node.

The default value is **TextAlign.Center** for wearables and **TextAlign.Start** for other devices.

**Type:** [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
