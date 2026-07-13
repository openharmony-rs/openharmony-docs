# LabelMarginOptions

LabelMarginOptions用于定义文本与左右侧图标之间间距。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: Dimension
```

文本与左侧图标之间间距，不支持百分比。

默认值：

size为ChipSize.SMALL时，left默认值：4

size为ChipSize.NORMAL时，left默认值：6

单位：vp

超出取值范围按默认值处理。

取值范围：[0, +∞)

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: Dimension
```

文本与右侧图标之间间距，不支持百分比。

默认值：

size为ChipSize.SMALL时，right默认值：4

size为ChipSize.NORMAL时，right默认值：6

单位：vp

超出取值范围按默认值处理。

取值范围：[0, +∞)

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

