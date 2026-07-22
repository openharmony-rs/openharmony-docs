# DragResult

定义拖拽操作的结果及组件的落入选定状态。

**起始版本：** 10

<!--Device-unnamed-declare enum DragResult--><!--Device-unnamed-declare enum DragResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UNKNOWN

```TypeScript
UNKNOWN = -1
```

拖拽结果尚未设置，在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart)，[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter)，[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove)，[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave)，[onDrop](arkts-arkui-commonmethod-c.md#ondrop)中使用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-UNKNOWN = -1--><!--Device-DragResult-UNKNOWN = -1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_SUCCESSFUL

```TypeScript
DRAG_SUCCESSFUL = 0
```

拖拽成功，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-DRAG_SUCCESSFUL = 0--><!--Device-DragResult-DRAG_SUCCESSFUL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_FAILED

```TypeScript
DRAG_FAILED = 1
```

拖拽失败，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-DRAG_FAILED = 1--><!--Device-DragResult-DRAG_FAILED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_CANCELED

```TypeScript
DRAG_CANCELED = 2
```

拖拽取消，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-DRAG_CANCELED = 2--><!--Device-DragResult-DRAG_CANCELED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_ENABLED

```TypeScript
DROP_ENABLED = 3
```

组件允许落入，在[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter)，[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove)，[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-DROP_ENABLED = 3--><!--Device-DragResult-DROP_ENABLED = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_DISABLED

```TypeScript
DROP_DISABLED = 4
```

组件不允许落入，在[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter)，[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove)，[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DragResult-DROP_DISABLED = 4--><!--Device-DragResult-DROP_DISABLED = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

