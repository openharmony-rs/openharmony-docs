# @ohos.arkui.advanced.EditableTitleBarV2

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [EditableLeftIconV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2-c.md) | Declaration of the left icon configuration. |
| [EditableSaveButtonV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2-c.md) | Declaration of the save button configuration. |
| [EditableTitleBarMenuItemV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2-c.md) | Declaration of the menu item on the right side. |
| [EditableTitleBarStyleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2-c.md) | Declaration of the title bar style configuration. |
| [EditableTitleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2-c.md) | Declaration of the title configuration. |

### Structs

| Name | Description |
| --- | --- |
| [EditableTitleBarV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarv2-s.md) | Declaration of the editable title bar. |

### Interfaces

| Name | Description |
| --- | --- |
| [EditableLeftIconV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2options-i.md) | Indicates the options of the left icon. |
| [EditableSaveButtonV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2options-i.md) | Indicates the options of the save button. |
| [EditableTitleBarMenuItemV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2options-i.md) | Indicates the options of the menu item. |
| [EditableTitleBarStyleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2options-i.md) | Indicates the style options of the title bar. |
| [EditableTitleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2options-i.md) | Indicates the options of the title. |

### Enums

| Name | Description |
| --- | --- |
| [EditableLeftIconTypeV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticontypev2-e.md) | Declaration of the left icon type. |

### Types

| Name | Description |
| --- | --- |
| [EditableTitleBarItemV2](arkts-arkui-editabletitlebaritemv2-t.md) | Declaration of the image item. |
| [EditableTitleBarItemV2Options](arkts-arkui-editabletitlebaritemv2options-t.md) | Indicates the options of the image item. |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | Callback function when click on this menu item. |

## Examples

```TypeScript
### Example 1: Custom Title Bar of the Right-Side Icon

This example uses the EditableTitleBarV2 API to display the left icon, main title, and custom right icon area of an editable title bar.

EditableTitleBarV2 is supported since API version 26.0.0.
```

```TypeScript
### Example 2: Title Bar with Avatar and Blur Background

This example uses the EditableTitleBarV2 interfaces such as leftIcon, title, and saveButton to implement an editable title bar with blur background, avatar display, hidden right-side save button and custom title bar margins.

EditableTitleBarV2 is supported since API version 26.0.0.
```

```TypeScript
### Example 3: Custom Button Announcement on the Right

This example uses the right-side custom button attributes such as accessibilityText and accessibilityDescription of the EditableTitleBarV2 API to customize the screen reader announcement text of the editable title bar.

The EditableTitleBarV2 API is supported since API version 26.0.0.
```

```TypeScript
### Example 4: Setting the Left Icon as the Default Focus

In the focus state, this example uses the defaultFocus attribute of [EditableLeftIconV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2-c.md) configured through the EditableTitleBarV2 API to enable the left icon on the editable title bar to obtain focus by default.

The EditableTitleBarV2 API is supported since API version 26.0.0.
```

```TypeScript
### Example 5: Setting the Right Custom Icon as the Default Focus

In the focus state, this example uses the right icon attribute defaultFocus of EditableTitleBarV2 to enable the right icon on the editable title bar to obtain focus by default.

The EditableTitleBarV2 API is supported since API version 26.0.0.
```

```TypeScript
### Example 6: Setting a Symbol Icon

This example implements the custom symbol icon feature of the editable title bar through the symbolStyle attribute of the EditableTitleBarV2 component.

The EditableTitleBarV2 API is supported since API version 26.0.0.
```
