# SelectionMenu

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## SelectionMenu

```TypeScript
export declare function SelectionMenu(options: SelectionMenuOptions): void
```

When the input parameter is empty, both the content area and the component size of the **SelectionMenu** component are zero. For example, if the [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md) component uses the [bindSelectionMenu](../arkts-components/arkts-arkui-richeditor-comp-attribute.md#bindselectionmenu) API to bind a right-click menu of **SelectionMenu**, no menu will pop up when right-clicking the rich text component area.

**Since:** 11

**Decorator:** @Builder

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-export declare function SelectionMenu(options: SelectionMenuOptions): void--><!--Device-unnamed-export declare function SelectionMenu(options: SelectionMenuOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | Yes | Configuration options for the text selection menu, used to configure the edit menu, extended dropdown menu, rich text controller, and callback events such as copy, paste, and cut. |
