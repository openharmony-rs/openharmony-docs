# Drawing Geometric Shapes (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->


## Overview

Currently, the following geometric shapes can be drawn:

- Point

- Arc

- Circle

- Path

- Region

- Box

- Rounded rectangle

Most geometric shapes can be drawn using a brush or a paintbrush. Points can be drawn only using a brush.


## Available APIs

The following table describes the APIs commonly used for drawing geometric shapes. For details about the APIs and parameters, see [drawing.Canvas](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md).

| API| Description|
| -------- | -------- |
| drawPoint(x: number, y: number): void | Draws a point.|
| drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void | Draws an arc.|
| drawCircle(x: number, y: number, radius: number): void | Draws a circle.|
| drawPath(path: Path): void | Draws a path.|
| drawRegion(region: Region): void | Draws a region.|
| drawRect(left: number, top: number, right: number, bottom: number): void | Draws a rectangle.|
| drawRoundRect(roundRect: RoundRect): void | Draws a rounded rectangle.|


## Drawing Points

Points can be drawn on the canvas only using a brush. You can use the drawPoint() API to draw a point. A point has two parameters, which are the x coordinate and y coordinate of the point to be drawn.

A simple example is as follows:

<!-- @[arkts_graphics_draw_point](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Set the brush.
let pen = new drawing.Pen();
// Set the color
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the line width.
pen.setStrokeWidth(40);
// Set the stroke effect of the paint.
canvas.attachPen(pen);
// Draw five points.
canvas.drawPoint(VALUE_200, VALUE_200);
canvas.drawPoint(VALUE_400, VALUE_400);
canvas.drawPoint(VALUE_600, VALUE_600);
canvas.drawPoint(VALUE_800, VALUE_800);
canvas.drawPoint(VALUE_1000, VALUE_1000);
// Remove the stroke effect.
canvas.detachPen();
```

The effect is as follows:

![Screenshot_20241129174520171](figures/Screenshot_20241129174520171.jpg)


## Drawing an Arc

You can use a paint or brush to draw an arc on the canvas. The drawArc() API is used to draw an arc.

Drawing an arc requires a rectangle ([common2D.Rect](../reference/apis-arkgraphics2d/js-apis-graphics-common2D.md#rect)) and two parameters, which indicate the start angle (startAngle) and sweep angle (sweepAngle) of the arc.

The following is a simple example of drawing an arc using a paint:

<!-- @[arkts_graphics_draw_arc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Create a pen.
let pen = new drawing.Pen();
// Set the color
pen.setColor({
  alpha: 0xFF,
  red: 0xFF,
  green: 0x00,
  blue: 0x00
});
// Set the line width.
pen.setStrokeWidth(20);
// Set the stroke effect of the paint.
canvas.attachPen(pen);
// Create a rectangle.
const rect: common2D.Rect = {
  left: VALUE_100,
  top: VALUE_200,
  right: VALUE_1000,
  bottom: VALUE_600
};
// Draw a rectangle.
canvas.drawArc(rect, 0, 180);
// Remove the stroke effect.
canvas.detachPen();
```

The effect is as follows:

![image_0000002194025289](figures/image_0000002194025289.png)


## Drawing a Circle

You can use a paint or brush to draw a circle on the canvas. The drawCircle() API is used to draw a circle.

Drawing a circle requires the x and y coordinates of the circle center and the radius of the circle.

The following example uses a brush to draw a circle.
<!-- @[arkts_graphics_draw_circle](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Create a pen.
let pen = new drawing.Pen();
// Set the color
pen.setColor({
  alpha: 0xFF,
  red: 0xFF,
  green: 0x00,
  blue: 0x00
});
// Set the line width.
pen.setStrokeWidth(20);
// Set the stroke effect of the paint.
canvas.attachPen(pen);
// Draw a circle.
canvas.drawCircle(VALUE_630, VALUE_630, VALUE_500);
// Remove the stroke effect.
canvas.detachPen();
```

The effect is as follows:

![Screenshot_20241129172555673](figures/Screenshot_20241129172555673.jpg)


## Draw a route.

You can use a brush or a brush to draw a path on the canvas. A path can be used to draw a straight line, arc, or Bezier curve. You can also combine paths to form other complex shapes.

The following describes the APIs and implementation of drawing a path. For details about the usage and parameters, see [Path](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Path.md). Common APIs are as follows:

1. new drawing.Path() is used to create a path object.

2. moveTo() is used to set the start point of a custom path.

3. lineTo() is used to add a line segment from the start point or the last point of the path (if the path is empty, the default value is (0,0)) to the target point.

The following example uses a brush and a brush to draw a five-pointed star.

<!-- @[arkts_graphics_draw_path](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
let height_ = VALUE_1800;
let width_ = VALUE_1800;
let len = height_ / 4;
let aX = width_ / 3;
let aY = height_ / 6;
let dX = aX - len * Math.sin(18.0);
let dY = aY + len * Math.cos(18.0);
let cX = aX + len * Math.sin(18.0);
let cY = dY;
let bX = aX + (len / 2.0);
let bY = aY + Math.sqrt((cX - dX) * (cX - dX) + (len / 2.0) * (len / 2.0));
let eX = aX - (len / 2.0);
let eY = bY;

// Create a path object and use the APIs to construct a pentagram.
let path = new drawing.Path();
// Specify the start point of the path.
path.moveTo(aX, aY);
// Draw a line segment from the last point of a path to the target point.
path.lineTo(bX, bY);
path.lineTo(cX, cY);
path.lineTo(dX, dY);
path.lineTo(eX, eY);
// Close the path. Now the path is drawn.
path.close();

// Create a paint object.
let pen = new drawing.Pen();
// Enable anti-aliasing.
pen.setAntiAlias(true);
// Set the stroke color.
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the line width.
pen.setStrokeWidth(10.0);
// Set the stroke effect of the paint.
canvas.attachPen(pen);
// Create a brush.
let brush = new drawing.Brush();
// Set the fill color.
brush.setColor(0xFF, 0x00, 0xFF, 0x00);
// Set the fill effect of the brush.
canvas.attachBrush(brush);
// Draw the path.
canvas.drawPath(path);
// Remove the fill effect.
canvas.detachBrush();
// Remove the stroke effect.
canvas.detachPen();
```

The effect is as follows:

![Screenshot_20241129164326302](figures/Screenshot_20241129164326302.jpg)


## Viewport rectangle

A region is not a specific shape. You can set it to a specified rectangle or path, or perform combination operations on two regions. You can use a paint or brush to draw a region. For details about the APIs, see [Region](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Region.md).

Currently, a rectangle region and a path region can be set by using the setRect() and setPath() APIs, respectively.

The following uses a brush to draw a combined region of rectangles as an example:

<!-- @[arkts_graphics_draw_region](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Create a brush.
let brush = new drawing.Brush();
// Set the color
brush.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the brush filling effect.
canvas.attachBrush(brush);
// Create region1 in the upper left corner.
let region1 = new drawing.Region();
region1.setRect(VALUE_100, VALUE_100, VALUE_600, VALUE_600);
// Create region2 in the lower right corner.
let region2 = new drawing.Region();
region2.setRect(VALUE_300, VALUE_300, VALUE_900, VALUE_900);
// Combine the two regions in XOR mode.
region1.op(region2, drawing.RegionOp.XOR);
// Draw the regions.
canvas.drawRegion(region1);
// Remove the fill effect.
canvas.detachBrush();
```

The effect is as follows:

![Screenshot_20241206112505234](figures/Screenshot_20241206112505234.jpg)


## Draws a rectangle.

You can use a brush or pen to draw a rectangle on the canvas. Use the drawRect() API to draw a rectangle. The API needs to pass four floating points, which indicate the coordinates of the left, top, right, and bottom of the rectangle. The four coordinates form a rectangle.

The following is a simple example of drawing a rectangle using a brush:

<!-- @[arkts_graphics_draw_rect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Create a brush.
let brush = new drawing.Brush();
// Set the color
brush.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the brush filling effect.
canvas.attachBrush(brush);
// Draw a rectangle.
canvas.drawRect(VALUE_200, VALUE_200, VALUE_1000, VALUE_700);
// Remove the fill effect.
canvas.detachBrush();
```

The effect is as follows:

![image_0000002194110921](figures/image_0000002194110921.png)


## Drawing a Rounded Rectangle

You can use a brush or pen to draw a rounded rectangle on the canvas. Use the drawRoundRect() API to draw a rounded rectangle. The API accepts one input parameter roundRect, which is the rounded rectangle object.

The rounded rectangle object is constructed using new drawing.RoundRect() API. The constructor accepts three parameters:

- common2D.Rect (rectangle object). A rounded rectangle is formed by cutting corners on the rectangle.

- Radius of the rounded corner on the x axis.

- Radius of the rounded corner on the y axis.

The following is a simple example of drawing a rounded rectangle using a brush:

<!-- @[arkts_graphics_draw_round_rect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ShapeDrawing.ets) -->

``` TypeScript
// Create a brush.
let brush = new drawing.Brush();
// Set the color
brush.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the brush filling effect.
canvas.attachBrush(brush);
// Create a rectangle object.
let rect: common2D.Rect = {
  left: VALUE_200,
  top: VALUE_200,
  right: VALUE_1000,
  bottom: VALUE_700
};
console.info('rect:', rect.right);
// Create a rounded rectangle object.
let rrect = new drawing.RoundRect(rect, 30, 30);
// Draw a rounded rectangle.
canvas.drawRoundRect(rrect);
// Remove the filling effect.
canvas.detachBrush();
```

The effect is as follows:

![image_0000002158584406](figures/image_0000002158584406.png)

<!--RP1-->
## Samples

The following samples are available for Drawing (ArkTS) development:

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->
