# RatingConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** RatingConfiguration extends CommonConfiguration<RatingConfiguration>

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface RatingConfiguration--><!--Device-unnamed-declare interface RatingConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator: boolean
```

评分条是否作为指示器使用。当值为true时，表示作为指示器；当值为false时，表示不作为指示器。 默认值：false

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingConfiguration-indicator: boolean--><!--Device-RatingConfiguration-indicator: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

设置并接收评分值。 默认值：0 取值范围： [0, stars] 小于0取0，大于stars取最大值stars。 该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingConfiguration-rating: number--><!--Device-RatingConfiguration-rating: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stars

```TypeScript
stars: number
```

评分条的星级总数。 默认值：5

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingConfiguration-stars: number--><!--Device-RatingConfiguration-stars: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stepSize

```TypeScript
stepSize: number
```

评分条的评分步长。 默认值：0.5

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingConfiguration-stepSize: number--><!--Device-RatingConfiguration-stepSize: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<number>
```

触发评分变化的回调，参数为新的评分值。

**类型：** Callback&lt;number&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingConfiguration-triggerChange: Callback<number>--><!--Device-RatingConfiguration-triggerChange: Callback<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

