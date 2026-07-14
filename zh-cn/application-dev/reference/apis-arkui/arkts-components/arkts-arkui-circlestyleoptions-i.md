# CircleStyleOptions

圆环样式的参数说明。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

背景圆环颜色。

默认值：'#33182431'。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableForeground

```TypeScript
enableForeground?: boolean
```

背景圆环是否显示在宫格圆点上层。

true：背景圆环显示在宫格圆点上层，遮盖宫格圆点；false：背景圆环显示在宫格圆点下层，不遮盖宫格圆点。

默认值：false。

**类型：** boolean

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableWaveEffect

```TypeScript
enableWaveEffect?: boolean
```

选中宫格圆点后的波浪效果开关。

true：显示波浪效果；false：不显示波浪效果。

默认值：true。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: LengthMetrics
```

背景圆环的半径。

默认值：[circleRadius](PatternLockAttribute#circleRadius)的1.833倍（即11/6）。

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

