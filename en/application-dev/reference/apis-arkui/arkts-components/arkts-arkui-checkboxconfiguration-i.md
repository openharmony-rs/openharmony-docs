# CheckBoxConfiguration

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md).

**Inheritance/Implementation:** CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>

**Since:** 12

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

Whether the check box is selected.

**true**: The check box is selected.

**false**: The check box is not selected.

If the **select** attribute is not set, the default value **false** is used.

If the **select** attribute is set, the attribute value is used here.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

Triggers a change in the check box selection state.

The value **true** indicates a change from unselected to selected, and **false** indicates a change from selected to unselected.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
