# CheckBoxConfiguration

```TypeScript
declare interface CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>
```

You need a custom class to implement the **ContentModifier** API. It inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>--><!--Device-unnamed-declare interface CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the check box.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CheckBoxConfiguration-name: string--><!--Device-CheckBoxConfiguration-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

Whether the check box is selected. The value **true** means the check box is selected, and **false** means the opposite.

If the **select** attribute is not set, the default value is **false**.

If the **select** attribute is set, the attribute value is used here.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CheckBoxConfiguration-selected: boolean--><!--Device-CheckBoxConfiguration-selected: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

Callback invoked when the selected state of the check box changes. The value **true** indicates the checkbox is set to the selected state, and **false** indicates the opposite.

**Type:** Callback&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>--><!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
