# Polygon

多边形绘制组件。该组件通过设置顶点坐标列表来定义多边形的形状，支持填充颜色、边框样式等属性配置。组件采用二维坐标系统，按照顶点顺序依次连接形成封闭多边形区域。适用于绘制三角形、四边形、五边形等自定义多边形形状，以及实现图表、图标等需要 多边形元素的可视化场景。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > updateConstructorParams接口更新构造参数。

## 子组件 无

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Uses new to create Polygon. Anonymous Object Rectification.

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolygonInterface-new (options?: PolygonOptions): PolygonAttribute--><!--Device-PolygonInterface-new (options?: PolygonOptions): PolygonAttribute-End-->

**系统能力：** 
- API版本9+：SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygonoptions-i.md) | 否 | Polygon options |

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

用于绘制多边形的构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolygonInterface-(options?: PolygonOptions): PolygonAttribute--><!--Device-PolygonInterface-(options?: PolygonOptions): PolygonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygonoptions-i.md) | 否 | Polygon组件的配置选项，用于定义绘制区域的宽度和高度。需要指定多边形尺寸时传入此参数，不传入时使用默认宽度和高度（均为0）。当传入undefined 或null时，参数设置无效，组件属性维持原值。 |

## 汇总

- [PolygonOptions](arkts-arkui-polygonoptions-i.md)
