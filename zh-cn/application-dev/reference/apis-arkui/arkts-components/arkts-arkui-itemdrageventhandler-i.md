# ItemDragEventHandler

定义拖拽事件

**起始版本：** 20

<!--Device-unnamed-declare interface ItemDragEventHandler--><!--Device-unnamed-declare interface ItemDragEventHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDragStart

```TypeScript
onDragStart?: Callback<number>
```

当项目被拖动时，会触发此回调。

**类型：** Callback&lt;number&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ItemDragEventHandler-onDragStart?: Callback<number>--><!--Device-ItemDragEventHandler-onDragStart?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDrop

```TypeScript
onDrop?: Callback<number>
```

当项目被释放时，会触发此回调。

**类型：** Callback&lt;number&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ItemDragEventHandler-onDrop?: Callback<number>--><!--Device-ItemDragEventHandler-onDrop?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLongPress

```TypeScript
onLongPress?: Callback<number>
```

当项目被长按时触发此回调。

**类型：** Callback&lt;number&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ItemDragEventHandler-onLongPress?: Callback<number>--><!--Device-ItemDragEventHandler-onLongPress?: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMoveThrough

```TypeScript
onMoveThrough?: OnMoveHandler
```

当项目通过其他项目移动时，会触发此回调。

**类型：** OnMoveHandler

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler--><!--Device-ItemDragEventHandler-onMoveThrough?: OnMoveHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

