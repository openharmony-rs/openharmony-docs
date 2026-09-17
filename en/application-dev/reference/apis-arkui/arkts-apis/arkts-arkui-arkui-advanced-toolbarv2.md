# @ohos.arkui.advanced.ToolBarV2

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md) | Declare type ToolBarV2Item |
| [ToolBarV2ItemImage](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimage-c.md) | Declare type ToolBarV2ItemImage |
| [ToolBarV2ItemText](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtext-c.md) | Declare type ToolBarV2ItemText |
| [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md) | Declare ToolBarV2Modifier used in ToolBar |
| [ToolBarV2SymbolGlyph](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyph-c.md) | Defines toolBarV2 symbolGlyph. |

### Structs

| Name | Description |
| --- | --- |
| [ToolBarV2](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2-s.md) | Declare Component ToolBarV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [ToolBarV2ItemImageOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemimageoptions-i.md) | Declare the options of ToolBarV2ItemImage |
| [ToolBarV2ItemOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemoptions-i.md) | Declare the options of ToolBarV2Item |
| [ToolBarV2ItemTextOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemtextoptions-i.md) | Declare the options of ToolBarV2ItemText |
| [ToolBarV2SymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyphoptions-i.md) | Declare the options of ToolBarV2SymbolGlyph |

### Enums

| Name | Description |
| --- | --- |
| [ToolBarV2ItemState](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2itemstate-e.md) | Declare enum ToolBarV2ItemState |

### Types

| Name | Description |
| --- | --- |
| [ToolBarV2ItemAction](arkts-arkui-toolbarv2itemaction-t.md) | Defines the action callback of ToolBarV2Item. |
| [ToolBarV2ItemIconType](arkts-arkui-toolbarv2itemicontype-t.md) | Defines the icon type of ToolBarV2 item. |

## Examples

```TypeScript
### Example 1: Setting Toolbar Items to Different States

This example shows the various display effects when the state property of toolbar items is set to ENABLE, DISABLE, or ACTIVATE.


```

```TypeScript
### Example 2: Customizing the Toolbar Style

This example demonstrates how to customize the toolbar's height, background color, and pressed state effect using ToolBarV2Modifier.


```

```TypeScript
### Example 3: Implementing Screen Reader Announcement

This example customizes the screen reader announcement text by setting the accessibilityText, accessibilityDescription, and accessibilityLevel properties of the toolbar item.
```
