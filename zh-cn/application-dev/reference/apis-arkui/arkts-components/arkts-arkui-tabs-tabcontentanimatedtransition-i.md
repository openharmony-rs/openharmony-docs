# TabContentAnimatedTransition

Tabs自定义切换动画相关信息。

**起始版本：** 11

<!--Device-unnamed-declare interface TabContentAnimatedTransition--><!--Device-unnamed-declare interface TabContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Tabs自定义切换动画超时时间。从自定义动画开始切换计时，如果到达该时间后，开发者仍未调用[TabContentTransitionProxy](arkts-arkui-tabs-tabcontenttransitionproxy-i.md)的finishTransition接口通知Tabs组件自定义动画结束，那么组件就会认为此次自定义动画已结束，直接执行后续操作。

默认值：1000

单位：ms

取值范围：[0, +∞)。

**类型：** number

**默认值：** 1000 ms

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TabContentAnimatedTransition-timeout?: number--><!--Device-TabContentAnimatedTransition-timeout?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<TabContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback<TabContentTransitionProxy>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>--><!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

