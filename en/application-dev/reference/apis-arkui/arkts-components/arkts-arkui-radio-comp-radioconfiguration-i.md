# RadioConfiguration

```TypeScript
declare interface RadioConfiguration extends CommonConfiguration<RadioConfiguration>
```

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** RadioConfiguration extends CommonConfiguration<RadioConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked: boolean
```

Whether the radio button is selected.

Default value: **false**

**true**: The radio button is selected. **false**: The radio button is not selected.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

Changes the selected state of the radio button.

The value **true** means that the radio button changes from unselected to selected, and **false** means that the radio button changes from selected to unselected.

**Type:** Callback&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

Current value of the radio button.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
