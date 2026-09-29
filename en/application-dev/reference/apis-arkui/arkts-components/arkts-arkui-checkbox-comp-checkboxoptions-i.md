# CheckboxOptions

```TypeScript
declare interface CheckboxOptions
```

Provides information about the check box.

**Since:** 8

<!--Device-unnamed-declare interface CheckboxOptions--><!--Device-unnamed-declare interface CheckboxOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group?: string
```

Name of the group to which the check box belongs (that is, the name of the **CheckboxGroup** to which it belongs).

Default value: **undefined**, used with nodes whose group information is undefined in [CheckboxGroupOptions](arkts-arkui-checkboxgroup-comp-checkboxgroupoptions-i.md).

**Note:** 

This value is useless when the [CheckboxGroup](arkts-arkui-checkboxgroup-comp.md) component is not used together.

**Type:** string

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxOptions-group?: string--><!--Device-CheckboxOptions-group?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorBuilder

```TypeScript
indicatorBuilder?: CustomBuilder
```

Custom component to indicate that the check box is selected. You can use this parameter when you need to implement the selected style other than the default check icon (such as the text, number, or custom icon). The custom component and the **Checkbox** component are aligned with their center points for display. When **indicatorBuilder** is set to **undefined** or **null**, it defaults to the state where **indicatorBuilder** is not set, and the default check icon style is used.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CheckboxOptions-indicatorBuilder?: CustomBuilder--><!--Device-CheckboxOptions-indicatorBuilder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name?: string
```

Name of the check box, used to identify different check box instances.

Default value: **undefined**.

**Type:** string

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxOptions-name?: string--><!--Device-CheckboxOptions-name?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
