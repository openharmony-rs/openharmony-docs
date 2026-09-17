# TreeView

The **TreeView** component represents a tree view used to display a hierarchical list of items. Each item can contain subitems, which may be expanded or collapsed.

This component is applicable in productivity applications, such as side navigation bars in notepad, email, and Gallery applications.

> **NOTE:** 
> 
> - If the **TreeView** component has universal attributes and universal events configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **TreeView** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **TreeView** component.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## treeController

```TypeScript
treeController: TreeController
```

Node information of the tree view.

**Type:** [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
