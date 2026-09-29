# ListItemSwipeActionManager

```TypeScript
declare class ListItemSwipeActionManager
```

Implements the swipe action menu manager for list items.

**Since:** 21

<!--Device-unnamed-declare class ListItemSwipeActionManager--><!--Device-unnamed-declare class ListItemSwipeActionManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## collapse

```TypeScript
static collapse(node: FrameNode): void
```

Collapses the swipe action menu for the specified list item.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-ListItemSwipeActionManager-static collapse(node: FrameNode): void--><!--Device-ListItemSwipeActionManager-static collapse(node: FrameNode): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | FrameNode | Yes | **ListItem** node object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | The component type of the node is incorrect. |
| [106203](../errorcode-node.md#106203-passed-node-not-mounted-to-component-tree) | The node not mounted to component tree. |

## expand

```TypeScript
static expand(node: FrameNode, direction: ListItemSwipeActionDirection): void
```

Expands the swipe action menu for the specified list item.

> **NOTE:** 
> 
> - If the **show** parameter of the **cachedCount** attribute of the **List** component is set to **true**,
> **ListItems** that have been preloaded outside the display area of the **List** support expansion. Otherwise,
> nodes outside the display area of the **List** do not support expansion.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-ListItemSwipeActionManager-static expand(node: FrameNode, direction: ListItemSwipeActionDirection): void--><!--Device-ListItemSwipeActionManager-static expand(node: FrameNode, direction: ListItemSwipeActionDirection): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | FrameNode | Yes | **ListItem** node object. |
| direction | [ListItemSwipeActionDirection](arkts-arkui-listitem-comp-listitemswipeactiondirection-e.md) | Yes | Swipe action menu display direction for the **ListItem** component. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100023](../errorcode-node.md#100023-parameter-error) | The component type of the node is incorrect. |
| [106203](../errorcode-node.md#106203-passed-node-not-mounted-to-component-tree) | The node not mounted to component tree. |
