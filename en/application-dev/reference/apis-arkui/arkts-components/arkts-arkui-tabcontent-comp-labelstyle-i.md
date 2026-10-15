# LabelStyle

```TypeScript
declare interface LabelStyle
```

Represents a style object for the label text and font.

**Since:** 10

<!--Device-unnamed-declare interface LabelStyle--><!--Device-unnamed-declare interface LabelStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Font of the label text.

When the tab is a subtab, the default font is in 16.0 fp size, 'HarmonyOS Sans' family, normal font style, medium weight when selected, and normal weight when not selected.

When the tab is a bottom tab, the default font is in 10.0 fp size, 'HarmonyOS Sans' family, normal font style, and medium weight.

The default font size of the bottom tab page is 12.0 fp since API version 12.

**Type:** Font

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-font?: Font--><!--Device-LabelStyle-font?: Font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy?: TextHeightAdaptivePolicy
```

How the adaptive height is determined for the label text. By default, the **maxLines** settings are prioritized.

**Type:** [TextHeightAdaptivePolicy](../arkts-apis/arkts-arkui-textheightadaptivepolicy-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy--><!--Device-LabelStyle-heightAdaptivePolicy?: TextHeightAdaptivePolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

Maximum font size of the label text. It cannot be set in percentage. For the setting to take effect, this attribute must be used together with **minFontSize**, **maxLines**, or layout constraint settings. When the adaptive text size is set, **font.size** does not take effect. The default value is **0.0fp**, indicating that the adaptive text size has no effect.

Value range: [minFontSize, +∞) This parameter does not take effect when the value is abnormal.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 
- API version 11+: 0.0fp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-maxFontSize?: number | ResourceStr--><!--Device-LabelStyle-maxFontSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines in the label text. If this attribute is specified, the text will not exceed the specified number of lines. You can use **textOverflow** to specify how to represent text overflow. Default value: **1**

Value range: [1, +∞) If the value is abnormal, the default value is used.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-maxLines?: number--><!--Device-LabelStyle-maxLines?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

Minimum font size of the label text. It cannot be set in percentage. For the setting to take effect, this attribute must be used together with **maxFontSize**, **maxLines**, or layout constraint settings. When the adaptive text size is set, **font.size** does not take effect. The default value is **0.0fp**, indicating that the adaptive text size has no effect.

Value range: (0, +∞) This parameter does not take effect when the value is abnormal.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 
- API version 11+: 0.0fp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-minFontSize?: number | ResourceStr--><!--Device-LabelStyle-minFontSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Display mode when the label text is too long. By default, an ellipsis (...) is used to represent text overflow.

**Type:** [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LabelStyle-overflow?: TextOverflow--><!--Device-LabelStyle-overflow?: TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedColor

```TypeScript
selectedColor?: ResourceColor
```

Font color of the label text when it is selected.

Default value: **#FF007DFF**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #FF007DFF

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LabelStyle-selectedColor?: ResourceColor--><!--Device-LabelStyle-selectedColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unselectedColor

```TypeScript
unselectedColor?: ResourceColor
```

Font color of the label text when it is not selected.

Default value: **#99182431**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #99182431

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LabelStyle-unselectedColor?: ResourceColor--><!--Device-LabelStyle-unselectedColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
