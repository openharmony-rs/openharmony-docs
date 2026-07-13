# RatingConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** RatingConfiguration extends [CommonConfiguration<RatingConfiguration>](CommonConfiguration<RatingConfiguration>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator: boolean
```

评分条是否作为指示器使用。当值为true时，表示作为指示器；当值为false时，表示不作为指示器。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

设置并接收评分值。

默认值：0

取值范围： [0, stars]

小于0取0，大于[stars](RatingAttribute#stars(value: number))取最大值stars。

该参数支持[$$](../../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

该参数支持[!!](../../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stars

```TypeScript
stars: number
```

评分条的星级总数。

默认值：5

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stepSize

```TypeScript
stepSize: number
```

评分条的评分步长。

默认值：0.5

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<number>
```

触发评分数量变化。

**类型：** Callback<number>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

