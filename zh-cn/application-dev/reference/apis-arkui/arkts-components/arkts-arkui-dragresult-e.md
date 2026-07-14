# DragResult

定义拖拽操作的结果及组件的落入选定状态。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UNKNOWN

```TypeScript
UNKNOWN = -1
```

拖拽结果尚未设置，在[onDragStart](arkts-arkui-commonmethod-c.md#ondragstart-1)，[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter-1)，
[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove-1)，[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave-1)，
[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)中使用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_SUCCESSFUL

```TypeScript
DRAG_SUCCESSFUL = 0
```

拖拽成功，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_FAILED

```TypeScript
DRAG_FAILED = 1
```

拖拽失败，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_CANCELED

```TypeScript
DRAG_CANCELED = 2
```

拖拽取消，在[onDrop](arkts-arkui-commonmethod-c.md#ondrop-1)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_ENABLED

```TypeScript
DROP_ENABLED = 3
```

组件允许落入，在[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter-1)，[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove-1)，
[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave-1)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_DISABLED

```TypeScript
DROP_DISABLED = 4
```

组件不允许落入，在[onDragEnter](arkts-arkui-commonmethod-c.md#ondragenter-1)，[onDragMove](arkts-arkui-commonmethod-c.md#ondragmove-1)，
[onDragLeave](arkts-arkui-commonmethod-c.md#ondragleave-1)中使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

