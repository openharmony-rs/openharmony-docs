# @ohos.arkui.advanced.SubHeader

## Modules to Import

```TypeScript
import { OperationOption, OperationType, SelectOptions, SubHeader, SymbolOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md) | Declare type OperationOption |
| [SelectOptions](arkts-arkui-arkui-advanced-subheader-selectoptions-c.md) | Declare type SelectOption |
| [SymbolOptions](arkts-arkui-arkui-advanced-subheader-symboloptions-c.md) | Declare type SymbolOptions |

### Structs

| Name | Description |
| --- | --- |
| [SubHeader](arkts-arkui-arkui-advanced-subheader-subheader-s.md) | The **SubHeader** component is positioned at the top of list items or content sections, organizing lists or content into distinct groups. The subheader text summarizes the content within each respective section. |

### Enums

| Name | Description |
| --- | --- |
| [OperationType](arkts-arkui-arkui-advanced-subheader-operationtype-e.md) | Defines the style of elements in the subheader operation area. |

## Examples

```TypeScript
### Example 1: Implementing an Efficiency-oriented Subheader

This example demonstrates how to implement a subheader where the left side contains an icon and a secondary title, and the right side has a button.


```

```TypeScript
### Example 2: Implementing a Double-Line Text Content-Rich Subheader

This example showcases a subheader with a primary title and a secondary title on the left, and a text button with a right arrow on the right.


```

```TypeScript
### Example 3: Implementing a Spinner Content-Rich Subheader

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

This example demonstrates the effect of setting titleBuilder in SubHeader to customize the title content. After titleBuilder is set, the primaryTitle and secondaryTitle attributes will not take effect.


```

```TypeScript
### Example 7: Customizing the Title Style

This example demonstrates how to set the font style, margin, and padding for the primary and secondary titles in the subheader.


```

```TypeScript
### Example 8: Implementing Announcement for the Button on the Right Side

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the button on the right side of the SubHeader component. This functionality is supported since API version 18.


```

```TypeScript
### Example 9: Setting the Right-Side Button to Obtain Focus by Default

This example demonstrates how to set the defaultFocus attribute in SubHeader to ensure the right-side button obtains focus by default in the focused state.

The defaultFocus API is added to [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md) since API version 18.
```
