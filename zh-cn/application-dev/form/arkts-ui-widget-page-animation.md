# ArkTS卡片为组件添加动效
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->

ArkTS卡片开放了使用动画效果的能力，支持[显式动画](../reference/apis-arkui/arkui-ts/ts-explicit-animation.md)、[属性动画](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md)、[组件内转场](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md)能力。ArkTS卡片使用动画效果时具有以下限制：

**表1** 动效参数限制

| 名称 | 参数说明 | 限制描述 |
| -------- | -------- | -------- |
| duration | 动画播放时长 | 限制最长的动效播放时长为1秒，当设置大于1秒的时间时，动效时长仍为1秒。 |
| tempo | 动画播放速度 | 卡片中禁止设置此参数，使用默认值1。 |
| delay | 动画延迟执行的时长 | 卡片中禁止设置此参数，使用默认值0毫秒。 |
| iterations | 动画播放次数 | 卡片中禁止设置此参数，使用默认值1次。 |

>**说明：**
>
>静态卡片不支持使用动效能力。

## 组件自身动效
以下示例代码使用[animation](../reference/apis-arkui/arkui-ts/ts-animatorproperty.md)接口实现了按钮旋转的动画效果。 

![WidgetAnimation](figures/WidgetAnimation.gif)



<!-- @[animation_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/ArkTSCardDocsSample/entry/src/main/ets/widget/pages/AnimationCard.ets) -->
## 组件转场动效
以下示例代码使用[transition](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md)接口实现了在卡片内图片出现与消失的动画效果。

![WidgetAnimation](figures/WidgetTransitionAnimation.gif)

<!-- @[TransitionEffectExample1_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormStandaloneDemo/library/src/main/ets/widget1/pages/TransitionEffectExample1.ets) -->