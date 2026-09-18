# CheckboxGroup

The **CheckboxGroup** component is used to select or deselect all check boxes in a group.

> **NOTE**

## Child Components

Not supported

## CheckboxGroup

```TypeScript
CheckboxGroup(options?: CheckboxGroupOptions)
```

Creates a check box group for controlling the select-all or deselect-all state of check boxes within the group. Check boxes and check box groups with the same **group** value belong to the same group.

When this API is used with components that come with the caching mechanism, such as the List component, those check boxes that have not been created yet need to be manually selected or unselected. For details, see [Example 4](../../../reference/apis-arkui/arkui-ts/ts-basic-components-checkboxgroup.md#example-4-implementing-the-select-all-functionality).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CheckboxGroupOptions](arkts-arkui-checkboxgroupoptions-i.md) | No | Check box group parameters. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CheckBoxGroupConfiguration](arkts-arkui-checkboxgroupconfiguration-i.md) | You must customize this class to implement the ContentModifier interface. For details, see [contentModifier](arkts-arkui-checkboxgroup-comp-attribute.md#contentmodifier). |
| [CheckboxGroupOptions](arkts-arkui-checkboxgroupoptions-i.md) | Information about the check box group. |
| [CheckboxGroupResult](arkts-arkui-checkboxgroupresult-i.md) | Name and status of a check box group. |

### Types

| Name | Description |
| --- | --- |
| [OnCheckboxGroupChangeCallback](arkts-arkui-oncheckboxgroupchangecallback-t.md) | Information about the check box group. |

### Enums

| Name | Description |
| --- | --- |
| [SelectStatus](arkts-arkui-selectstatus-e.md) | Enumerates the selection states of check boxes in the check box group. |

## Examples

```TypeScript
### Example 1: Setting a Check Box Group

This example demonstrates how to control the select-all or deselect-all state of a check box group.


```

```TypeScript
### Example 2: Customizing Check Mark Style

This example shows how to customize the check mark style of a check box group by setting the mark attribute of CheckboxGroup.


```

```TypeScript
### Example 3: Customizing Check Box Group Style

This example demonstrates how to customize the style of a check box group through the [contentModifier](#contentmodifier21) attribute. The custom style implements a pentagonal check box group. If all check boxes are selected, a red triangle pattern is displayed inside and the title displays "fully selected"; if some are selected, the triangle pattern turns blue and the title displays "partially selected"; if none are selected, the triangle pattern is hidden and the title displays "unselected".

The contentModifier attribute is supported since API version 21.


```

```TypeScript
### Example 4: Implementing the Select-All Functionality

This example demonstrates how to manually control the selected state of the check box that has not been created when used with components that support caching, such as List.
```
