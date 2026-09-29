# CheckboxGroupOptions

```TypeScript
declare interface CheckboxGroupOptions
```

Information about the check box group.

**Since:** 8

<!--Device-unnamed-declare interface CheckboxGroupOptions--><!--Device-unnamed-declare interface CheckboxGroupOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group?: string
```

Group name.

Default value: **undefined**. In the default state, the options whose **group** value is **undefined** in [CheckboxOptions](arkts-arkui-checkbox-comp-checkboxoptions-i.md) are managed by this parameter.

**NOTE:** 

Among multiple check box groups with the same group name, only the first one takes effect.

**Type:** string

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxGroupOptions-group?: string--><!--Device-CheckboxGroupOptions-group?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
