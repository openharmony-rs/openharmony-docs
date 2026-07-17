# LinearGradientBlurOptions

**起始版本：** 12

<!--Device-unnamed-declare interface LinearGradientBlurOptions--><!--Device-unnamed-declare interface LinearGradientBlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: GradientDirection
```

渐变模糊方向。

默认值：

GradientDirection.Bottom

**类型：** GradientDirection

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinearGradientBlurOptions-direction: GradientDirection--><!--Device-LinearGradientBlurOptions-direction: GradientDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fractionStops

```TypeScript
fractionStops: FractionStop[]
```

数组中保存的每一个二元数组（取值0-1，小于0则为0，大于1则为1）表示[模糊程度, 模糊位置]；模糊位置需严格递增，开发者传入的数据不符合规范会记录日志，渐变模糊数组中二元数组个数必须大于等于2，否则渐变模糊不生效。

**类型：** FractionStop[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LinearGradientBlurOptions-fractionStops: FractionStop[]--><!--Device-LinearGradientBlurOptions-fractionStops: FractionStop[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

