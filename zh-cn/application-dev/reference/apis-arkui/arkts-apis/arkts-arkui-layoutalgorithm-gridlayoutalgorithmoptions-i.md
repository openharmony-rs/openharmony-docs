# GridLayoutAlgorithmOptions

设置网格布局算法的列数模板、列间距、行间距。

**起始版本：** 24

<!--Device-unnamed-interface GridLayoutAlgorithmOptions--><!--Device-unnamed-interface GridLayoutAlgorithmOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: LengthMetrics
```

列与列之间的间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LengthMetrics

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithmOptions-columnsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithmOptions-columnsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
columnsTemplate?: string | ItemFillPolicy
```

设置当前网格布局的列数。

默认值：'1fr'

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** string \| ItemFillPolicy

**默认值：** '1fr'

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithmOptions-columnsTemplate?: string | ItemFillPolicy--><!--Device-GridLayoutAlgorithmOptions-columnsTemplate?: string | ItemFillPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: LengthMetrics
```

行与行之间的间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LengthMetrics

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithmOptions-rowsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithmOptions-rowsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

