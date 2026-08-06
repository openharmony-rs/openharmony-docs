# BackgroundEffectOptions

背景效果参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BackgroundEffectOptions--><!--Device-unnamed-export declare interface BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

背景模糊效果使用的取色模式，默认为DEFAULT。使用AVERAGE时color必须带有透明度，取色模式才生效。

**类型：** AdaptiveColor

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-adaptiveColor?: AdaptiveColor--><!--Device-BackgroundEffectOptions-adaptiveColor?: AdaptiveColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

灰阶模糊参数，默认为[0,0]。

**类型：** BlurOptions

**默认值：** { grayScale: [0,0] }

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-blurOptions?: BlurOptions--><!--Device-BackgroundEffectOptions-blurOptions?: BlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## brightness

```TypeScript
brightness?: double
```

亮度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 2]。

**类型：** double

**默认值：** 1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-brightness?: double--><!--Device-BackgroundEffectOptions-brightness?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

颜色，默认透明色。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-color?: ResourceColor--><!--Device-BackgroundEffectOptions-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

模糊不生效时使用的背景色。该参数需配合policy参数使用。当policy使模糊失效时，控件模糊效果会被移除，如果设置了inactiveColor会使用inactiveColor作为控件背景色。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-inactiveColor?: ResourceColor--><!--Device-BackgroundEffectOptions-inactiveColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

模糊激活策略。 默认值：BlurStyleActivePolicy.ALWAYS\_ACTIVE

**类型：** BlurStyleActivePolicy

**默认值：** BlurStyleActivePolicy.ALWAYS_ACTIVE

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-policy?: BlurStyleActivePolicy--><!--Device-BackgroundEffectOptions-policy?: BlurStyleActivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: double | undefined
```

模糊半径，取值范围：[0, +∞)，默认为0。

**类型：** double \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-radius: double | undefined--><!--Device-BackgroundEffectOptions-radius: double | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saturation

```TypeScript
saturation?: double
```

饱和度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 50]。

**类型：** double

**默认值：** 1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundEffectOptions-saturation?: double--><!--Device-BackgroundEffectOptions-saturation?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

