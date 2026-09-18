# @ohos.arkui.advanced.SubHeaderV2(api/@ohos.arkui.advanced.SubHeaderV2.d.ts)

## Modules to Import

```TypeScript
import { SubHeaderV2IconType, SubHeaderV2Title, SubHeaderV2Select, SubHeaderV2, SubHeaderV2OperationType, SubHeaderV2OperationItem, SubHeaderV2OperationItemType } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SubHeaderV2OperationItem](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitem-c.md) | Represents an item in the operation area. |
| [SubHeaderV2Select](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2select-c.md) | Defines the content and events for selection. |
| [SubHeaderV2Title](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2title-c.md) | Defines the title settings for the subheader. |

### Structs

| Name | Description |
| --- | --- |
| [SubHeaderV2](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2-s.md) | The component is positioned at the top of list items or content sections, organizing lists or content into distinct groups. The subheader text summarizes the content within each respective section. |

### Interfaces

| Name | Description |
| --- | --- |
| [SubHeaderV2OperationItemOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md) | Defines the options for initializing a **SubHeaderV2OperationItem** object. |
| [SubHeaderV2SelectOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2selectoptions-i.md) | Defines the options for initializing a **SubHeaderV2Select** object. |
| [SubHeaderV2TitleOptions](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2titleoptions-i.md) | Defines the options for initializing a **SubHeaderV2Title** object. |

### Enums

| Name | Description |
| --- | --- |
| [SubHeaderV2OperationType](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationtype-e.md) | Defines the style of elements in the operation area. |

### Types

| Name | Description |
| --- | --- |
| [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md) | [SubHeaderV2IconType](arkts-arkui-subheaderv2icontype-t.md) |
| [SubHeaderV2OperationItemAction](arkts-arkui-subheaderv2operationitemaction-t.md) | Defines the callback for items in the operation area. |
| [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md) | [SubHeaderV2OperationItemType](arkts-arkui-subheaderv2operationitemtype-t.md) |
| [SubHeaderV2SelectOnSelect](arkts-arkui-subheaderv2selectonselect-t.md) | Defines the callback invoked when an item in the drop-down list box is selected. |
| [SubHeaderV2TitleBuilder](arkts-arkui-subheaderv2titlebuilder-t.md) | Defines the callback used to customize the content of the title area. |

## Examples

```TypeScript
### Example 1: Implementing an Efficiency-oriented Subheader

This example demonstrates how to implement a subheader where the left side contains an icon and a secondary title, and the right side has a text button.


```

```TypeScript
### Example 2: Implementing a Double-Line Text Content-rich Subheader

This example showcases a subheader with a primary title and a secondary title on the left, and a text button with a right arrow on the right.


```

```TypeScript
### Example 3: Implementing a Spinner Content-rich Subheader

This example showcases a subheader with content and events for selection on the left, and an icon-attached button on the right.


```

```TypeScript
### Example 4: Setting the Icon Symbol for the Left Side

This example demonstrates how to set the icon symbol for the left side of the subheader.


```

```TypeScript
### Example 5: Setting the Icon Symbol for the Right Side

The following example shows how to set operationType to OperationType.ICON_GROUP for the right side of the subheader, with operationItem set to a symbol icon.


```

```TypeScript
### Example 6: Customizing Title Content

This example demonstrates how to customize the title content with a titleBuilder object for the SubHeaderV2 component.


```

```TypeScript
### Example 7: Customizing the Title Style

This example demonstrates how to set custom font styles for the primary and secondary titles in the SubHeaderV2 component.


```

```TypeScript
### Example 8: Implementing Announcement for the Button on the Right Side

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the button on the right side of the SubHeaderV2 component.


```

```TypeScript
### Example 9: Setting the Right-Side Button to Obtain Focus by Default

This example demonstrates how to set defaultFocus in SubHeaderV2 to ensure the right-side button obtains focus by default in the focused state.

The defaultFocus API is added to [SubHeaderV2OperationItem](arkts-arkui-arkui-advanced-subheaderv2-subheaderv2operationitemoptions-i.md) since API version 18.
```
