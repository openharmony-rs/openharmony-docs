# @ohos.arkui.advanced.SelectionMenu

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [SelectionMenu](arkts-arkui-arkui-advanced-selectionmenu-selectionmenu-f.md) | Defines a **SelectionMenu** component. When the input parameter is empty, both the component and its content area have a zero size, making the component invisible. For example, when a **SelectionMenu** component activated via right -click is bound to a RichEditor component using bindSelectionMenu, it will not be displayed when the **RichEditor** component receives a right-click event. |

### Interfaces

| Name | Description |
| --- | --- |
| [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | Provides the information about the selected content. |
| [EditorMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-editormenuoptions-i.md) | Describes the edit menu options. |
| [ExpandedMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-expandedmenuoptions-i.md) | Describes the expanded drop-down menu options. |
| [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | Defines the configuration options of the **SelectionMenu** component. |

## Examples

```TypeScript
### Example 1: Binding Context Menus on Selection with Different Trigger Methods

This example demonstrates the effects of a custom context menu on selection bound to text with different triggering modes.

> NOTE
> 
> The system does not currently have built-in icons for bold, italic, and other styles. The sample code uses local resource icons. When using this feature, replace the icon resources in editorMenuOptions with your own.
> 
> The sample image shows the custom menu pop-up effect triggered by mouse operations.
```

```TypeScript
### Example 2: Setting the Symbol Icon

Starting from API version 18, this example demonstrates custom Symbol type icons by setting the symbolStyle property of EditorMenuOptions.


```

```TypeScript
### Example 3: Setting the Background Material

This example demonstrates the ultra-thin background material by setting the backgroundSystemMaterial property of SelectionMenuOptions.

Starting from API version 26.0.0, the backgroundSystemMaterial property is added to SelectionMenuOptions.
```
