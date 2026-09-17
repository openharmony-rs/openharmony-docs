# @ohos.arkui.advanced.ComposeTitleBar

## Modules to Import

```TypeScript
import { ComposeTitleBar, ComposeTitleBarMenuItem } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ComposeTitleBarMenuItem](arkts-arkui-arkui-advanced-composetitlebar-composetitlebarmenuitem-c.md) | Declaration of the menu item on the right side. |

### Structs

| Name | Description |
| --- | --- |
| [ComposeTitleBar](arkts-arkui-arkui-advanced-composetitlebar-composetitlebar-s.md) | **ComposeTitleBar** represents a common title bar that contains a title, subtitle (optional), and profile picture (optional). It can come with a Back button for switching between pages of different levels. |

## Examples

```TypeScript
### Example 1: Implementing a Simple Title Bar

This example showcases how to implement a simple title bar, a title bar with a back arrow, and a title bar with a list of menu items on the right side.


```

```TypeScript
### Example 2: Implementing Screen Reader Announcement for the Custom Button on the Right Side

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the custom button on the right side of the title bar. This functionality is supported since API version 18.


```

```TypeScript
### Example 3: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in ComposeTitleBarMenuItem to set custom symbol icons. This functionality is supported since API version 18.
```
