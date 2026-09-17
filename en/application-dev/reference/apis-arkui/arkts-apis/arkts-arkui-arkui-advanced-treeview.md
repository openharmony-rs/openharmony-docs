# @ohos.arkui.advanced.TreeView

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md) | Implements a **TreeController** object, which can be bound to a tree view component to control the node information of the component. One **TreeController** object can be bound to only one tree view component. |
| [TreeListener](arkts-arkui-arkui-advanced-treeview-treelistener-c.md) | Listener of the tree view component. You can bind it to the **TreeView** component and use it to listen for changes of tree nodes. One listener can be bound to only one **TreeView** component. |
| [TreeListenerManager](arkts-arkui-arkui-advanced-treeview-treelistenermanager-c.md) | Implements a **TreeListenerManager** object, which can be bound to a **TreeView** component to listen for changes of tree nodes. One **TreeListenerManager** object can be bound to only one tree view component. |

### Structs

| Name | Description |
| --- | --- |
| [TreeView](arkts-arkui-arkui-advanced-treeview-treeview-s.md) | The **TreeView** component represents a tree view used to display a hierarchical list of items. Each item can contain subitems, which may be expanded or collapsed. |

### Interfaces

| Name | Description |
| --- | --- |
| [CallbackParam](arkts-arkui-arkui-advanced-treeview-callbackparam-i.md) | Declare CallbackParam |
| [NodeParam](arkts-arkui-arkui-advanced-treeview-nodeparam-i.md) | Declare NodeParam |

### Enums

| Name | Description |
| --- | --- |
| [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | Enumerates the listening types of tree view nodes. |

## Examples

```TypeScript
### Example 1: Configuring a Simple Tree View

This example showcases how to use TreeController to perform operations on tree nodes, such as adding, deleting, and renaming. It also demonstrates the effects of adding nodes with different parameters.


```

```TypeScript
### Example 2: Setting the Symbol Icon

This example demonstrates how to use symbolIconStyle, symbolEditIconStyle, and symbolSelectedIconStyle in NodeParam to set custom symbol icons. This functionality is supported since API version 18.
```
