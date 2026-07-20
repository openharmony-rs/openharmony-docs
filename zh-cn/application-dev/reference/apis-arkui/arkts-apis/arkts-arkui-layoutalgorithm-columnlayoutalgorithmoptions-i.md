# ColumnLayoutAlgorithmOptions

设置垂直方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**起始版本：** 24

<!--Device-unnamed-interface ColumnLayoutAlgorithmOptions--><!--Device-unnamed-interface ColumnLayoutAlgorithmOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: HorizontalAlign
```

所有子组件在水平方向上的对齐格式。

默认值：HorizontalAlign.Center

非法值：按默认值处理。

**类型：** HorizontalAlign

**默认值：** HorizontalAlign.Center

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign--><!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
isReverse?: boolean
```

子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](../arkts-components/arkts-arkui-commonmethod-c.md#direction-1)影响，如果[direction](../arkts-components/arkts-arkui-commonmethod-c.md#direction-1)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。

默认值：false

非法值：按默认值处理。

**类型：** boolean

**默认值：** false

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean--><!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在垂直方向上的对齐格式。

默认值：FlexAlign.Start

非法值：按默认值处理。

**类型：** FlexAlign

**默认值：** FlexAlign.Start

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign--><!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

纵向布局元素垂直方向间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

**类型：** LengthMetrics

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics--><!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

