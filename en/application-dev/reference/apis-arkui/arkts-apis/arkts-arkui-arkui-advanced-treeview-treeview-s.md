# TreeView

```TypeScript
export declare struct TreeView
```

A tree view is a hierarchical list suitable for displaying nested structures. It consists of parent nodes and child nodes, and supports expanding or collapsing.

The tree view is applicable in the side navigation bar of productivity apps, such as notepad, email, and Gallery.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **TreeView** component has [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **TreeView** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **TreeView** component.

**Since:** 10

**Decorator:** @Component

<!--Device-unnamed-export declare struct TreeView--><!--Device-unnamed-export declare struct TreeView-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## treeController

```TypeScript
treeController: TreeController
```

Controller of the tree view component, used to control the node information of the tree.

**Type:** [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeView-treeController: TreeController--><!--Device-TreeView-treeController: TreeController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
