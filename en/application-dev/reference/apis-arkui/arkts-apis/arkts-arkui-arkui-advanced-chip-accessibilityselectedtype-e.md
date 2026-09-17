# AccessibilitySelectedType

Enumerates the selected state types of the chip. It allows you to specify how accessibility services convey the component's selected state to users. Different selected state types provide distinct semantics and user experiences.

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CLICKED

```TypeScript
CLICKED = 0
```

Click type. The chip acts as a regular clickable component, without reporting any selected state to accessibility services. Use this type when the chip triggers an action but does not maintain a selected state.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CHECKED

```TypeScript
CHECKED = 1
```

Checkbox type. The chip reports its selected state to accessibility services using the [accessibilityChecked](../arkts-components/arkts-arkui-commonmethod-c.md#accessibilitychecked) attribute. Use this type for multi-select scenarios, such as tag filtering and attribute selection.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECTED

```TypeScript
SELECTED = 2
```

Radio type. The chip reports its selected state to accessibility services using the [accessibilitySelected](../arkts-components/arkts-arkui-commonmethod-c.md#accessibilityselected) attribute. Use this type for single-select scenarios, such as navigation bar tabs and radio buttons.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
