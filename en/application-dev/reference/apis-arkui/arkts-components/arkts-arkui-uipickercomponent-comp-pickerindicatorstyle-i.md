# PickerIndicatorStyle

```TypeScript
declare interface PickerIndicatorStyle
```

Sets parameters of the selected item indicator style.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the selected item.

Default value: 'sys.color.comp_background_tertiary'

**NOTE:** 

This parameter takes effect only when **type** is set to **PickerIndicatorType.BACKGROUND**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** 'sys.color.comp_background_tertiary'

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

Background border radius of the selected item.

Value range: no more than half of the smaller value between the width and height of the selected item. If the value Default value: { value:12, unit:LengthUnit.vp }, meaning 12 vp for all corners

is less than 0, the default value is used. If the value is greater than the maximum value, the maximum value is used.

NOTE

1. This parameter takes effect only when **type** is set to **PickerIndicatorType.BACKGROUND**.
2. [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md): Sets the size and unit of the four corner radii
in a unified manner.
3. [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md): Sets the size (unit: vp) of the four corner radii individually.
4. [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md): Sets the size and unit of the four corner radii
individually.

**Type:** LengthMetrics &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**Default:** { value:12, unit:LengthUnit.vp }

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerColor

```TypeScript
dividerColor?: ResourceColor
```

Color of the divider.

Default value: 'sys.color.comp_divider'

**NOTE:** 

This parameter takes effect only when **type** is set to **PickerIndicatorType.DIVIDER**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** $r('sys.color.comp_divider')

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: LengthMetrics
```

Distance between the divider and the end edge of the **UIPickerComponent** container.

Default value: 0

Unit: same as that of **LengthMetrics**

Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **UIPickerComponent** container. If the value is less than 0 or the sum of **startMargin** and **endMargin** exceeds the width of the **UIPickerComponent** container, the default value is used. Percentages are not supported.

**NOTE:** 

This parameter takes effect only when **type** is set to **PickerIndicatorType.DIVIDER**.

**Type:** LengthMetrics

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: LengthMetrics
```

Distance between the divider and the start edge of the **UIPickerComponent** container.

Default value: 0

Unit: same as that of **LengthMetrics**

Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **UIPickerComponent** container. If the value is less than 0 or the sum of **startMargin** and **endMargin** exceeds the width of the **UIPickerComponent** container, the default value is used. Percentages are not supported.

NOTE

This parameter takes effect only when **type** is set to **PickerIndicatorType.DIVIDER**.

**Type:** LengthMetrics

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

Stroke width of the divider.

Default value: 2.0px.

Unit: same as that of **LengthMetrics**

Value range: [0, half the height of the selected item (that is, 20 vp)]. If the value of **strokeWidth** is less than 0 or greater than half the height of the selected item, the default value is used. Percentages are not supported.

NOTE

1. This parameter takes effect only when **type** is set to **PickerIndicatorType.DIVIDER**.
2. If this parameter is set in **LengthMetrics.resource** mode, the value of a non-length attribute will be treated
as 0 vp.

**Type:** LengthMetrics

**Default:** 2.0px

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: PickerIndicatorType
```

Type of the selected item indicator.

Default value: PickerIndicatorType.BACKGROUND

If the value of **type** is a decimal number, the integer after rounding down is used. If the value of **type** is not within the value range of **PickerIndicatorType**, the default value is used.

**Type:** [PickerIndicatorType](arkts-arkui-uipickercomponent-comp-pickerindicatortype-e.md)

**Default:** PickerIndicatorType.BACKGROUND

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
