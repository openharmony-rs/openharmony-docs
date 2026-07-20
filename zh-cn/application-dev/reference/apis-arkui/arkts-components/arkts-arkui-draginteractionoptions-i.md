# DragInteractionOptions

设置拖拽过程中预览图浮起的交互模式。

**起始版本：** 12

<!--Device-unnamed-declare interface DragInteractionOptions--><!--Device-unnamed-declare interface DragInteractionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultAnimationBeforeLifting

```TypeScript
defaultAnimationBeforeLifting?: boolean
```

表示是否启用长按浮起阶段组件自身的默认点按效果（缩小）。true表示启用默认点按效果，false表示不启用默认点按效果。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInteractionOptions-defaultAnimationBeforeLifting?: boolean--><!--Device-DragInteractionOptions-defaultAnimationBeforeLifting?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableEdgeAutoScroll

```TypeScript
enableEdgeAutoScroll?: boolean
```

设置在拖拽至可滚动组件边缘时是否触发自动滚屏。true表示触发自动滚屏，false表示不触发自动滚屏。

默认值：true

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DragInteractionOptions-enableEdgeAutoScroll?: boolean--><!--Device-DragInteractionOptions-enableEdgeAutoScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

表示拖拽时是否启用震动。true表示启用震动，false表示不启用震动。仅在存在蒙层的预览（通过[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)）场景生效。

**注意：** 仅当应用具备 ohos.permission.VIBRATE 权限，且用户启用了触感反馈时才会生效。

默认值：false

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DragInteractionOptions-enableHapticFeedback?: boolean--><!--Device-DragInteractionOptions-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isLiftingDisabled

```TypeScript
isLiftingDisabled?: boolean
```

表示长按拖拽时，是否禁用浮起效果。true表示禁用浮起效果，false表示不禁用浮起效果。

如果设置为true，当组件支持拖拽并同时设置[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)时，仅弹出配置的自定义菜单预览。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DragInteractionOptions-isLiftingDisabled?: boolean--><!--Device-DragInteractionOptions-isLiftingDisabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isMultiSelectionEnabled

```TypeScript
isMultiSelectionEnabled?: boolean
```

表示拖拽过程中背板图是否支持多选聚拢效果。true表示支持多选聚拢效果，false表示不支持多选聚拢效果。该参数只在[Grid](./grid)和[List](./list)组件中的[GridItem](./gridItem)组件和[ListItem](./list_item)组件生效。

当一个item组件设置为多选拖拽时，该组件的子组件不可拖拽。聚拢组件预览图设置的优先级为[dragPreview](arkts-arkui-commonmethod-c.md#dragpreview-1)中的string，dragPreview中的PixelMap，组件自截图，不支持dragPreview中的Builder形式。

不支持组件绑定[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu-1)中参数存在isShown的模式。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragInteractionOptions-isMultiSelectionEnabled?: boolean--><!--Device-DragInteractionOptions-isMultiSelectionEnabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

