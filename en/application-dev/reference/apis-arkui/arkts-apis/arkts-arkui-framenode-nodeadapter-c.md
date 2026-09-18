# NodeAdapter

Provides lazy loading capabilities for FrameNode data, implementing LazyForEach API functionality.

> **NOTE:** 
> 
> Negative input parameters are ignored and trigger no processing.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attachNodeAdapter

```TypeScript
static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean
```

Attaches a FrameNode to a NodeAdapter. Each node can be bound to only one NodeAdapter. Attempts to re-attach to a NodeAdapter that has already been attached to will fail and return **false**.

> **NOTE:** 
> 
> The following components can be bound: **Column**, **Row**, **Stack**, **GridRow**, **Flex**, **Swiper**,
> **RelativeContainer**, **List**, **ListItemGroup**, **WaterFlow**, and **Grid**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adapter | [NodeAdapter](arkts-arkui-framenode-nodeadapter-c.md) | Yes | NodeAdapter class for lazy loading. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode to be attached. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Attachment result. Returns **true** if the attachment is successful; returns **false** otherwise. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **NodeAdapter** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## detachNodeAdapter

```TypeScript
static detachNodeAdapter(node: FrameNode): void
```

Detaches a FrameNode from its NodeAdapter.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode to detach. |

## dispose

```TypeScript
dispose(): void
```

Disposes of this **NodeAdapter** object. Bindings, if any, of the object will be cleared before the object is disposed of.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getAllAvailableItems

```TypeScript
getAllAvailableItems(): Array<FrameNode>
```

Obtains all available items. Available nodes include both currently displayed and preloaded nodes. The number of preloaded nodes can be configured by adjusting the **cachedCount** property of the parent container, following the [usage constraints](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md#constraints) of **LazyForEach**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FrameNode](arkts-arkui-framenode-c.md)&gt; | Array of items in the FrameNode. |

## insertItem

```TypeScript
insertItem(start: number, count: number): void
```

Inserts a specified number of items starting from a specific index.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Starting index of the items to insert.<br>Value range: 0, +∞). |
| count | number | Yes | Number of the items to insert.<br>Value range: [0, +∞). |

## isDisposed

```TypeScript
isDisposed(): boolean
```

Checks whether the NodeAdapter's backend reference has been released. Frontend nodes maintain references to corresponding backend entity nodes. After a node calls the **dispose** API to release this reference, subsequent API calls may cause crashes or return default values. This API facilitates validation of node validity prior to operations, thereby mitigating risks in scenarios where calls after disposal are required.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the reference to the backend node is released. The value **true** means that the reference to backend node is released, and **false** means the opposite. |

**Examples**

```TypeScript
See [NodeAdapter Validity Check Example.
```

## moveItem

```TypeScript
moveItem(from: number, to: number): void
```

Moves items from the starting index to the ending index.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Original index from which the data will be moved.<br>Value range: [0, +∞). |
| to | number | Yes | Target index to which the data will be moved.<br>Value range: [0, +∞). |

## onAttachToNode

```TypeScript
onAttachToNode?(target: FrameNode): void
```

Called when a FrameNode is attached to the NodeAdapter.

> **NOTE:** 
> 
> In versions earlier than API version 26.0.0, this callback is triggered when the host node is attached to the
> main tree. If you set this callback by dynamically assigning a value, you can complete the setting after calling
> [attachNodeAdapter](#attachnodeadapter) and before the host node is attached to the main tree.
> In this case, you will receive this callback when the host node is attached to the main tree.
> 
> In API version 26.0.0 and later, this callback is triggered immediately when the NodeAdapter is bound to the host
> node, instead of when the host node is attached to the main tree. In this case, the host node may not have been
> attached to the main tree. If the node on which the callback logic depends has been mounted (for example,
> accessing layout information or executing animation), you are advised to register
> onAppear in the callback and place the related logic in **onAppear** for
> execution. If you set this callback by dynamically assigning a value, complete the setting before calling
> [attachNodeAdapter](#attachnodeadapter). Otherwise, the callback may fail to be triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode attached to the NodeAdapter. |

## onCreateChild

```TypeScript
onCreateChild?(index: number): FrameNode
```

Called during node initialization or when new child nodes are detected. When adding child components, follow the child component restrictions for declarative components. For example, **WaterFlow** only supports adding **FlowItem** child nodes. The parent node uses the child node's index and key to determine whether the node is being loaded for the first time or a new node is sliding into view.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the loaded node.<br>Value range: [0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | FrameNode created by you. |

## onDetachFromNode

```TypeScript
onDetachFromNode?(): void
```

Called when detachment occurs.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDisposeChild

```TypeScript
onDisposeChild?(id: number, node: FrameNode): void
```

Called when a child node is about to be disposed. Nodes that are neither displayed on the screen nor within the preload range are considered nodes about to be disposed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | ID of the child node to be disposed of. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode to be disposed of. |

## onGetChildId

```TypeScript
onGetChildId?(index: number): number
```

Called during node initialization or when new child nodes are detected. The **index** parameter enables custom ID generation. Ensure that IDs remain unique across different index values.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the loaded node.<br>Value range: [0, +∞). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Custom ID. Make sure the ID is unique. |

## onUpdateChild

```TypeScript
onUpdateChild?(id: number, node: FrameNode): void
```

Called when a loaded node is reused. Node reuse occurs when the key value of a cached node matches that of the node to be reused.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | ID of the node to be reused. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | FrameNode that is reused. |

## reloadAllItems

```TypeScript
reloadAllItems(): void
```

Reloads all items in this node. This API calls the [OnDataReloaded](../arkts-components/arkts-arkui-datachangelistener-i.md#ondatareloaded) API in **LazyForEach** to trigger component data refresh.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reloadItem

```TypeScript
reloadItem(start: number, count: number): void
```

Reloads a specified number of items starting from a specific index.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Starting index of the items to reload.<br>Value range: 0, +∞). |
| count | number | Yes | Number of the items to reload.<br>Value range: [0, +∞). |

## removeItem

```TypeScript
removeItem(start: number, count: number): void
```

Removes a specified number of items starting from a specific index.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Starting index of the items to remove.<br>Value range: [0, +∞). |
| count | number | Yes | Number of the items to remove.<br>Value range: [0, +∞). |

## totalNodeCount

```TypeScript
set totalNodeCount(count: number)
```

Sets the total number of items in this node.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

```TypeScript
get totalNodeCount(): number
```

Get the total number of node count.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See the example for [NodeAdapter Usage Example.
```
