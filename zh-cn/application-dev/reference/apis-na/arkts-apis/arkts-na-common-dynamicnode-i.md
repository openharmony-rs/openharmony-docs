# DynamicNode

Define DynamicNode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface DynamicNode--><!--Device-unnamed-export declare interface DynamicNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMove

```TypeScript
onMove(handler: OnMoveHandler | undefined): this
```

Set the move action.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicNode-onMove(handler: OnMoveHandler | undefined): this--><!--Device-DynamicNode-onMove(handler: OnMoveHandler | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnMoveHandler](arkts-na-onmovehandler-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onMove

```TypeScript
onMove(handler: OnMoveHandler | undefined, eventHandler: ItemDragEventHandler): this
```

Set the move action.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicNode-onMove(handler: OnMoveHandler | undefined, eventHandler: ItemDragEventHandler): this--><!--Device-DynamicNode-onMove(handler: OnMoveHandler | undefined, eventHandler: ItemDragEventHandler): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnMoveHandler](arkts-na-onmovehandler-t.md) \| undefined | 是 |  |
| eventHandler | [ItemDragEventHandler](arkts-na-common-itemdrageventhandler-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

