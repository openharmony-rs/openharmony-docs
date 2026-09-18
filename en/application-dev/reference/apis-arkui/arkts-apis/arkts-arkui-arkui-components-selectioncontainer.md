# @ohos.arkui.components.SelectionContainer

## Modules to Import

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | Defines the attributes of SelectionContainer. |
| [SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md) | Defines the controller of the SelectionContainer component. |

### Interfaces

| Name | Description |
| --- | --- |
| [SelectionContainerEditMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainereditmenuoptions-i.md) | Defines custom edit menu options for SelectionContainer. |
| [SelectionContainerInterface](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerinterface-i.md) | Provides a SelectionContainer component interface. |
| [SelectionContainerMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainermenuoptions-i.md) | Defines selection menu options for SelectionContainer. |
| [SelectionContainerOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontaineroptions-i.md) | Describes the initialization options of the SelectionContainer component. |

### Enums

| Name | Description |
| --- | --- |
| [SelectionContainerTextJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainertextjoinstyle-e.md) | Defines text join style for SelectionContainer. |

### Types

| Name | Description |
| --- | --- |
| [OnMenuItemClickWithTextCallback](arkts-arkui-onmenuitemclickwithtextcallback-t.md) | Invoke upon clicking an item, capable of intercepting the default system menu execution behavior. |

### Constants

| Name | Description |
| --- | --- |
| [SelectionContainer](arkts-arkui-arkui-components-selectioncontainer-con.md) | Defines SelectionContainer component. |
| [SelectionContainerInstance](arkts-arkui-arkui-components-selectioncontainer-con.md#selectioncontainerinstance) | Defines SelectionContainer component instance. |

## Examples

```TypeScript
### Example 1: Selecting Text Across Nodes and Copying the Text

This example demonstrates how to select text across multiple Text components, concatenate the selected text, and handle copy callbacks by using [SelectionContainer](#interfaces), copyOption, [textJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md#textjoinstyle), onTextSelectionChange, onWillCopy, and onCopy.

Since API version 26.0.0, the SelectionContainer component and APIs such as copyOption are added.


```

```TypeScript
### Example 2: Binding a Custom Selection Menu

This example demonstrates how to bind a custom menu when selecting text across nodes through bindSelectionMenu.

Since API version 26.0.0, the bindSelectionMenu attribute is added.


```

```TypeScript
### Example 3: Extending Menu Options

This example uses editMenuOptions to remove the translation and search menu items from the system menu and add five custom menu items. It also demonstrates, in the [onMenuItemClick](arkts-arkui-onmenuitemclickwithtextcallback-t.md) callback, the difference between intercepting the system copy operation (returning true) and not intercepting the select-all operation (returning false).

The editMenuOptions attribute is added since API version 26.0.0.


```

```TypeScript
### Example 4: Closing the Selection Menu and Clearing Text Selection Through the Controllers

This example demonstrates how to close the selection menu and clear the text selection by passing [SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md) through [SelectionContainer](#interfaces) and calling closeSelectionMenu and [clearTextSelection](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md#cleartextselection).

Since API version 26.0.0, the [SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md) and [SelectionContainerOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontaineroptions-i.md) APIs are added.
```
