# Polygon属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** PolygonAttribute extends [CommonShapeMethod<PolygonAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class PolygonAttribute extends CommonShapeMethod<PolygonAttribute>--><!--Device-unnamed-declare class PolygonAttribute extends CommonShapeMethod<PolygonAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## points

```TypeScript
points(value: Array<any>)
```

设置多边形的顶点坐标列表，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolygonAttribute-points(value: Array<any>): PolygonAttribute--><!--Device-PolygonAttribute-points(value: Array<any>): PolygonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 多边形的顶点坐标列表。使用时传入一个二维数组，每个子数组表示一个顶点的[x, y]坐标。<br/>默认值：[]（空数组）<br/>默认单位：vp <br/>异常值undefined和null按照默认值处理。 |

