# Polyline

折线绘制组件。

> **说明：**

> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

Uses new to create Polyline.Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolylineInterface-new (options?: PolylineOptions): PolylineAttribute--><!--Device-PolylineInterface-new (options?: PolylineOptions): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 否 | Poly line options |

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

用于绘制折线的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolylineInterface-(options?: PolylineOptions): PolylineAttribute--><!--Device-PolylineInterface-(options?: PolylineOptions): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 否 | Polyline绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [PolylineOptions](arkts-arkui-polyline-polylineoptions-i.md)
