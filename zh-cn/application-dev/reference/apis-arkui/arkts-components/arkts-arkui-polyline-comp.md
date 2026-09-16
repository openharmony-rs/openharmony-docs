# Polyline

折线绘制组件。

> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

Uses new to create Polyline. Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 否 | Polyline绘制区域，用于设置Polyline组件的宽度和高度。当需要指定Polyline的绘制区域大小时传入此参数，不传入时使用默认宽度和高度（均为0）。<br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 用于描述Polyline组件绘制属性。 |

## 示例

```TypeScript
### 示例1（组件属性绘制）

通过points、fillOpacity、stroke、strokeWidth、strokeLineJoin、strokeLineCap属性分别绘制折线的经过坐标、透明度、边框颜色、边框宽度、拐角样式、端点样式。


```

```TypeScript
### 示例2（宽和高使用不同参数类型绘制折线）

width、height属性分别使用不同的长度类型绘制图形。


```

```TypeScript
### 示例3（使用attributeModifier动态设置Polyline组件的属性）

以下示例展示了如何使用attributeModifier动态设置Polyline组件的points、fill、fillOpacity、stroke、strokeDashArray、strokeDashOffset、strokeLineCap、strokeLineJoin、strokeMiterLimit、strokeOpacity、strokeWidth和antiAlias属性。
```
