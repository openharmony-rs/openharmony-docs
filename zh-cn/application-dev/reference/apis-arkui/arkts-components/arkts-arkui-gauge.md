# Gauge

数据量规图表组件，用于将数据展示为环形图表。

> **说明：**

> - 该组件从API版本26.0.0开始支持[WithTheme]{@link with_theme}。

## 子组件

可以包含单个子组件。
> **说明：**  
>  
> - 支持的子组件类型：系统组件和自定义组件，支持条件渲染控制[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)，不支持循环渲染控制  
> [ForEach]{@link for_each}和[LazyForEach]{@link lazy_for_each}。  
>  
> - 建议使用文本组件构建当前数值文本和辅助文本。  
>  
> - 若子组件宽高为百分比形式，则基准范围为以外圆环做为内切圆的矩形。

## Gauge

```TypeScript
Gauge(options: GaugeOptions)
```

创建数据量规图表组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GaugeInterface-(options: GaugeOptions): GaugeAttribute--><!--Device-GaugeInterface-(options: GaugeOptions): GaugeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GaugeOptions](arkts-arkui-gaugeoptions-i.md) | 是 | 数据量规图表组件参数。 |

## 汇总

- [GaugeConfiguration](arkts-arkui-gauge-gaugeconfiguration-i.md)
- [GaugeIndicatorOptions](arkts-arkui-gauge-gaugeindicatoroptions-i.md)
- [GaugeOptions](arkts-arkui-gauge-gaugeoptions-i.md)
- [GaugeShadowOptions](arkts-arkui-gauge-gaugeshadowoptions-i.md)
