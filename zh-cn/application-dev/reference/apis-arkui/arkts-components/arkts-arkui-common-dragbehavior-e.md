# DragBehavior

当设置[DragResult](arkts-arkui-common-dragresult-e.md)为DROP_ENABLED后，可设置DragBehavior为复制（COPY）或剪切（MOVE）。当DragBehavior为复制（COPY）时，拖拽对象的角标会显示加号；为剪切（MOVE）时，拖拽对象的角标不会显示加号。DragBehavior用来向开发者描述数据的处理方式是复制（COPY）还是剪切（MOVE），但无法最终决定对数据的实际处理方式。DragBehavior会通过onDragEnd带回给数据拖出方，发起拖拽的一方可通过DragBehavior来区分做出的是复制（COPY）还是剪切（MOVE）数据的不同行为。

**起始版本：** 10

<!--Device-unnamed-declare enum DragBehavior--><!--Device-unnamed-declare enum DragBehavior-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
COPY = 0
```

指定对数据的处理方式为复制。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragBehavior-COPY = 0--><!--Device-DragBehavior-COPY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MOVE

```TypeScript
MOVE = 1
```

指定对数据的处理方式为剪切。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragBehavior-MOVE = 1--><!--Device-DragBehavior-MOVE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

