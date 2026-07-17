# ContentModifier

开发者需要自定义class实现ContentModifier接口。

**起始版本：** 12

<!--Device-unnamed-declare interface ContentModifier<T>--><!--Device-unnamed-declare interface ContentModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyContent

```TypeScript
applyContent(): WrappedBuilder<[T]>
```

定制内容区的Builder。

**T参数支持范围:**

ButtonConfiguration、CheckBoxConfiguration、DataPanelConfiguration、TextClockConfiguration、ToggleConfiguration、GaugeConfiguration、LoadingProgressConfiguration、RadioConfiguration、ProgressConfiguration、RatingConfiguration、SliderConfiguration

**属性支持范围:**

支持通用属性enabled，contentModifier。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContentModifier-applyContent(): WrappedBuilder<[T]>--><!--Device-ContentModifier-applyContent(): WrappedBuilder<[T]>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WrappedBuilder](arkts-arkui-common-wrappedbuilder-c.md)<[T]> | 组件的属性类，用来区别不同组件自定义内容区后所需要的不同信息，比如Button组件的ButtonConfiguration，Checkbox组件的CheckBoxConfiguration等。 |

