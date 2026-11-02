# RepeatOptions

```TypeScript
interface RepeatOptions
```

创建Repeat组件时的配置项。

**起始版本：** 26.1.0

<!--Device-unnamed-interface RepeatOptions--><!--Device-unnamed-interface RepeatOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowReuseInAnimation

```TypeScript
allowReuseInAnimation?: boolean
```

动画过程中Repeat更新时，是否允许复用子组件。仅在Repeat的父容器组件为List、Grid、WaterFlow时生效。

Repeat与动画一起使用时，Repeat自身的复用能力会与动画产生冲突，导致动画效果异常。此时可将该参数设置为false，动画过程中Repeat更新时将不复用子组件，从而达到适配动画的效果。

true：动画过程中允许复用子组件。

false：动画过程中不允许复用子组件。

默认值：Repeat的父容器为List时为false，为Grid或WaterFlow时为true

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.1.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-RepeatOptions-allowReuseInAnimation?: boolean--><!--Device-RepeatOptions-allowReuseInAnimation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: RepeatController
```

绑定到Repeat组件上的控制器。绑定后，需要清理缓存时可调用[clearCache](arkts-arkui-repeat-comp-repeatcontroller-c.md#clearcache)清理Repeat组件复用池中的节点。

**类型：** [RepeatController](arkts-arkui-repeat-comp-repeatcontroller-c.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RepeatOptions-controller?: RepeatController--><!--Device-RepeatOptions-controller?: RepeatController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
