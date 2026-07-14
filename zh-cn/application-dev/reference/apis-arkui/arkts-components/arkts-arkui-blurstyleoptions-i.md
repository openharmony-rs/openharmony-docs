# BlurStyleOptions

内容模糊选项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

内容模糊效果使用的取色模式。

默认值：AdaptiveColor.DEFAULT

**类型：** AdaptiveColor

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

灰阶模糊参数。

默认值：grayscale: [0,0]

**类型：** BlurOptions

**默认值：** { grayScale: [0,0] }

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

内容模糊效果使用的深浅色模式。

默认值：ThemeColorMode.SYSTEM

**类型：** ThemeColorMode

**默认值：** ThemeColorMode.SYSTEM

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

内容模糊效果程度。

默认值：1.0

取值范围：[0.0, 1.0]

1.0表示模糊程度最高。

0.0表示模糊程度最低。

**类型：** number

**默认值：** 1.0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

