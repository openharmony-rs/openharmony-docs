# BackgroundBlurStyleOptions

继承自[BlurStyleOptions](arkts-na-common-blurstyleoptions-i.md)。

**继承/实现关系：** BackgroundBlurStyleOptions extends [BlurStyleOptions](arkts-na-common-blurstyleoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BackgroundBlurStyleOptions--><!--Device-unnamed-export declare interface BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

模糊不生效时使用的背景色。该参数需配合policy参数使用。当policy使模糊失效时，控件模糊效果会被移除，如果设置了inactiveColor会使用inactiveColor作为控件背景色。

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** Color.Transparent

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundBlurStyleOptions-inactiveColor?: ResourceColor--><!--Device-BackgroundBlurStyleOptions-inactiveColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

模糊激活策略。 默认值：BlurStyleActivePolicy.ALWAYS_ACTIVE

**类型：** [BlurStyleActivePolicy](arkts-na-common-blurstyleactivepolicy-e.md)

**默认值：** BlurStyleActivePolicy.ALWAYS_ACTIVE

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundBlurStyleOptions-policy?: BlurStyleActivePolicy--><!--Device-BackgroundBlurStyleOptions-policy?: BlurStyleActivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

