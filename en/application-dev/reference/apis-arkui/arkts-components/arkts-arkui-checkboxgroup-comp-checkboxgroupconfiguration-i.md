# CheckBoxGroupConfiguration

```TypeScript
declare interface CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>
```

You must customize this class to implement the ContentModifier interface. For details, see [contentModifier](arkts-arkui-checkboxgroup-comp-attribute.md#contentmodifier).

**Inheritance/Implementation:** CheckBoxGroupConfiguration extends CommonConfiguration&lt;CheckBoxGroupConfiguration&gt;

**Since:** 21

<!--Device-unnamed-declare interface CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>--><!--Device-unnamed-declare interface CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the current check box group, used to identify and associate **Checkbox** with **CheckboxGroup**. When the value is the same as the **group** attribute of **Checkbox**, they are the same group.

**Type:** string

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-CheckBoxGroupConfiguration-name: string--><!--Device-CheckBoxGroupConfiguration-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: SelectStatus
```

Selected status of the check box group.

**Type:** [SelectStatus](arkts-arkui-checkboxgroup-comp-selectstatus-e.md)

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-CheckBoxGroupConfiguration-status: SelectStatus--><!--Device-CheckBoxGroupConfiguration-status: SelectStatus-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

Triggers a change in the selection state of the check box group. The value true indicates that the selected status changes from partially selected or unselected to fully selected, and the value false indicates that the selected status changes from fully selected or partially selected to fully unselected.

**Type:** Callback&lt;boolean&gt;

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-CheckBoxGroupConfiguration-triggerChange: Callback<boolean>--><!--Device-CheckBoxGroupConfiguration-triggerChange: Callback<boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
