# DynamicNode

Define DynamicNode.

**起始版本：** 12

<!--Device-unnamed-declare class DynamicNode<T>--><!--Device-unnamed-declare class DynamicNode<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onmove"></a>
## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>): T
```

Set the move action.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-optional-t.md)&lt;OnMoveHandler&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onmove-1"></a>
## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T
```

设置移动动作

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-optional-t.md)&lt;OnMoveHandler&gt; | 是 |  |
| eventHandler | [ItemDragEventHandler](arkts-arkui-itemdrageventhandler-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

