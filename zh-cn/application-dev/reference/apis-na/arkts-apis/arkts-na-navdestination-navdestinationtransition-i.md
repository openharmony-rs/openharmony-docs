# NavDestinationTransition

NavDestination自定义动画接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavDestinationTransition--><!--Device-unnamed-export declare interface NavDestinationTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve
```

动画的曲线类型，默认值为[Curve.EaseInOut](../../apis-arkui/arkts-apis/arkts-arkui-curve-e.md)。

**类型：** [Curve](../../apis-arkui/arkts-apis/arkts-arkui-curve-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationTransition-curve?: Curve--><!--Device-NavDestinationTransition-curve?: Curve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: int
```

转场动画的延迟。 取值范围为全体整数，单位：ms。 默认值： 0（毫秒）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationTransition-delay?: int--><!--Device-NavDestinationTransition-delay?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

转场动画的持续时间。 取值范围为全体整数，单位：ms。 默认值： 1000（毫秒）。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationTransition-duration?: int--><!--Device-NavDestinationTransition-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: VoidCallback
```

指定转场动效的闭包函数，系统会根据闭包中对组件UI状态的修改，生成对应的过渡动画。参见 [animateTo](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto)中的event。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationTransition-event: VoidCallback--><!--Device-NavDestinationTransition-event: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTransitionEnd

```TypeScript
onTransitionEnd?: VoidCallback
```

转场动画结束时的回调函数。

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationTransition-onTransitionEnd?: VoidCallback--><!--Device-NavDestinationTransition-onTransitionEnd?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

