# ColumnLayoutAlgorithmOptions

设置垂直方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-interface ColumnLayoutAlgorithmOptions--><!--Device-unnamed-interface ColumnLayoutAlgorithmOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: HorizontalAlign
```

所有子组件在水平方向上的对齐格式。 非法值：按默认值处理。

**类型：** [HorizontalAlign](arkts-na-enums-horizontalalign-e.md)

**默认值：** HorizontalAlign.Center

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign--><!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
isReverse?: boolean
```

子组件在垂直方向上的排列是否反转。 取值为true表示子组件在垂直方向上反转排列。 取值为false表示子组件在垂直方向上正序排列。 非法值：按默认值处理。

**类型：** boolean

**默认值：** false

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean--><!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在垂直方向上的对齐格式。 非法值：按默认值处理。

**类型：** [FlexAlign](arkts-na-enums-flexalign-e.md)

**默认值：** FlexAlign.Start

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign--><!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

纵向布局元素垂直方向间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics--><!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

