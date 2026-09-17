# @ohos.arkui.advanced.EditableTitleBar

## Modules to Import

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md) | Declaration of the menu item on the right side. |

### Structs

| Name | Description |
| --- | --- |
| [EditableTitleBar](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebar-s.md) | The editable title bar is a title bar that comes with button icons, typically **Cancel** on the left and **Confirm** on the right, on a multi-select or editing page. |

### Interfaces

| Name | Description |
| --- | --- |
| [EditableTitleBarOptions](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebaroptions-i.md) | Indicates the options of the editable title bar. |

### Enums

| Name | Description |
| --- | --- |
| [EditableLeftIconType](arkts-arkui-arkui-advanced-editabletitlebar-editablelefticontype-e.md) | Declaration of the left icon type. |

### Types

| Name | Description |
| --- | --- |
| [EditableTitleBarItem](arkts-arkui-editabletitlebaritem-t.md) | Declaration of the image item. |

## Examples

```TypeScript
### Example 1: Implementing an Editable Title Bar with a Custom Right Icon

This example demonstrates how to implement an editable title bar with a left icon, main title, and custom right icon area.


```

```TypeScript
### Example 2: Implementing an Editable Title Bar with Background Blur and a Profile Picture

This example demonstrates the effects of setting background blur, a profile picture, removing the right save icon, and customizing the title bar margins in EditableTitleBar.


```

```TypeScript
### Example 3: Implementing Screen Reader Announcement for the Custom Button on the Right Side

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the custom button on the right side of the title bar. This functionality is supported since API version 18.


```

```TypeScript
### Example 4: Setting the Left Icon as the Default Focus

This example demonstrates how to set the leftIconDefaultFocus attribute in EditableTitleBar to ensure the left icon obtains focus by default in the focused state.

The leftIconDefaultFocus API is added to [EditableTitleBar](#editabletitlebar-1) since API version 18.


```

```TypeScript
### Example 5: Setting a Custom Right Icon as the Default Focus

This example demonstrates how to set the defaultFocus attribute in EditableTitleBar to ensure the right icon obtains focus by default in the focused state.

The defaultFocus API is added to [EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md) since API version 18.


```

```TypeScript
### Example 6: Setting the Symbol Icon

This example demonstrates how to use symbolStyle in EditableTitleBarMenuItem to set custom symbol icons. This functionality is supported since API version 18.
```
