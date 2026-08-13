# RowLayoutAlgorithmOptions

设置水平方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-interface RowLayoutAlgorithmOptions--><!--Device-unnamed-interface RowLayoutAlgorithmOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: VerticalAlign
```

所有子组件在垂直方向上的对齐格式。 非法值：按默认值处理。

**类型：** [VerticalAlign](arkts-na-enums-verticalalign-e.md)

**默认值：** VerticalAlign.Center

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithmOptions-alignItems?: VerticalAlign--><!--Device-RowLayoutAlgorithmOptions-alignItems?: VerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
isReverse?: boolean
```

子组件在水平方向上的排列是否反转。 取值为true表示子组件在水平方向上反转排列， 由于水平方向受通用属性 [direction](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#direction)影响， 如果[direction](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#direction)属性生效， 再做一次反转。 取值为false表示子组件在水平方向上正序排列。 非法值：按默认值处理。

**类型：** boolean

**默认值：** false

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithmOptions-isReverse?: boolean--><!--Device-RowLayoutAlgorithmOptions-isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在水平方向上的对齐格式。 非法值：按默认值处理。

**类型：** [FlexAlign](arkts-na-enums-flexalign-e.md)

**默认值：** FlexAlign.Start

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithmOptions-justifyContent?: FlexAlign--><!--Device-RowLayoutAlgorithmOptions-justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

横向布局元素水平方向间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithmOptions-space?: LengthMetrics--><!--Device-RowLayoutAlgorithmOptions-space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

