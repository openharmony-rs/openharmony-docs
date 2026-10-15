# TreeController

```TypeScript
export declare class TreeController
```

A controller for the tree view component, used to control node information of the tree. The same controller instance cannot control multiple tree view components simultaneously.

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

After a node is selected, call this method to add a child node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-addNode(nodeParam?: NodeParam): TreeController--><!--Device-TreeController-addNode(nodeParam?: NodeParam): TreeController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nodeParam | [NodeParam](arkts-arkui-arkui-advanced-treeview-nodeparam-i.md) | No | Node information. If this parameter is not passed, a node titled **New Folder** will be added under the currently selected node. |

**Return value:**

| Type | Description |
| --- | --- |
| [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md) | Returns the controller instance of the tree view component, supporting chain calls. |

## buildDone

```TypeScript
buildDone(): void
```

Saves the tree information after all nodes are added.

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

Updates the display information of the current node by specifying the parent node ID, parent node subtitle, and current node subtitle.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void--><!--Device-TreeController-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentId | number | Yes | Parent node ID.<br>The value range is greater than or equal to -1. The root node ID is -1. If the value is set to less than -1, it does not take effect. |
| parentSubTitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Subtitle of the parent node. After setting, the subtitle display content of the parent node is updated. |
| currentSubtitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Subtitle of the current node. After setting, the subtitle display content of the current node is updated. |

## removeNode

```TypeScript
removeNode(): void
```

Deletes the selected node.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeController-removeNode(): void--><!--Device-TreeController-removeNode(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
