# PickerComponentTextStyle

```TypeScript
declare interface PickerComponentTextStyle
```

Defines the text style shared by DatePickerComponent and UIPickerComponent.

**Since:** 26.1.0

<!--Device-unnamed-declare interface PickerComponentTextStyle--><!--Device-unnamed-declare interface PickerComponentTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Font color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PickerComponentTextStyle-color?: ResourceColor--><!--Device-PickerComponentTextStyle-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Text style. Only size and weight are supported.

**Type:** Font

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PickerComponentTextStyle-font?: Font--><!--Device-PickerComponentTextStyle-font?: Font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | ResourceStr
```

Maximum font size for the text. Used with minFontSize to enable font scaling. When both minFontSize and maxFontSize are set, the size property in font is ignored. For details, see maxFontSize of TextAttribute.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PickerComponentTextStyle-maxFontSize?: number | ResourceStr--><!--Device-PickerComponentTextStyle-maxFontSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | ResourceStr
```

Minimum font size for the text. Used with maxFontSize to enable font scaling. When both minFontSize and maxFontSize are set, the size property in font is ignored. For details, see minFontSize of TextAttribute.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PickerComponentTextStyle-minFontSize?: number | ResourceStr--><!--Device-PickerComponentTextStyle-minFontSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Text overflow behavior. This property has no effect when set to MARQUEE. For details, see textOverflow of TextAttribute.

**Type:** [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PickerComponentTextStyle-overflow?: TextOverflow--><!--Device-PickerComponentTextStyle-overflow?: TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
