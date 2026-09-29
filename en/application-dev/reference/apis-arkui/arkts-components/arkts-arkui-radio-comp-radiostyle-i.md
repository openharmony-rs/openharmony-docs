# RadioStyle

```TypeScript
declare interface RadioStyle
```

Radio button color.

**Since:** 10

<!--Device-unnamed-declare interface RadioStyle--><!--Device-unnamed-declare interface RadioStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkedBackgroundColor

```TypeScript
checkedBackgroundColor?: ResourceColor
```

Color of the background when the radio button is selected.

Default value: **$r('sys.color.ohos_id_color_text_primary_activated')**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #007DFF

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RadioStyle-checkedBackgroundColor?: ResourceColor--><!--Device-RadioStyle-checkedBackgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorColor

```TypeScript
indicatorColor?: ResourceColor
```

Color of the indicator when the radio button is selected. Since API version 12, this parameter takes effect only when **indicatorType** is set to **RadioIndicatorType.TICK** or **RadioIndicatorType.DOT**.

Default value: **$r('sys.color.ohos_id_color_foreground_contrary')**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #FFFFFF

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RadioStyle-indicatorColor?: ResourceColor--><!--Device-RadioStyle-indicatorColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uncheckedBorderColor

```TypeScript
uncheckedBorderColor?: ResourceColor
```

Color of the border when the radio button is deselected.

Default value: **$r('sys.color.ohos_id_color_switch_outline_off')**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #182431

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RadioStyle-uncheckedBorderColor?: ResourceColor--><!--Device-RadioStyle-uncheckedBorderColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
