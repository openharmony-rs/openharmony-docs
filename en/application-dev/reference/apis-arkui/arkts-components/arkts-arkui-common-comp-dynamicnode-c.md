# DynamicNode

```TypeScript
declare class DynamicNode<T>
```

Define DynamicNode.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>): T
```

Invoked when data is moved during drag and drop sorting. This callback is only applicable in a List component. where each ForEach iteration generates a ListItem component. It allows you to define custom drag actions and handle various drag events.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnMoveHandler](arkts-arkui-common-comp-onmovehandler-t.md)&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="onmove-1"></a>

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T
```

Set the move action.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnMoveHandler](arkts-arkui-common-comp-onmovehandler-t.md)&gt; | Yes |  |
| eventHandler | [ItemDragEventHandler](arkts-arkui-common-comp-itemdrageventhandler-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |
