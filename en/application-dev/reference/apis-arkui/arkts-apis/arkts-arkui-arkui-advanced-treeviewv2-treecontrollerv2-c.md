# TreeControllerV2

```TypeScript
export declare class TreeControllerV2
```

Controller of the tree view component, used to control the node information of the tree. Bind this object to the tree view component before use. The same controller cannot control multiple tree view components.

**Since:** 26.0.0

<!--Device-unnamed-export declare class TreeControllerV2--><!--Device-unnamed-export declare class TreeControllerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## addNode

```TypeScript
addNode(nodeParam?: NodeParamV2): TreeControllerV2
```

Adds a child node to the tapped node. After the node is added, you must call [buildDone()](#builddone) to trigger the saving of tree information; otherwise, the added node will not be displayed in the tree view. Chained calls are supported, for example, **addNode().addNode().buildDone()**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeControllerV2-addNode(nodeParam?: NodeParamV2): TreeControllerV2--><!--Device-TreeControllerV2-addNode(nodeParam?: NodeParamV2): TreeControllerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nodeParam | [NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md) | No | Node information, used to specify the attributes of the node to be added. If this parameter is not passed, a node titled "New Folder" is added under the currently selected node. |

**Return value:**

| Type | Description |
| --- | --- |
| [TreeControllerV2](arkts-arkui-arkui-advanced-treeviewv2-treecontrollerv2-c.md) | Controller of the tree view component, used to chain other tree view control methods. |

## buildDone

```TypeScript
buildDone(): void
```

Builds the tree view. After all nodes are added, this method must be called to trigger the saving of tree information. This API uses a two-phase build mode: first add nodes to the memory through **addNode**, and then call this method to save the node information in a unified manner and render it into the tree view. If this method is not called, the added nodes will not be displayed in the tree view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeControllerV2-buildDone(): void--><!--Device-TreeControllerV2-buildDone(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifyNode

```TypeScript
modifyNode(): void
```

Modifies the tapped node.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeControllerV2-modifyNode(): void--><!--Device-TreeControllerV2-modifyNode(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## refreshNode

```TypeScript
refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void
```

Locates the parent node based on the passed **parentId**, and updates the subtitle of the parent node (**parentSubTitle**) and the subtitle of the current node (**currentSubtitle**).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeControllerV2-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void--><!--Device-TreeControllerV2-refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentId | number | Yes | ID of the parent node.<br>Value range: greater than or equal to -1.<br>If a value less than -1 is passed, the node is invalid. |
| parentSubTitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Subtitle of the parent node, used to update the subtitle displayed on the parent node. |
| currentSubtitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Subtitle of the current node, used to update the subtitle displayed on the current node. |

## removeNode

```TypeScript
removeNode(): void
```

Deletes the tapped node.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeControllerV2-removeNode(): void--><!--Device-TreeControllerV2-removeNode(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
