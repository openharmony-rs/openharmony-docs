# ItemDragEventHandler

Define item drag event handler.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ItemDragEventHandler--><!--Device-unnamed-export declare interface ItemDragEventHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDragStart

```TypeScript
onDragStart?: Callback<int>
```

This callback is triggered when the item is dragged.

**类型：** [Callback](arkts-na-callback-t.md)&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ItemDragEventHandler-onDragStart?: Callback<int>--><!--Device-ItemDragEventHandler-onDragStart?: Callback<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDrop

```TypeScript
onDrop?: Callback<int>
```

This callback is triggered when the item is dropped.

**类型：** [Callback](arkts-na-callback-t.md)&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ItemDragEventHandler-onDrop?: Callback<int>--><!--Device-ItemDragEventHandler-onDrop?: Callback<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<int>
```

This callback is triggered when the item is long pressed.

**类型：** [Callback](arkts-na-callback-t.md)&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ItemDragEventHandler-onLongPress?: Callback<int>--><!--Device-ItemDragEventHandler-onLongPress?: Callback<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMoveThrough

```TypeScript
onMoveThrough?: OnMoveHandler
```

This callback is triggered when an item is moved through other items.

**类型：** [OnMoveHandler](arkts-na-onmovehandler-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler--><!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

