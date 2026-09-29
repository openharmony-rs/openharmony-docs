# PickerIndicatorStyle

```TypeScript
declare interface PickerIndicatorStyle
```

Describes the parameters of the selected item indicator style.

**Since:** 22

<!--Device-unnamed-declare interface PickerIndicatorStyle--><!--Device-unnamed-declare interface PickerIndicatorStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the selected item.

Default value: **'sys.color.comp_background_tertiary'**

**NOTE:** 

This attribute takes effect when **type** is **PickerIndicatorType.BACKGROUND**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** 'sys.color.comp_background_tertiary'

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-backgroundColor?: ResourceColor--><!--Device-PickerIndicatorStyle-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

Corner radius of the selected item background.

Default value: **{ value:12, unit:LengthUnit.vp }**, which means all four corner radii are 12 vp.

Value range: Let x be the smaller of the width and height of the selected item. The maximum value does not exceed half of x. When the value is less than 0, the default value is used; when the value is greater than the maximum value, the maximum value is used.

**NOTE:** 

1. This attribute takes effect when **type** is **PickerIndicatorType.BACKGROUND**.
2. [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md): sets the size and unit of all four corner radii
uniformly.
3. [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md): sets the size of the four corner radii separately (in vp).
4. [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md): sets the size and unit of the four corner radii
separately.

**Type:** LengthMetrics &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**Default:** { value:12, unit:LengthUnit.vp }

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-PickerIndicatorStyle-borderRadius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerColor

```TypeScript
dividerColor?: ResourceColor
```

Color of the divider.

Default value: **'sys.color.comp_divider'**

**NOTE:** 

This attribute takes effect when type is **PickerIndicatorType.DIVIDER**.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** $r('sys.color.comp_divider')

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-dividerColor?: ResourceColor--><!--Device-PickerIndicatorStyle-dividerColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: LengthMetrics
```

Distance between the divider and the end edge of the **UIPickerComponent** container.

Default value: **0**

Unit: same as **LengthMetrics**.

Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **UIPickerComponent** container. When the value is less than 0 or the sum of **startMargin** and **endMargin** exceeds the width of the **UIPickerComponent** container, the default value is used. The percentage type is not supported.

**NOTE:** 

This attribute takes effect when **type** is **PickerIndicatorType.DIVIDER**.

**Type:** LengthMetrics

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-endMargin?: LengthMetrics--><!--Device-PickerIndicatorStyle-endMargin?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: LengthMetrics
```

Distance between the divider and the start edge of the **UIPickerComponent** container.

Default value: **0**

Unit: same as **LengthMetrics**.

Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **UIPickerComponent** container. When the value is less than 0 or the sum of **startMargin** and **endMargin** exceeds the width of the **UIPickerComponent** container, the default value is used. The percentage type is not supported.

**NOTE:** 

This attribute takes effect when **type** is **PickerIndicatorType.DIVIDER**.

**Type:** LengthMetrics

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-startMargin?: LengthMetrics--><!--Device-PickerIndicatorStyle-startMargin?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

Line width of the divider.

Default value: **{ value: 2.0, unit: LengthUnit.px }**

Unit: same as **LengthMetrics**.

Value range: [0, half of the selected item height]. When **strokeWidth** is less than 0 or greater than half of the selected item height, the default value is used. Note: The selected item height can be set through the **itemHeight** attribute, and the default value is 40 vp, in which case the upper limit of the value range is 20 vp; when **itemHeight** is set to another value, the upper limit changes accordingly. The percentage type is not supported.

**NOTE:** 

1. This attribute takes effect when type is **PickerIndicatorType.DIVIDER**.
2. When the value is set through **LengthMetrics.resource**, a value of a non-length attribute is processed as
0 vp.

**Type:** LengthMetrics

**Default:** 2.0px

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-strokeWidth?: LengthMetrics--><!--Device-PickerIndicatorStyle-strokeWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: PickerIndicatorType
```

Type of the selected item indicator.

Default value: **PickerIndicatorType.BACKGROUND**

When the value of **type** is a decimal, the value rounded down is used; when the value of **type** is not within the **PickerIndicatorType** enum range, the default value is used.

**Type:** [PickerIndicatorType](arkts-arkui-uipickercomponent-comp-pickerindicatortype-e.md)

**Default:** PickerIndicatorType.BACKGROUND

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-PickerIndicatorStyle-type: PickerIndicatorType--><!--Device-PickerIndicatorStyle-type: PickerIndicatorType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
