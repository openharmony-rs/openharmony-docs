# SelectionMenu

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## SelectionMenu

```TypeScript
export declare function SelectionMenu(options: SelectionMenuOptions): void
```

Defines a **SelectionMenu** component. When the input parameter is empty, both the component and its content area have a zero size, making the component invisible. For example, when a **SelectionMenu** component activated via right -click is bound to a RichEditor component using bindSelectionMenu, it will not be displayed when the **RichEditor** component receives a right-click event.

**Since:** 11

**Decorator:** @Builder

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | Yes | Configuration options of the **SelectionMenu** component. |
