# BlurStyleOptions

模糊样式选项，用于配置模糊效果的深浅色模式、取色模式、灰阶模糊参数和模糊程度。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

内容模糊效果使用的自适应取色模式。

默认值：AdaptiveColor.DEFAULT

**类型：** [AdaptiveColor](arkts-arkui-adaptivecolor-e.md)

**默认值：** AdaptiveColor.DEFAULT

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

灰阶模糊参数，仅对图像中的黑白色生效，对彩色无效果。

默认值：grayscale: [0,0]

**类型：** [BlurOptions](arkts-arkui-bluroptions-i.md)

**默认值：** { grayScale: [0,0] }

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

内容模糊效果使用的深浅色模式。

默认值：ThemeColorMode.SYSTEM

**类型：** [ThemeColorMode](arkts-arkui-themecolormode-e.md)

**默认值：** ThemeColorMode.SYSTEM

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

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

超出取值范围时，按边界值自动修正。

**类型：** number

**默认值：** 1.0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
