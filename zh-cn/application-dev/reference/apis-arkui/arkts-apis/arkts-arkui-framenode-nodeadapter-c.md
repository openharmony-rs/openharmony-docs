# NodeAdapter

NodeAdapter提供FrameNode的数据懒加载能力，通过[LazyForEach](../arkts-components/arkts-arkui-lazyforeach.md)实现接口功能。
> **说明：**  
>  
> 入参不能为负数，入参为负数时不做处理。

**起始版本：** 12

<!--Device-unnamed-declare class NodeAdapter--><!--Device-unnamed-declare class NodeAdapter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attachNodeAdapter

```TypeScript
static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean
```

给FrameNode绑定一个NodeAdapter。一个节点只能绑定一个NodeAdapter。已经绑定NodeAdapter的再次绑定会失败并返回false。
> **说明：**  
>  
> 支持绑定的组件：Column、Row、Stack、GridRow、Flex、Swiper、RelativeContainer、List、ListItemGroup、WaterFlow、Grid。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean--><!--Device-NodeAdapter-static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adapter | [NodeAdapter](arkts-arkui-framenode-nodeadapter-c.md) | 是 | 定义懒加载的NodeAdapter类。 |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 绑定的FrameNode节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 绑定结果，返回true绑定成功，false绑定失败。 |

## constructor

```TypeScript
constructor()
```

NodeAdapter的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-constructor()--><!--Device-NodeAdapter-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## detachNodeAdapter

```TypeScript
static detachNodeAdapter(node: FrameNode): void
```

解除绑定操作，解除FrameNode节点绑定的NodeAdapter。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-static detachNodeAdapter(node: FrameNode): void--><!--Device-NodeAdapter-static detachNodeAdapter(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 要解除绑定的FrameNode节点。 |

## dispose

```TypeScript
dispose(): void
```

立即释放当前的NodeAdapter。如果是已绑定的状态，会先进行解绑操作，再释放当前的NodeAdapter。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-dispose(): void--><!--Device-NodeAdapter-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getAllAvailableItems

```TypeScript
getAllAvailableItems(): Array<FrameNode>
```

获取所有有效数据。有效节点数据包括显示在屏幕上的节点以及预加载的节点。其中预加载节点的数量可依照LazyForEach的[使用限制](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md#使用限制)，调整父容器的cachedCount属性进行设置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-getAllAvailableItems(): Array<FrameNode>--><!--Device-NodeAdapter-getAllAvailableItems(): Array<FrameNode>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;FrameNode&gt; | FrameNode数据节点集合。 |

## insertItem

```TypeScript
insertItem(start: number, count: number): void
```

从索引值开始新增指定数量的节点数据。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-insertItem(start: number, count: number): void--><!--Device-NodeAdapter-insertItem(start: number, count: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 新增的节点开始索引值。<br/>取值范围：[0, +∞) |
| count | number | 是 | 新增数据节点的数量。<br/>取值范围：[0, +∞) |

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前FrameNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-isDisposed(): boolean--><!--Device-NodeAdapter-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

## moveItem

```TypeScript
moveItem(from: number, to: number): void
```

将数据从原始索引移动到目的索引。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-moveItem(from: number, to: number): void--><!--Device-NodeAdapter-moveItem(from: number, to: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | 数据移动的原始索引值。<br/>取值范围：[0, +∞) |
| to | number | 是 | 数据移动的目的索引值。<br/>取值范围：[0, +∞) |

## onAttachToNode

```TypeScript
onAttachToNode?(target: FrameNode): void
```

FrameNode绑定NodeAdapter时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onAttachToNode?(target: FrameNode): void--><!--Device-NodeAdapter-onAttachToNode?(target: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 绑定NodeAdapter的FrameNode节点。 |

## onCreateChild

```TypeScript
onCreateChild?(index: number): FrameNode
```

节点首次加载或新节点滑入时回调。建议开发者在添加子组件时，遵循声明式组件中子组件的约束。例如，WaterFlow支持添加FlowItem子节点。父节点根据子节点的索引与key值判断是否触发了节点首次加载或新节点滑入。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onCreateChild?(index: number): FrameNode--><!--Device-NodeAdapter-onCreateChild?(index: number): FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 加载节点索引值。<br/>取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | 返回开发者创建的FrameNode节点。 |

## onDetachFromNode

```TypeScript
onDetachFromNode?(): void
```

解除绑定时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onDetachFromNode?(): void--><!--Device-NodeAdapter-onDetachFromNode?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisposeChild

```TypeScript
onDisposeChild?(id: number, node: FrameNode): void
```

子节点即将销毁时回调。既不显示在屏幕上，也不处于预加载范围内的节点都属于即将销毁的节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onDisposeChild?(id: number, node: FrameNode): void--><!--Device-NodeAdapter-onDisposeChild?(id: number, node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 即将销毁的子节点id。 |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 即将销毁的FrameNode节点。 |

## onGetChildId

```TypeScript
onGetChildId?(index: number): number
```

节点首次加载或新节点滑入时回调。传入的index参数用于自定义生成Id，需要开发者自行保证根据不同index生成Id的唯一性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onGetChildId?(index: number): number--><!--Device-NodeAdapter-onGetChildId?(index: number): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 加载节点索引值。<br/>取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回开发者自定义生成的Id，需要开发者自行保证Id的唯一性。 |

## onUpdateChild

```TypeScript
onUpdateChild?(id: number, node: FrameNode): void
```

重新加载的数据节点被复用时回调。已缓存节点的key值与被复用节点一致时进行节点复用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-onUpdateChild?(id: number, node: FrameNode): void--><!--Device-NodeAdapter-onUpdateChild?(id: number, node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 复用节点的id。 |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 被复用的FrameNode节点。 |

## reloadAllItems

```TypeScript
reloadAllItems(): void
```

重新加载全部数据操作。实际调用了LazyForEach中的[OnDataReloaded](../arkts-components/arkts-arkui-datachangelistener-i.md#ondatareloaded)接口通知组件重新加载所有数据。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-reloadAllItems(): void--><!--Device-NodeAdapter-reloadAllItems(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reloadItem

```TypeScript
reloadItem(start: number, count: number): void
```

从索引值开始重新加载指定数量的节点数据。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-reloadItem(start: number, count: number): void--><!--Device-NodeAdapter-reloadItem(start: number, count: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 重新加载的节点开始索引值。<br/>取值范围：[0, +∞) |
| count | number | 是 | 重新加载数据节点的数量。<br/>取值范围：[0, +∞) |

## removeItem

```TypeScript
removeItem(start: number, count: number): void
```

从索引值开始删除指定数量的节点数据。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-removeItem(start: number, count: number): void--><!--Device-NodeAdapter-removeItem(start: number, count: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 删除的节点开始索引值。<br/>取值范围：[0, +∞) |
| count | number | 是 | 删除数据节点的数量。<br/>取值范围：[0, +∞) |

## totalNodeCount

```TypeScript
get totalNodeCount(): number
```

Get the total number of node count.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeAdapter-get totalNodeCount(): number--><!--Device-NodeAdapter-get totalNodeCount(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

