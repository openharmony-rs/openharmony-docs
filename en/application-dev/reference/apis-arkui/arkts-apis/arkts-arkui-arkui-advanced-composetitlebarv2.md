# @ohos.arkui.advanced.ComposeTitleBarV2

## Modules to Import

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, ComposeTitleBarV2MenuItemParams } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2MenuItem](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitem-c.md) | Declaration of the menu item on the right side. |

### Structs

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2-s.md) | Declaration of the composable title bar. Composable title bar represents a common title bar that contains a title, subtitle (optional), and profile picture (optional). It can come with a Back button for switching between pages of different levels. |

### Interfaces

| Name | Description |
| --- | --- |
| [ComposeTitleBarV2MenuItemParams](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitemparams-i.md) | Options for creating a menu item instance. |

### Types

| Name | Description |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | Declare the type of callback function when clicking on this menu item. |

## Examples

```TypeScript
### Example 1: Setting a Simple Title Bar

Since API version 26.0.0, the ComposeTitleBarV2 API can be used to implement a simple title bar. This example demonstrates the basic usage of ComposeTitleBarV2.
```

```TypeScript
### Example 2: Setting a Right-side Custom Button Announcement

Since API version 26.0.0, you can customize the text announced by the screen reader by configuring the following attribute APIs for the right-side custom buttons of the title bar: accessibilityText, accessibilityDescription, and accessibilityLevel.
```

```TypeScript
### Example 3: Setting a Symbol Icon

Since API version 26.0.0, a symbol icon can be configured by setting the symbolStyle attribute API of ComposeTitleBarV2MenuItem.
```
