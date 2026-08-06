# TabContentAnimatedTransition

Tabs自定义切换动画相关信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TabContentAnimatedTransition--><!--Device-unnamed-export declare interface TabContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: int
```

Tabs自定义切换动画超时时间。从自定义动画开始切换计时，如果到达该时间后，开发者仍未调用[TabContentTransitionProxy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的 finishTransition接口通知Tabs组件自定义动画结束，那么组件就会认为此次自定义动画已结束，直接执行后续操作。 单位为： ms，取值应为≥0的整数。 默认值： 1000。

**类型：** int

**默认值：** 1000 ms

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabContentAnimatedTransition-timeout?: int--><!--Device-TabContentAnimatedTransition-timeout?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<TabContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback&lt;TabContentTransitionProxy&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>--><!--Device-TabContentAnimatedTransition-transition: Callback<TabContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

