# TreeControllerV2

Declare TreeControllerV2

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## addNode

```TypeScript
addNode(nodeParam?: NodeParamV2): TreeControllerV2
```

Initialize the interface of the tree view. This interface is used to generate ListNodeDataSource data. addNode is only designed for initialization. It can only be invoked during initialization. A maximum of 50 directory levels can be added. For details, see the comment description of NodeParam.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nodeParam | [NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md) | No | Configuration information of the newly added node. |

**Return value:**

| Type | Description |
| --- | --- |
| [TreeControllerV2](arkts-arkui-arkui-advanced-treeviewv2-treecontrollerv2-c.md) | ListTreeNode Tree view component proxy class. |

## buildDone

```TypeScript
buildDone(): void
```

After the initialization is complete by calling the addNode interface, call this interface to complete initialization. This interface must be called when you finish initializing the ListTreeViewV2 by addNode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifyNode

```TypeScript
modifyNode(): void
```

Modify the node name. Register an ON_ITEM_MODIFY callback to obtain the ID, parent node ID, and node name of the modified node.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## refreshNode

```TypeScript
refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void
```

This interface is called when a secondaryTitle needs to be updated

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentId | number | Yes | ID of the parent node.<br>Value range:The value must be greater than or equal to -1. |
| parentSubTitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | secondaryTitle of parent node. |
| currentSubtitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | secondaryTitle of current node. |

## removeNode

```TypeScript
removeNode(): void
```

Delete a node. Register an ON_ITEM_DELETE callback through the ListTreeListenerV2 mechanism to obtain the IDs of all deleted nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
