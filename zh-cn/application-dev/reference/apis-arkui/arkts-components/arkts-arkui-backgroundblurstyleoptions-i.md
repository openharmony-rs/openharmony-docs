# BackgroundBlurStyleOptions

继承自[BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)。

**继承/实现关系：** BackgroundBlurStyleOptions extends [BlurStyleOptions](arkts-arkui-blurstyleoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface BackgroundBlurStyleOptions extends BlurStyleOptions--><!--Device-unnamed-declare interface BackgroundBlurStyleOptions extends BlurStyleOptions-End-->

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

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundBlurStyleOptions-inactiveColor?: ResourceColor--><!--Device-BackgroundBlurStyleOptions-inactiveColor?: ResourceColor-End-->

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

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundBlurStyleOptions-policy?: BlurStyleActivePolicy--><!--Device-BackgroundBlurStyleOptions-policy?: BlurStyleActivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

