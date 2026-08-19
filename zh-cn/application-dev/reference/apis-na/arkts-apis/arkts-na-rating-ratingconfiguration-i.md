# RatingConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** RatingConfiguration extends CommonConfiguration<RatingConfiguration>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RatingConfiguration--><!--Device-unnamed-export declare interface RatingConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator: boolean
```

评分条是否作为指示器使用。当值为true时，表示作为指示器；当值为false时，表示不作为指示器。 默认值：false

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingConfiguration-indicator: boolean--><!--Device-RatingConfiguration-indicator: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: double
```

设置并接收评分值。 默认值：0 取值范围： [0, stars] 小于0取0，大于stars取最大值stars。 该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingConfiguration-rating: double--><!--Device-RatingConfiguration-rating: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stars

```TypeScript
stars: int
```

评分条的星级总数。 默认值：5

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingConfiguration-stars: int--><!--Device-RatingConfiguration-stars: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stepSize

```TypeScript
stepSize: double
```

评分条的评分步长。 默认值：0.5

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingConfiguration-stepSize: double--><!--Device-RatingConfiguration-stepSize: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<double>
```

触发评分数量变化。

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RatingConfiguration-triggerChange: Callback<double>--><!--Device-RatingConfiguration-triggerChange: Callback<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

