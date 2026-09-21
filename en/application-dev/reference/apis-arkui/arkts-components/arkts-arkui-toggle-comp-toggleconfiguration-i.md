# ToggleConfiguration

```TypeScript
declare interface ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>
```

You need a custom class to implement the **ContentModifier** API. This API inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

Whether the toggle is enabled for state switching.

**true**: The state can be changed. **false**: The state cannot be changed.

Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn: boolean
```

Whether the toggle is turned on.

**true**: The toggle is turned on. **false**: The toggle is turned off.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

Callback invoked when the toggle's state changes.

**true**: The toggle is turned on. **false**: The toggle is turned off.

**Type:** Callback&lt;boolean&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
