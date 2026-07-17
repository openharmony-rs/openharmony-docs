# NavDestinationTransition

NavDestination自定义动画接口。

**起始版本：** 15

<!--Device-unnamed-declare interface NavDestinationTransition--><!--Device-unnamed-declare interface NavDestinationTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve
```

动画的曲线类型，默认值为[Curve.EaseInOut](../arkts-apis/arkts-arkui-enums-curve-e.md)。

**类型：** Curve

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationTransition-curve?: Curve--><!--Device-NavDestinationTransition-curve?: Curve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

转场动画的延迟。

默认值：0（毫秒）

单位：ms

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationTransition-delay?: number--><!--Device-NavDestinationTransition-delay?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

转场动画的持续时间。

默认值：1000（毫秒）

单位：ms

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationTransition-duration?: number--><!--Device-NavDestinationTransition-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: Callback<void>
```

指定转场动效的闭包函数，系统会根据闭包中对组件UI状态的修改，生成对应的过渡动画。参见[animateTo](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c-sys.md#animatetoimmediately-1)中的event。

**类型：** Callback<void>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationTransition-event: Callback<void>--><!--Device-NavDestinationTransition-event: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: Callback<void>
```

转场动画结束时的回调函数。

**类型：** Callback<void>

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationTransition-onTransitionEnd?: Callback<void>--><!--Device-NavDestinationTransition-onTransitionEnd?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

