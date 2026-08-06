# Gauge

数据量规图表组件，用于将数据展示为环形图表。适用于展示任务完成进度、性能指标、数据占比等场景，支持自定义颜色、起止角度、指针样式、阴影效果等多种视觉配置，能够直观地呈现数据状态，提升用户对数据的理解和交互体验。 > **说明：** > > - 该组件从API版本26.0.0开始支持[WithTheme]{@link ./with_theme}。

## 子组件 可以包含单个子组件。 > **说明：** > > - 支持的子组件类型：系统组件和自定义组件，支持条件渲染控制[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)，不支持循环渲染控制 > [ForEach]{@link ./for_each}和[LazyForEach]{@link ./lazy_for_each}。 > > - 建议使用文本组件构建当前数值文本和辅助文本。 > > - 若子组件宽高为百分比形式，则百分比基准为以外圆作为内切圆的矩形的宽和高。

## Gauge

```TypeScript
Gauge(options: GaugeOptions)
```

创建数据量规图表组件。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GaugeInterface-(options: GaugeOptions): GaugeAttribute--><!--Device-GaugeInterface-(options: GaugeOptions): GaugeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 数据量规图表组件参数。 |

## 汇总

