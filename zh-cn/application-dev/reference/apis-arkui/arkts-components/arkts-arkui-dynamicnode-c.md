# DynamicNode

Define DynamicNode.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class DynamicNode<T>--><!--Device-unnamed-declare class DynamicNode<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>): T
```

拖拽排序数据移动回调。当父容器组件为[List]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或[Grid]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，并且ForEach/LazyForEach/Repeat每次迭代都生成一个ListItem或GridItem组 件时才生效。调用后开启拖拽排序功能；拖拽排序离手后，如果数据位置发生变化，将触发handler回调，上报数据移动起始索引号和目标索引号。需要在回调中修改数据源，并确保数据仅顺序发生变化，才能正常执行落位动画。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;OnMoveHandler&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T
```

拖拽排序数据移动回调。当父容器组件为[List]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或[Grid]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_，并且ForEach/LazyForEach/Repeat每次迭代都生成一个ListItem或GridItem组 件时才生效。调用后开启拖拽排序功能；拖拽排序离手后，如果数据位置发生变化，将触发handler回调，上报数据移动起始索引号和目标索引号。需要在回调中修改数据源，并确保数据仅顺序发生变化，才能正常执行落位动画。与 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_相比，新增eventHandler参 数，可监听长按、开始拖拽、经过其他组件、拖拽结束等拖拽阶段事件。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;OnMoveHandler&gt; | 是 |  |
| eventHandler | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

