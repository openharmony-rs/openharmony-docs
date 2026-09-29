# TreeController

```TypeScript
export declare class TreeController
```

Implements a **TreeController** object, which can be bound to a tree view component to control the node information of the component. One **TreeController** object can be bound to only one tree view component.

**Since:** 10

<!--Device-unnamed-export declare class TreeController--><!--Device-unnamed-export declare class TreeController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## addNode

```TypeScript
addNode(nodeParam?: NodeParam): TreeController
```

Adds a child node to the selected node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-addNode(nodeParam?: NodeParam): TreeController--><!--Device-TreeController-addNode(nodeParam?: NodeParam): TreeController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nodeParam | [NodeParam](arkts-arkui-arkui-advanced-treeview-nodeparam-i.md) | No | Node information. |

**Return value:**

| Type | Description |
| --- | --- |
| [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md) | Controller of the **TreeView** component. |

## buildDone

```TypeScript
buildDone(): void
```

Builds a tree view. After a node is added, this API must be called to save the tree information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-buildDone(): void--><!--Device-TreeController-buildDone(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifyNode

```TypeScript
modifyNode(): void
```

Modifies the selected node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-modifyNode(): void--><!--Device-TreeController-modifyNode(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## refreshNode

```TypeScript
refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void
```

Refreshes the tree view. You can call this API to update the information about the current node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void--><!--Device-TreeController-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentId | number | Yes | ID of the parent node.<br>The value must be greater than or equal to -1. |
| parentSubTitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Secondary text of the parent node. |
| currentSubtitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Secondary text of the current node. |

## removeNode

```TypeScript
removeNode(): void
```

Removes the selected node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-removeNode(): void--><!--Device-TreeController-removeNode(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
