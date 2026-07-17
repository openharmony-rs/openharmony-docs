# Polygon

多边形绘制组件。

> **说明：**

> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

Uses new to create Polygon.Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolygonInterface-new (options?: PolygonOptions): PolygonAttribute--><!--Device-PolygonInterface-new (options?: PolygonOptions): PolygonAttribute-End-->

**系统能力：** 
- API版本9+：SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PolygonOptions | 否 | Polygon options |

## Polygon

```TypeScript
Polygon(options?: PolygonOptions)
```

用于绘制多边形的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolygonInterface-(options?: PolygonOptions): PolygonAttribute--><!--Device-PolygonInterface-(options?: PolygonOptions): PolygonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PolygonOptions | 否 | Polygon绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [PolygonOptions](arkts-arkui-polygon-polygonoptions-i.md)
