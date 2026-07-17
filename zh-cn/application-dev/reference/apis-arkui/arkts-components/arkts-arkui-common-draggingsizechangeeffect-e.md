# DraggingSizeChangeEffect

当一个节点上同时设置长按浮起预览（参考bindContextMenu）与拖拽时，使用该字段设置长按浮起预览图与拖拽预览图过渡动效方式。

**起始版本：** 19

<!--Device-unnamed-declare enum DraggingSizeChangeEffect--><!--Device-unnamed-declare enum DraggingSizeChangeEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

发起拖拽时直接从菜单预览图切换为最终尺寸的拖拽预览图。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DraggingSizeChangeEffect-DEFAULT = 0--><!--Device-DraggingSizeChangeEffect-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIZE_TRANSITION

```TypeScript
SIZE_TRANSITION = 1
```

发起拖拽时，由菜单预览图直接切换为拖拽预览图，尺寸逐步从菜单预览图尺寸过渡到最终预览图尺寸，设置了DragPreviewMode中的DISABLE_SCALE枚举值时尺寸过渡不生效。这在长按浮起预览图与拖拽预览图相同时使用。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DraggingSizeChangeEffect-SIZE_TRANSITION = 1--><!--Device-DraggingSizeChangeEffect-SIZE_TRANSITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SIZE_CONTENT_TRANSITION

```TypeScript
SIZE_CONTENT_TRANSITION = 2
```

发起拖拽时，由菜单预览图逐步过渡切换为最终拖拽预览图，设置DragPreviewMode中的DISABLE_SCALE时尺寸过渡不生效。这常用于菜单预览图与拖拽预览图差异较大时使用，过渡效果包含内容透明度及尺寸变化。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DraggingSizeChangeEffect-SIZE_CONTENT_TRANSITION = 2--><!--Device-DraggingSizeChangeEffect-SIZE_CONTENT_TRANSITION = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

