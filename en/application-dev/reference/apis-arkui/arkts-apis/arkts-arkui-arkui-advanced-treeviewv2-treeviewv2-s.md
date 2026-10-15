# TreeViewV2

```TypeScript
export declare struct TreeViewV2
```

The **TreeViewV2** component is displayed as a list in a hierarchical manner, which is suitable for displaying nested structures. It has parent nodes and child nodes, can be expanded or collapsed, and supports node addition, deletion, modification, drag-and-drop movement, custom icons, event listening, and context menus.

It is used in productivity apps, such as the side navigation bars in memos, emails, and galleries. It is suitable for scenarios that require displaying and managing hierarchical data and supporting node interaction operations.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the tree view through this component, achieving more efficient UI refresh.

> **NOTE:** 
> 
> - This module's APIs can only be used in the stage model.
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) are set for **TreeViewV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **TreeViewV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **TreeViewV2**.

**Since:** 26.0.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct TreeViewV2--><!--Device-unnamed-export declare struct TreeViewV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## treeControllerV2

```TypeScript
treeControllerV2: TreeControllerV2
```

Controller of the tree view nodes, used to control the node information of the tree. After being bound to the tree view component, it can be used to add, delete, and modify nodes. The same controller cannot control multiple tree view components.

**Type:** [TreeControllerV2](arkts-arkui-arkui-advanced-treeviewv2-treecontrollerv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeViewV2-treeControllerV2: TreeControllerV2--><!--Device-TreeViewV2-treeControllerV2: TreeControllerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
