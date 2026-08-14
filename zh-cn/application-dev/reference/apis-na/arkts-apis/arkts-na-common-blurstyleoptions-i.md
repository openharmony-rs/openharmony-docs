# BlurStyleOptions

Defines the options of blurStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface BlurStyleOptions--><!--Device-unnamed-export declare interface BlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

Adaptive color mode. &lt;br&gt;Default value: **AdaptiveColor.DEFAULT**.

**类型：** [AdaptiveColor](arkts-na-common-adaptivecolor-e.md)

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlurStyleOptions-adaptiveColor?: AdaptiveColor--><!--Device-BlurStyleOptions-adaptiveColor?: AdaptiveColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

Defines the options of blur

**类型：** [BlurOptions](arkts-na-common-bluroptions-i.md)

**默认值：** { grayScale: [0,0] }

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlurStyleOptions-blurOptions?: BlurOptions--><!--Device-BlurStyleOptions-blurOptions?: BlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

Color mode used for the foreground blur. &lt;br&gt;Default value: **ThemeColorMode.SYSTEM**.

**类型：** [ThemeColorMode](arkts-na-common-themecolormode-e.md)

**默认值：** ThemeColorMode.SYSTEM

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlurStyleOptions-colorMode?: ThemeColorMode--><!--Device-BlurStyleOptions-colorMode?: ThemeColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: double
```

Foreground blur scale. &lt;br&gt;Default value: **1.0**. &lt;br&gt;Value range: [0.0, 1.0].

**类型：** double

**默认值：** 1.0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlurStyleOptions-scale?: double--><!--Device-BlurStyleOptions-scale?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

