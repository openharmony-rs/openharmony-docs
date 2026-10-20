# SegmentButtonInteractionMode

```TypeScript
declare enum SegmentButtonInteractionMode
```

定义分段按钮的拖拽交互模式。

**起始版本：** 26.2.0

<!--Device-unnamed-declare enum SegmentButtonInteractionMode--><!--Device-unnamed-declare enum SegmentButtonInteractionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOLLOWING_DRAG

```TypeScript
FOLLOWING_DRAG = 0
```

启用跟手拖拽。非系统材质场景仅启用跟手拖拽动画。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButtonInteractionMode-FOLLOWING_DRAG = 0--><!--Device-SegmentButtonInteractionMode-FOLLOWING_DRAG = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NORMAL_DRAG

```TypeScript
NORMAL_DRAG = 1
```

启用普通拖拽。仅改变拖拽位移和选中更新方式；系统材质的外观、形变及已配置光效保持原有行为。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SegmentButtonInteractionMode-NORMAL_DRAG = 1--><!--Device-SegmentButtonInteractionMode-NORMAL_DRAG = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
