# NavigationAnimatedTransition

自定义转场动画协议，开发者需实现该协议来定义Navigation路由跳转的跳转动画。

**起始版本：** 11

<!--Device-unnamed-declare interface NavigationAnimatedTransition--><!--Device-unnamed-declare interface NavigationAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isInteractive

```TypeScript
isInteractive?: boolean
```

本次转场动画是否为可交互转场。

true：本次转场动画是可交互转场；false：本次转场动画不是可交互转场。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAnimatedTransition-isInteractive?: boolean--><!--Device-NavigationAnimatedTransition-isInteractive?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: (success: boolean) => void
```

转场完成回调。

success：转场是否成功。

**类型：** (success: boolean) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAnimatedTransition-onTransitionEnd?: (success: boolean) => void--><!--Device-NavigationAnimatedTransition-onTransitionEnd?: (success: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

动画超时结束时间。

单位：ms。

取值范围：[0, +∞)。

默认值：可交互动画无默认值，不可交互动画默认超时时间为1000ms。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAnimatedTransition-timeout?: number--><!--Device-NavigationAnimatedTransition-timeout?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: (transitionProxy: NavigationTransitionProxy) => void
```

自定义转场动画执行回调。

transitionProxy：自定义转场动画代理对象。

**类型：** (transitionProxy: NavigationTransitionProxy) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAnimatedTransition-transition: (transitionProxy: NavigationTransitionProxy) => void--><!--Device-NavigationAnimatedTransition-transition: (transitionProxy: NavigationTransitionProxy) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

