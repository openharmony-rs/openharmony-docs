# Checkbox

**Checkbox** is a component that is used to enable or disable an option.

> **NOTE** > > Since API version 11, the default style of the **Checkbox** component is changed from rounded square to circle.

## Child Components

Not supported

## Checkbox

```TypeScript
Checkbox(options?: CheckboxOptions)
```

Creates a check box.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | No | Check box parameters. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CheckBoxConfiguration](arkts-arkui-checkboxconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [CheckboxOptions](arkts-arkui-checkboxoptions-i.md) | Provides information about the check box. |

### Types

| Name | Description |
| --- | --- |
| [OnCheckboxChangeCallback](arkts-arkui-oncheckboxchangecallback-t.md) | Represents the callback invoked when the selected state of the check box changes. |

## Examples

```TypeScript
### Example 1: Setting the Check Box Shape

This example shows how to set CheckBoxShape to implement check boxes in circle and rounded square shapes.


```

```TypeScript
### Example 2: Setting the Check Box Color

This example demonstrates how to set mark to customize the color of a check box.


```

```TypeScript
### Example 3: Customizing the Check Box Style

This example demonstrates how to implement a custom check box style using the [contentModifier](#contentmodifier12) attribute, which implements a pentagon-shaped check box. When the check box is selected, a red triangle pattern is displayed inside and the title shows "Selected"; when the check box is deselected, the red triangle pattern is hidden and the title shows "Unselected".


```

```TypeScript
### Example 4: Setting the Text Check Box Style

This example configures the selected style of a check box to display as text using the indicatorBuilder property.


```

```TypeScript
### Example 5: Obtaining the Check Box Selection Information

This example demonstrates how to obtain selection information by selecting check boxes and check box groups.


```

```TypeScript
### Example 6: Implementing Swipe-based Multi-Selection

This example implements swipe-based multi-selection for Checkbox components through gesture event configuration.
```
