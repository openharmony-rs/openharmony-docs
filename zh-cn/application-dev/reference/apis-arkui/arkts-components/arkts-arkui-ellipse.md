# Ellipse

椭圆绘制组件。该组件通过设置宽度和高度属性绘制椭圆形状，在给定的矩形区域内渲染椭圆轮廓和填充区域。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 无

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

use new function to set the value. Anonymous Object Rectification.

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-EllipseInterface-new (options?: EllipseOptions): EllipseAttribute--><!--Device-EllipseInterface-new (options?: EllipseOptions): EllipseAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipseoptions-i.md) | 否 | ellipse options |

## Ellipse

```TypeScript
Ellipse(options?: EllipseOptions)
```

用于绘制椭圆的构造函数。调用后创建一个Ellipse对象，可设置宽高属性。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-EllipseInterface-(options?: EllipseOptions): EllipseAttribute--><!--Device-EllipseInterface-(options?: EllipseOptions): EllipseAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EllipseOptions](arkts-arkui-ellipseoptions-i.md) | 否 | 椭圆绘制配置选项，包含宽度和高度设置。不传入时使用默认尺寸（宽度和高度均为0）。 <br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [EllipseOptions](arkts-arkui-ellipseoptions-i.md)
