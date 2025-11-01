# 几何形状绘制（ArkTS）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->


## 场景介绍

当前支持绘制的几何形状，主要包括以下几种：

- 点

- 圆弧

- 圆

- 路径

- 区域

- 矩形

- 圆角矩形

大部分的几何形状均可以选择使用画笔或者使用画刷来实现绘制，其中点的绘制只能使用画笔。


## 接口说明

几何形状绘制的常用接口如下表所示，详细的使用和参数说明请见[drawing.Canvas](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md)。

| 接口 | 描述 |
| -------- | -------- |
| drawPoint(x: number, y: number): void | 用于画一个点。 |
| drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void | 用于画一个弧。 |
| drawCircle(x: number, y: number, radius: number): void | 用于画一个圆形。 |
| drawPath(path: Path): void | 用于画一个自定义路径。 |
| drawRegion(region: Region): void | 用于画一块区域。 |
| drawRect(left: number, top: number, right: number, bottom: number): void | 用于画一个矩形。 |
| drawRoundRect(roundRect: RoundRect): void | 用于画一个圆角矩形。 |


## 绘制点

点只能基于画笔在画布上进行绘制，通过使用drawPoint()接口绘制点。绘制点需要接受两个参数，分别为需要绘制的点的x坐标和y坐标。

简单示例如下：

<!-- @[arkts_graphics_draw_point](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// 设置画笔
let pen = new drawing.Pen();
// 设置颜色
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// 设置线宽
pen.setStrokeWidth(40);
// 设置画笔描边效果
canvas.attachPen(pen);
// 绘制5个点
<!-- @[arkts_graphics_draw_arc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// 创建画笔
let pen = new drawing.Pen();
// 设置颜色
pen.setColor({
  alpha: 0xFF,
  red: 0xFF,
  green: 0x00,
  blue: 0x00
});
// 设置线宽
pen.setStrokeWidth(20);
// 设置画笔描边效果
canvas.attachPen(pen);
// 创建矩形对象
const rect: common2D.Rect = {
  left: VALUE_100,
  top: VALUE_200,
  right: VALUE_1000,
  bottom: VALUE_600
};
// 绘制矩形
canvas.drawArc(rect, 0, 180);
// 去除描边效果
canvas.detachPen();
```
canvas.drawPoint(VALUE_400, VALUE_400);
canvas.drawPoint(VALUE_600, VALUE_600);
canvas.drawPoint(VALUE_800, VALUE_800);
canvas.drawPoint(VALUE_1000, VALUE_1000);
// 去除描边效果
canvas.detachPen();
```

![Screenshot_20241129174520171](figures/Screenshot_20241129174520171.jpg)


## 绘制圆弧

可以使用画笔或画刷在画布上进行圆弧的绘制，通过使用drawArc()接口绘制圆弧。

绘制圆弧需要一个矩形（[common2D.Rect](../reference/apis-arkgraphics2d/js-apis-graphics-common2D.md#rect)），以矩形的边为轮廓进行绘制，还需要两个参数，分别表示弧形的起始角度（startAngle）和扫描角度（sweepAngle）。

此处以使用画笔绘制圆弧为例，简单示例如下：
<!-- @[arkts_graphics_draw_arc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![zh-cn_image_0000002194025289](figures/zh-cn_image_0000002194025289.png)


## 绘制圆

可以使用画笔或画刷在画布上进行圆的绘制，通过使用drawCircle()接口绘制圆。

绘制圆需要圆心点的x坐标和y坐标，以及圆半径（radius）。

此处以使用画笔绘制圆为例，简单示例如下：
<!-- @[arkts_graphics_draw_circle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![Screenshot_20241129172555673](figures/Screenshot_20241129172555673.jpg)


## 绘制路径

可以使用画笔或画刷在画布上进行路径的绘制，路径具体可以用于绘制直线、弧线、贝塞尔曲线等，也可以通过路径组合的方式组成其他复杂的形状。

绘制路径的相关接口和实现如下，详细的使用和参数说明请见[Path](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Path.md)。常用的接口如下：

1. 使用new drawing.Path()可以创建一个路径对象。

2. 使用moveTo()接口可以设置自定义路径的起始点位置。

3. 使用lineTo()接口可以添加一条从起始点或路径的最后点位置（若路径没有内容则默认为(0,0)）到目标点位置的线段。

此处以使用画笔和画刷绘制五角星为例，简单示例如下：

<!-- @[arkts_graphics_draw_path](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![Screenshot_20241129164326302](figures/Screenshot_20241129164326302.jpg)


## 绘制区域

区域不是一个特定的形状，可以设置为指定的矩形或路径，也可以对两个区域进行组合操作。可以使用画笔或画刷对区域进行绘制。详细的API说明请参考[Region](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Region.md)。

目前支持设置矩形区域和路径区域，分别通过setRect()接口和setPath()接口来设置。

此处以使用画刷绘制矩形的组合区域为例，示例如下：

<!-- @[arkts_graphics_draw_region](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![Screenshot_20241206112505234](figures/Screenshot_20241206112505234.jpg)


## 绘制矩形

可以使用画笔或画刷在画布上进行矩形的绘制。使用drawRect()接口绘制矩形。接口需要传入四个浮点数，分别表示矩形的左、上、右、下四个位置的坐标，连接这4个坐标形成一个矩形。

此处以使用画刷绘制矩形为例，简单示例如下：

<!-- @[arkts_graphics_draw_rect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![zh-cn_image_0000002194110921](figures/zh-cn_image_0000002194110921.png)


## 绘制圆角矩形

可以使用画笔或画刷在画布上进行圆角矩形的绘制。使用drawRoundRect()接口绘制圆角矩形。接口接受1个入参roundRect，对应为圆角矩形对象。

圆角矩形对象通过new drawing.RoundRect()接口构造，构造函数接受3个参数，分别为：

- common2D.Rect（矩形对象），圆角矩形是在该矩形的基础上切圆角形成。

- x轴上的圆角半径。

- y轴上的圆角半径。

此处以使用画刷绘制圆角矩形为例，简单示例代码如下：

<!-- @[arkts_graphics_draw_round_rect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

![zh-cn_image_0000002158584406](figures/zh-cn_image_0000002158584406.png)

<!--RP1-->
## 相关实例

针对Drawing(ArkTS)的开发，有以下相关实例可供参考：

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->