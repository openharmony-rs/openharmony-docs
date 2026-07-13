# BackgroundEffectOptions

背景效果参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

背景模糊效果使用的取色模式，默认为DEFAULT。使用AVERAGE时color必须带有透明度，取色模式才生效。

**类型：** AdaptiveColor

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

灰阶模糊参数，默认为[0,0]。

**类型：** BlurOptions

**默认值：** { grayScale: [0,1] } [since 11 - 11]
@default { grayScale: [0,0] } [since 12]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## brightness

```TypeScript
brightness?: number
```

亮度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 2]。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

颜色，默认透明色。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

模糊不生效时使用的背景色。该参数需配合policy参数使用。当policy使模糊失效时，控件模糊效果会被移除，如果设置了inactiveColor会使用inactiveColor作为控件背景色。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

模糊激活策略。

默认值：BlurStyleActivePolicy.ALWAYS_ACTIVE

**类型：** BlurStyleActivePolicy

**默认值：** BlurStyleActivePolicy.ALWAYS_ACTIVE

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

模糊半径，取值范围：[0, +∞)，默认为0。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saturation

```TypeScript
saturation?: number
```

饱和度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 50]。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

