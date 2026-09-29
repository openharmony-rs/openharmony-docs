# TextPickerTextStyle

```TypeScript
declare interface TextPickerTextStyle extends PickerTextStyle
```

Defines the text style options for the text picker. Inherits from [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md).

**Inheritance/Implementation:** TextPickerTextStyle extends [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Since:** 15

<!--Device-unnamed-declare interface TextPickerTextStyle extends PickerTextStyle--><!--Device-unnamed-declare interface TextPickerTextStyle extends PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxFontSize

```TypeScript
maxFontSize?: number | string | Resource
```

Sets the maximum font size of the text, used together with minFontSize. Pass this parameter when you need to limit the maximum display size of the text to prevent it from being too large or to implement font size adaptation.

**Note:** When minFontSize and maxFontSize are set, the size in font does not take effect. For details, see the [maxFontSize](arkts-arkui-text-comp-attribute.md#maxfontsize) attribute of the Text component.

**Type:** number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerTextStyle-maxFontSize?: number | string | Resource--><!--Device-TextPickerTextStyle-maxFontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minFontSize

```TypeScript
minFontSize?: number | string | Resource
```

Sets the minimum font size of the text, used together with maxFontSize. Pass this parameter when you need to limit the minimum display size of the text to prevent it from being too small or to implement font size adaptation.

**Note:** When minFontSize and maxFontSize are set, the size in font does not take effect. The default maximum number of lines is 1, and the adaptive height mode is MIN_FONT_SIZE_FIRST. For details, see the [minFontSize](arkts-arkui-text-comp-attribute.md#minfontsize) attribute of the Text component.

**Type:** number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerTextStyle-minFontSize?: number | string | Resource--><!--Device-TextPickerTextStyle-minFontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Text overflow behavior. This property has no effect when set to **MARQUEE**. For details, see [textOverflow](arkts-arkui-text-comp-attribute.md#textoverflow).

**Type:** [TextOverflow](../arkts-apis/arkts-arkui-textoverflow-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerTextStyle-overflow?: TextOverflow--><!--Device-TextPickerTextStyle-overflow?: TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
