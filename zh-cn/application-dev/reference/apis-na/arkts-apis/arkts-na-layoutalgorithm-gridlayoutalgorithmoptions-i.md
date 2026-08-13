# GridLayoutAlgorithmOptions

设置网格布局算法的列数模板、列间距、行间距。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-interface GridLayoutAlgorithmOptions--><!--Device-unnamed-interface GridLayoutAlgorithmOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: LengthMetrics
```

列与列之间的间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithmOptions-columnsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithmOptions-columnsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
columnsTemplate?: string | ItemFillPolicy
```

设置当前网格布局的列数。 非法值：按默认值处理。

**类型：** string \| [ItemFillPolicy](arkts-na-units-itemfillpolicy-i.md)

**默认值：** '1fr'

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithmOptions-columnsTemplate?: string | ItemFillPolicy--><!--Device-GridLayoutAlgorithmOptions-columnsTemplate?: string | ItemFillPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: LengthMetrics
```

行与行之间的间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithmOptions-rowsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithmOptions-rowsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

