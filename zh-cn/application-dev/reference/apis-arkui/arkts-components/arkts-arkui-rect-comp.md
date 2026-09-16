# Rect

矩形绘制组件，用于在界面中绘制矩形图形，支持设置填充颜色、边框样式、圆角等属性。

> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

Use new function to create Rect. Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) &#124; [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect options |

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

用于绘制矩形的构造函数。调用后创建一个Rect对象，可设置宽度、高度、圆角等属性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) &#124; [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect绘制属性，包含宽度、高度、圆角等配置。不传入时使用各属性默认值绘制矩形（宽高和圆角均为0）。<br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RectOptions](arkts-arkui-rectoptions-i.md) | 用于描述矩形绘制组件的绘制属性。 |
| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 用于描述圆角矩形绘制组件的绘制属性。 |

## 示例

```TypeScript
### 示例1（组件属性绘制）

使用fill、fillOpacity、stroke、radius属性分别绘制矩形的填充颜色、透明度、边框颜色、圆角。


```

```TypeScript
### 示例2（绘制渐变色矩形）

使用通用属性[linearGradient](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-gradient-color.md#lineargradient18)、[clipShape](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clipshape18)分别绘制渐变色矩形。

从API version 18开始，新增linearGradient、clipShape通用属性。


```

```TypeScript
### 示例3（使用不同参数类型绘制矩形）

width、height、radius、radiusWidth、radiusHeight等属性分别使用不同的长度类型绘制图形。


```

```TypeScript
### 示例4（使用attributeModifier动态设置Rect组件的属性）

以下示例展示了如何使用attributeModifier动态设置Rect组件的fill、fillOpacity、stroke、strokeDashArray、strokeDashOffset、strokeLineCap、strokeLineJoin、strokeMiterLimit、strokeOpacity、strokeWidth和antiAlias属性。
```
