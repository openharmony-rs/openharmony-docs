# ChipV2AccessibilitySelectedType

```TypeScript
export declare enum ChipV2AccessibilitySelectedType
```

Defines the selected state types that can be specified for **ChipV2**. This API is used to control how the accessibility service conveys the selected state of the component to users. Different selected state types provide different semantics and user experiences.

| Name | Value | Description |  
| ---- | -- | ---- |  
| [CLICKED](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md) | 0 | Click type. The component does not report any selected state to the accessibility service and is used only as a clickable component. This is suitable for scenarios where an action is performed but no state is maintained, such as a regular button. |
| [CHECKED](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md) | 1 | Check type. The component reports its selected state to the accessibility service through the [accessibilityChecked](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitychecked) attribute. This is suitable for multi-select scenarios, such as tag filtering and attribute selection.|
| [SELECTED](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityselectedtype-e.md) | 2 | Select type. The component reports its selected state to the accessibility service through the [accessibilitySelected](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilityselected) attribute. This is suitable for scenarios indicating the currently selected item, such as navigation bar tabs and single-select list items.|

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CLICKED

```TypeScript
CLICKED = 0
```

Default type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CHECKED

```TypeScript
CHECKED = 1
```

Checked type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECTED

```TypeScript
SELECTED = 2
```

Selected type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
