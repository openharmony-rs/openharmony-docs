# ContextMenuAnimationOptions

长按预览时显示的样式信息。

**起始版本：** 11

<!--Device-unnamed-interface ContextMenuAnimationOptions--><!--Device-unnamed-interface ContextMenuAnimationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverScale

```TypeScript
hoverScale?: AnimationRange<number>
```

在自定义预览图（preview为CustomBuilder类型）以及长按弹出（responseType指定为LongPress）菜单的场景下，hoverScale用于为绑定组件的截图浮起动画设置两个参数：相对于预览原图的起始与结束缩放比例。hoverScale设置后，浮起动画和预览图之间会有切换过渡动效。

**说明：**

倍率设置参数小于等于0时，不生效。

[bindContextMenu<sup>12+</sup>](arkts-arkui-commonmethod-c.md#bindcontextmenu)场景下，不生效。

设置transition接口时，不生效。

使用此接口且同时使用scale接口时，scale接口起始值不生效。

为保障最佳体验，最终预览图尺寸不建议小于原组件截图尺寸。当前预览动效宽高会受组件截图和自定义预览大小影响，请根据实际使用情况自行保障展示效果。

**类型：** AnimationRange&lt;number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuAnimationOptions-hoverScale?: AnimationRange<number>--><!--Device-ContextMenuAnimationOptions-hoverScale?: AnimationRange<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverScaleInterruption

```TypeScript
hoverScaleInterruption?: boolean
```

在自定义预览图（preview为CustomBuilder类型）以及长按弹出（responseType指定为LongPress）菜单的场景下，且hoverScaleInterruption为true时，在触发拖拽效果前抬起手是否允许取消预览菜单弹出。true表示允许取消预览菜单弹出，false表示不允许取消预览菜单弹出。

默认值：false

**说明：**

未设置hoverScale接口或设置了transition接口时，该参数不生效。长按时长不足以触发拖拽效果时抬起手，预览菜单hoverScale效果回退，预览菜单不弹出，并可触发原组件上绑定的click等手势事件。长按时长足以触发拖拽效果后抬起手，预览菜单正常弹出，并不再触发原组件上绑定的click等手势事件。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuAnimationOptions-hoverScaleInterruption?: boolean--><!--Device-ContextMenuAnimationOptions-hoverScaleInterruption?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: AnimationRange<number>
```

动画开始和结束时相对预览原图缩放比例。

默认值：[0.95, 1.1]

**说明：**

缩放比例需要根据实际开发场景设置，建议设置值为小于预览图宽度或布局的最大限制。

**类型：** AnimationRange&lt;number&gt;

**默认值：** [0.95, 1.1] [since 11 - 11]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuAnimationOptions-scale?: AnimationRange<number>--><!--Device-ContextMenuAnimationOptions-scale?: AnimationRange<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

设置菜单显示和退出的过渡效果。

**说明：**

在菜单退出动效过程中，横竖屏切换时，菜单会避让。二级菜单不继承自定义动效。弹出过程中可以点击二级菜单，但在退出动效执行过程中不允许点击二级菜单。

详细描述见[TransitionEffect](arkts-arkui-transitioneffect-c.md)对象说明。

**类型：** TransitionEffect

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenuAnimationOptions-transition?: TransitionEffect--><!--Device-ContextMenuAnimationOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

