# @ohos.arkui.advanced.ToolBar

## Modules to Import

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | Provides APIs for setting the height (**height**), background color (**backgroundColor**), left and right padding (**padding**, which only takes effect when there are fewer than five items) of the toolbar, and whether to display the pressed state effect (**stateEffect**). |
| [ToolBarOption](arkts-arkui-arkui-advanced-toolbar-toolbaroption-c.md) | Defines the content and attributes of a toolbar. |
| [ToolBarOptions](arkts-arkui-arkui-advanced-toolbar-toolbaroptions-c.md) | Inherits from Array&lt;[ToolBarOption](arkts-arkui-arkui-advanced-toolbar-toolbaroption-c.md)&gt;. |

### Structs

| Name | Description |
| --- | --- |
| [ToolBar](arkts-arkui-arkui-advanced-toolbar-toolbar-s.md) | The **Toolbar** component is designed to present a set of action options related to the current screen, displayed at the bottom of the screen. It can display up to five child components. If there are six or more child components, the first four are shown directly, and the additional ones are grouped under a **More** item on the rightmost side of the toolbar. |

### Interfaces

| Name | Description |
| --- | --- |
| [ToolBarSymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbar-toolbarsymbolglyphoptions-i.md) | Defines the icon symbol options. |

### Enums

| Name | Description |
| --- | --- |
| [ItemState](arkts-arkui-arkui-advanced-toolbar-itemstate-e.md) | Enumerates toolbar item states. |

## Examples

```TypeScript
### Example 1: Setting Toolbar Items to Different States

This example shows the various display effects when the state property of toolbar items is set to ENABLE, DISABLE, or ACTIVATE.


```

```TypeScript
### Example 2: Customizing the Toolbar Style

This example demonstrates how to customize the toolbar's height, background color, and other styles using ToolBarModifier. This functionality is supported since API version 13.


```

```TypeScript
### Example 3: Implementing Screen Reader Announcement

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the toolbar item. This functionality is supported since API version 18.
```
