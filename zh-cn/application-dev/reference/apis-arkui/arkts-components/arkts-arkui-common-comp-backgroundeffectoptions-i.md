# BackgroundEffectOptions

```TypeScript
declare interface BackgroundEffectOptions
```

背景效果参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

背景模糊效果使用的取色模式，默认为DEFAULT。使用AVERAGE时color必须带有透明度，取色模式才生效；若color不带透明度，取色模式不生效。

**类型：** [AdaptiveColor](arkts-arkui-common-comp-adaptivecolor-e.md)

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

灰阶模糊参数，默认为[0,0]。

**类型：** [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md)

**默认值：** 
- API版本11：{ grayScale: [0,1] }
- API版本12+：{ grayScale: [0,0] }

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## brightness

```TypeScript
brightness?: number
```

亮度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 2]。传入负数时，恢复为默认值1。超出推荐取值范围时，效果可能不符合预期。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

背景效果的蒙版颜色，默认透明色。当adaptiveColor为AVERAGE时，color必须带有透明度，取色模式才生效。设置不同颜色值会在背景模糊效果上叠加对应颜色的蒙版层。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** Color.Transparent

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

模糊不生效时使用的背景色。该参数需配合policy参数使用。当policy使模糊失效时，组件模糊效果会被移除。如果设置了inactiveColor，会使用inactiveColor作为组件背景色；如果未设置inactiveColor，组件背景色恢复为默认透明色。默认不设置inactiveColor背景色。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** Color.Transparent

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

模糊激活策略。

默认值：BlurStyleActivePolicy.ALWAYS_ACTIVE

**类型：** [BlurStyleActivePolicy](arkts-arkui-common-comp-blurstyleactivepolicy-e.md)

**默认值：** BlurStyleActivePolicy.ALWAYS_ACTIVE

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

模糊半径，单位：vp。取值范围：[0, +∞)，默认为0。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## saturation

```TypeScript
saturation?: number
```

饱和度，取值范围：[0, +∞)，默认为1。推荐取值范围：[0, 50]。传入负数时，恢复为默认值1。超出推荐取值范围时，效果可能不符合预期。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
