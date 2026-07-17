# ContentCoverOptions

继承自[BindOptions](arkts-arkui-common-bindoptions-i.md)。

全屏模态页面内容选项。

**继承/实现关系：** ContentCoverOptions extends [BindOptions](arkts-arkui-common-bindoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface ContentCoverOptions extends BindOptions--><!--Device-unnamed-declare interface ContentCoverOptions extends BindOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSafeArea

```TypeScript
enableSafeArea?: boolean
```

全屏模态是否适配安全区域，true表示全屏模态适配安全区域，将内容限制在安全区内，避让导航条和状态栏，false表示不做处理，和之前的样式保持一致。默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ContentCoverOptions-enableSafeArea?: boolean--><!--Device-ContentCoverOptions-enableSafeArea?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modalTransition

```TypeScript
modalTransition?: ModalTransition
```

全屏模态页面的系统转场方式。

默认值：ModalTransition.DEFAULT。

**说明：**

与transition同时设置时，此属性不生效。

**类型：** ModalTransition

**默认值：** ModalTransition.DEFAULT

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContentCoverOptions-modalTransition?: ModalTransition--><!--Device-ContentCoverOptions-modalTransition?: ModalTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissContentCoverAction>
```

全屏模态页面交互式关闭回调函数。

**说明：**

当用户执行back事件关闭交互操作时，如果注册该回调函数，则不会立刻关闭。在回调函数中可以通过reason得到阻拦关闭页面的操作类型，从而根据原因选择是否关闭全屏模态页面。在onWillDismiss回调中，不能再做onWillDismiss拦截。

**类型：** Callback<DismissContentCoverAction>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContentCoverOptions-onWillDismiss?: Callback<DismissContentCoverAction>--><!--Device-ContentCoverOptions-onWillDismiss?: Callback<DismissContentCoverAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

全屏模态页面的自定义转场方式。

**类型：** TransitionEffect

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContentCoverOptions-transition?: TransitionEffect--><!--Device-ContentCoverOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

