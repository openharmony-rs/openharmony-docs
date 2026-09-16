# Gauge

数据量规图表组件，用于将数据展示为环形图表。适用于展示任务完成进度、性能指标、数据占比等场景，支持自定义颜色、起止角度、指针样式、阴影效果等多种视觉配置，能够直观地呈现数据状态，提升用户对数据的理解和交互体验。

> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

可以包含单个子组件。

> **说明：** 
> 
> - 支持的子组件类型：系统组件和自定义组件，支持条件渲染控制[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)，不支持循环渲染控制ForEach和LazyForEach。
> 
> - 建议使用文本组件构建当前数值文本和辅助文本。
> 
> - 若子组件宽高为百分比形式，则百分比基准为以外圆作为内切圆的矩形的宽和高。

## Gauge

```TypeScript
Gauge(options: GaugeOptions)
```

创建数据量规图表组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GaugeOptions](arkts-arkui-gaugeoptions-i.md) | 是 | 数据量规图表组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [GaugeConfiguration](arkts-arkui-gaugeconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [GaugeIndicatorOptions](arkts-arkui-gaugeindicatoroptions-i.md) | 数据量规图表指针选项。 |
| [GaugeOptions](arkts-arkui-gaugeoptions-i.md) | 数据量规图表选项。 |
| [GaugeShadowOptions](arkts-arkui-gaugeshadowoptions-i.md) | GaugeShadowOptions继承自[MultiShadowOptions](arkts-arkui-multishadowoptions-i.md)，具有MultiShadowOptions的全部属性。 |

## 示例

```TypeScript
### 示例1（设置多色量规图）

该示例通过[colors](#colors)接口，实现了多色量规图效果。


```

```TypeScript
### 示例2（设置单色量规图）

该示例通过[colors](#colors)接口，实现了单色量规图效果。


```

```TypeScript
### 示例3（设置定制说明区）

该示例通过[description](#description11)接口，实现了说明区的设置功能。


```

```TypeScript
### 示例4（设置辅助区）

该示例通过设置子组件，实现了辅助区的设置功能。


```

```TypeScript
### 示例5（设置最大最小值）

该示例通过设置[GaugeOptions](#gaugeoptions18对象说明)的min、max属性，实现了量规图的最大最小值设置的功能。


```

```TypeScript
### 示例6（设置指针）

该示例通过[indicator](#indicator11)接口，实现了设置量规图的指针的功能。


```

```TypeScript
### 示例7（设置起止角度）

该示例通过[startAngle](#startangle)和[endAngle](#endangle)接口，实现了量规图起止角度设置的功能。


```

```TypeScript
### 示例8（设置定制内容区）

该示例通过[contentModifier](#contentmodifier12)接口，实现了定制量规图内容区的功能。


```

```TypeScript
### 示例9（设置隐私隐藏）

该示例展示了[privacySensitive](#privacysensitive12)接口的调用方式。实际隐私隐藏效果需要卡片框架支持。


```

```TypeScript
### 示例10（设置自定义指针）

该示例通过[indicator](#indicator11)接口，实现了自定义指针功能，开发者导入svg类型的图片以替换默认指针。
```

```TypeScript
<svg width='200px' height='200px'>
    <path d='M 10,30 A 20,20 0,0,1 50,30 A 20,20 0,0,1 90,30 Q 90,60 50,90 Q 10,60 10,30 z'
          stroke='black' stroke-width='3' fill='white'>
    </path>
</svg>
```
