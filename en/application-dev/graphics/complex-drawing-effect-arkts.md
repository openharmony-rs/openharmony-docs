# Complex Drawing Effects (ArkTS)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

In addition to the basic drawing effects such as filling colors, stroke colors, and some style settings, you can also use brushes and pens to implement more complex drawing effects. For example:


- Blend mode.

- Path effects, such as dashed lines

- Shader effects, such as linear gradient and radial gradient

- Filter effects, such as blur


## Blend Modes

Blend modes can be used for pens or brushes. They define how source pixels (content to be drawn) are combined with destination pixels (content that already exists on the canvas).

You can use the setBlendMode() API to apply a blend mode to a brush or pen. This API requires a BlendMode parameter, which is the type of the blend mode. For details, see [BlendMode](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-e.md#blendmode).

The following figure shows a key example and effect.

<!-- @[arkts_graphics_draw_import_ui_and_graphics2d](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
import { DrawContext, FrameNode, NodeController, RenderNode, UIContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';
```

<!-- @[arkts_graphics_draw_render_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
function drawRenderNode(canvas: drawing.Canvas) {
  canvas.saveLayer(null, null);
  const brushCircle = new drawing.Brush();
  const colorCircle: common2D.Color = {alpha: 255, red: 0, green: 0, blue: 255};
  brushCircle.setColor(colorCircle);
  canvas.attachBrush(brushCircle);
  canvas.drawCircle(500, 500, 200);
  const brush = new drawing.Brush();
  // Set the dash pattern.
  brush.setBlendMode(drawing.BlendMode.SRC_IN);
  canvas.saveLayer(null, brush);

  const brushRect = new drawing.Brush();
  const colorRect: common2D.Color = {alpha: 255, red: 255, green: 255, blue: 0};
  brushRect.setColor(colorRect);
  canvas.attachBrush(brushRect);
  const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
  canvas.drawRect(rect);
  canvas.restore();
  canvas.restore();
  canvas.detachBrush();
}
```

![image_BlendMode_SrcIn.png](figures/image_BlendMode_SrcIn.png)


## Path Effect

The dash pattern is used only for brushes.

You can use the createDashPathEffect() API to set the dash pattern. This API accepts two parameters:

- intervals: an array of floating-point numbers, indicating the intervals of dashes or dots.

- phase: a floating-point number, indicating the offset in the intervals array, that is, the position in the array where the dash or dot effect starts to be applied.

The following shows how to draw a rectangle with a dash pattern. The key code and effect are as follows:

<!-- @[arkts_graphics_draw_path_effect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
// Create a pen.
let pen = new drawing.Pen();
// Set the line width.
pen.setStrokeWidth(10.0);
// Set the color
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the dash pattern. Here, the real line length is 10 px, the interval is 5 px, the real line length is 2 px, and the interval is 5 px. Repeat the pattern.
let intervals = [10, 5, 2, 5];
// Set the dash pattern.
let effect = drawing.PathEffect.createDashPathEffect(intervals, 0);
pen.setPathEffect(effect);
// Set the brush stroke effect.
canvas.attachPen(pen);
// Create a rectangle.
let rect: common2D.Rect = {
  left: VALUE_200,
  top: VALUE_200,
  right: VALUE_1000,
  bottom: VALUE_700
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the stroke effect.
canvas.detachPen();
```

| Original image| Image after the dashed line effect is set|
| -------- | -------- |
| ![Screenshot_20241130160231398](figures/Screenshot_20241130160231398.jpg) | ![Screenshot_20241130160433593](figures/Screenshot_20241130160433593.jpg) |


## Shader Effect

The shader effect is implemented based on the brush or paint brush. You can use the setShaderEffect() API to set the shader effect of the brush or paint brush. Currently, different shader effects are supported, such as linear gradient shader effect, radial gradient shader effect, and sector gradient shader effect.


For details about the shader APIs and parameters, see [ShaderEffect](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-ShaderEffect.md).


### Linear Gradient Shader Effect

You can use the createLinearGradient() API to create the linear gradient shader effect. The API accepts six parameters, including the start point, end point, color array, tiling mode, relative position array, and matrix object.

- The start point and end point are used to determine the gradient direction.

- The color array is used to store the colors used for gradient.

- The relative position array is used to determine the relative position of each color in the gradient. If the relative position is empty, the colors are evenly distributed between the start point and end point.

- The matrix object is used to perform matrix transformation on the shader. The default value is null, indicating the unit matrix.

- The tiling mode is used to determine how to continue the gradient effect beyond the gradient area. The tiling mode is classified into the following types:
  - CLAMP: When an image exceeds its original boundary, the edge color is copied.
  - REPEAT: The image is repeated in the horizontal and vertical directions.
  - MIRROR: The image is repeated in the horizontal and vertical directions, and mirrored images are alternately used between adjacent images.
  - DECAL: Only the original domain is drawn, and transparent black is returned in other places.

The following figure shows how to draw a rectangle and use the brush to set the linear gradient shader effect.

<!-- @[arkts_graphics_draw_linear_gradient](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
let startPt: common2D.Point = { x: VALUE_100, y: VALUE_100 };
let endPt: common2D.Point = { x: VALUE_900, y: VALUE_900 };
let colors = [0xFFFFFF00, 0xFFFF0000, 0xFF0000FF];
// Create a linear gradient shader.
let shaderEffect = drawing.ShaderEffect.createLinearGradient(startPt, endPt, colors, drawing.TileMode.CLAMP);
// Create a brush.
let brush = new drawing.Brush();
// Set the linear shader.
brush.setShaderEffect(shaderEffect);
// Set the brush fill effect.
canvas.attachBrush(brush);
let rect: common2D.Rect = {
  left: VALUE_100,
  top: VALUE_100,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the fill effect.
canvas.detachBrush();
```

![image_0000002158744106](figures/image_0000002158744106.png)


### Radial Gradient Shader

You can use the createRadialGradient() API to create a radial gradient shader. The API accepts six parameters: centerPt (coordinates of the center point), radius (radius), colors (color array), TileMode (tiling mode), pos (relative position array), and matrix (matrix object).

The implementation method is similar to that of the linear gradient shader. The difference is that the radial gradient shader starts from the center point and expands outward.

The following uses drawing a rectangle and setting the radial gradient shader effect using a brush as an example. The key example and effect are as follows:

<!-- @[arkts_graphics_draw_path_gradient](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
let centerPt: common2D.Point = { x: VALUE_500, y: VALUE_500 };
let colors = [0xFFFF0000, 0xFF00FF00, 0xFF0000FF];
// Create a radial gradient shader.
let shaderEffect = drawing.ShaderEffect.createRadialGradient(centerPt, VALUE_600, colors, drawing.TileMode.CLAMP);
// Create a brush.
let brush = new drawing.Brush();
// Set the radial gradient shader.
brush.setShaderEffect(shaderEffect);
// Set the brush fill effect.
canvas.attachBrush(brush);
let rect: common2D.Rect = {
  left: VALUE_100,
  top: VALUE_100,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the fill effect.
canvas.detachBrush();
```

![Screenshot_20241130164939281](figures/Screenshot_20241130164939281.jpg)


### Sweep Gradient Shader

You can use the createSweepGradient() API to create a sweep gradient shader. The API accepts seven parameters: centerPt (coordinates of the center point), colors (color array), TileMode (tiling mode), startAngle (start angle of the sweep gradient), endAngle (end angle of the sweep gradient), pos (relative position array), and matrix (matrix object).

The implementation method is similar to that of the linear gradient shader. The difference is that the sweep gradient shader changes gradually during rotation around the center point.

The following uses drawing a rectangle and setting the sweep gradient shader for the brush as an example. The key code and effect are as follows:

<!-- @[arkts_graphics_draw_sector_gradient](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
let centerPt: common2D.Point = { x: VALUE_500, y: VALUE_500 };
let colors = [0xFF00FFFF, 0xFFFF00FF, 0xFFFFFF00];
// Create a sweep gradient shader.
let shaderEffect = drawing.ShaderEffect.createSweepGradient(centerPt, colors, drawing.TileMode.CLAMP, 0, 360);
// Create a brush.
let brush = new drawing.Brush();
// Set the sweep gradient shader.
brush.setShaderEffect(shaderEffect);
// Set the brush fill effect.
canvas.attachBrush(brush);
let rect: common2D.Rect = {
  left: VALUE_100,
  top: VALUE_100,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the fill effect.
canvas.detachBrush();
```

![Screenshot_20241130165741720](figures/Screenshot_20241130165741720.jpg)


## Filter Effect

The filter effect can be implemented based on the brush or pen. Currently, different filter effects are supported, such as image filter, color filter, and mask filter.

For details about the APIs and parameters related to filters, see [ImageFilter](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-ImageFilter.md).


### Color Filter Effect

The color filter can be implemented based on the pen or brush. For details about the APIs and parameters related to the color filter, see [ColorFilter](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-ColorFilter.md).

Currently, the following color filters can be implemented:

- Color filter with a blending mode.

- Color filter with a 5x4 color matrix.

- Color filter that applies the SRGB gamma curve to the RGB color channel.

- Color filter that applies the RGB color channel to the SRGB gamma curve.

- Color filter that multiplies the input luminance value by the transparency channel and sets the red, green, and blue channels to zero.

- Color filter consisting of two color filters.

The color filter with a 5x4 color matrix is used as an example.

You can use the createMatrixColorFilter() API to create a color filter with a 5x4 color matrix. The API accepts one parameter, which indicates the color matrix. The value is a floating-point array of 20 characters. The array format is as follows:

[ a0, a1, a2, a3, a4 ]

[ b0, b1, b2, b3, b4 ]

[ c0, c1, c2, c3, c4 ]

[ d0, d1, d2, d3, d4 ]

For each original pixel color value (R, G, B, A), the formula for calculating the transformed color value (R', G', B', A') is as follows:

R' = a0\*R + a1\*G + a2\*B + a3\*A + a4

G' = b0\*R + b1\*G + b2\*B + b3\*A + b4

B' = c0\*R + c1\*G + c2\*B + c3\*A + c4

A' = d0\*R + d1\*G + d2\*B + d3\*A + d4

The following example shows how to draw a rectangle and use a brush to set a color filter effect with a 5x4 color matrix. The key example and effect diagram are as follows:

<!-- @[arkts_graphics_draw_color_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
// Create a brush.
let brush = new drawing.Brush();
// Set the color
brush.setColor(0xFF, 0xFF, 0x00, 0x00);
// Set the color matrix.
let matrix: number[] = [
  1, 0, 0, 0, 0,
  0, 1, 0, 0, 0,
  0, 0, 0.5, 0.5, 0,
  0, 0, 0.5, 0.5, 0
];
// Create a color filter with a 5x4 color matrix.
let filter = drawing.ColorFilter.createMatrixColorFilter(matrix);
// Set the color filter.
brush.setColorFilter(filter);
// Set the brush filling effect.
canvas.attachBrush(brush);
let rect: common2D.Rect = {
  left: VALUE_300,
  top: VALUE_300,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the fill effect.
canvas.detachBrush();
```

| Original image| Image effect after the color filter with a 5x4 color matrix is set|
| -------- | -------- |
| ![Screenshot_20241130173415925](figures/Screenshot_20241130173415925.jpg) | ![Screenshot_20241130173354704](figures/Screenshot_20241130173354704.jpg) |


### Image Filter Effect

Image filters can be implemented based on brushes or pens. For details about the APIs and parameters of image filters, see [ImageFilter](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-ImageFilter.md).

Currently, only the following two types of image filters are supported:

- Image filter based on the color filter.
  You can use the createFromColorFilter() API to implement this. The API accepts two parameters: colorFilter and imageFilter. The color filter effect is superimposed on the image filter imageFilter. imageFilter can be empty. If imageFilter is empty, only the color filter effect is added.

- Image filter with the blur effect.
  You can use the createBlurImageFilter() API to implement this. The API accepts four parameters: sigmaX, sigmaY, cTileMode, and imageFilter. sigmaX and sigmaY indicate the standard deviation of the blur, cTileMode indicates the tile mode, and imageFilter indicates the input image filter.

  The final effect is to perform blurring processing on the input image filter imageFilter. That is, the filter effect can be superimposed. imageFilter can be empty. If imageFilter is empty, only the blur effect is added.

The following figure shows how to draw a rectangle and add an image filter with the blur effect using a paint brush.

<!-- @[arkts_graphics_draw_image_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
// Set the paint brush.
let pen = new drawing.Pen();
// Set the line width.
pen.setStrokeWidth(10.0);
// Set the color
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Create an image filter with the blur effect.
let filter = drawing.ImageFilter.createBlurImageFilter(20, 20, drawing.TileMode.CLAMP);
// Set the image filter.
pen.setImageFilter(filter);
// Set the paint brush stroke effect.
canvas.attachPen(pen);
let rect: common2D.Rect = {
  left: VALUE_300,
  top: VALUE_300,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the stroke effect.
canvas.detachPen();
```

| Original image| Image after the blur effect is set|
| -------- | -------- |
| ![Screenshot_20241130170911500](figures/Screenshot_20241130170911500.jpg) | ![Screenshot_20241130170826458](figures/Screenshot_20241130170826458.jpg) |


### Mask Filter

The mask filter blurs only the transparency and shape edges. Compared with the image filter, the mask filter is less costly.

The mask filter can be implemented based on the brush or paintbrush. For details about the APIs and parameters of the mask filter, see [MaskFilter](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-MaskFilter.md).

You can use the createBlurMaskFilter() API to create a mask filter with the blur effect. This API accepts two parameters:

- blurType: blur type to be applied. For details, see [BlurType](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-e.md#blurtype12).

- sigma: standard deviation of the Gaussian blur to be applied. The value must be greater than 0.

The following uses a rectangle as an example to describe how to set the mask filter effect using a brush. The key code and effect are as follows:

<!-- @[arkts_graphics_draw_mask_filter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/ComplexEffect.ets) -->

``` TypeScript
// Create a pen.
let pen = new drawing.Pen();
// Set the line width.
pen.setStrokeWidth(10.0);
// Set the color
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Create a mask filter with the blur effect.
let filter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.NORMAL, 20);
// Set the blur effect.
pen.setMaskFilter(filter);
// Set the brush stroke effect.
canvas.attachPen(pen);
let rect: common2D.Rect = {
  left: VALUE_300,
  top: VALUE_300,
  right: VALUE_900,
  bottom: VALUE_900
};
// Draw the rectangle.
canvas.drawRect(rect);
// Remove the stroke effect.
canvas.detachPen();
```

| Original image| Image after the blur effect is set|
| -------- | -------- |
| ![Screenshot_20241130170911500](figures/Screenshot_20241130170911500.jpg) | ![Screenshot_20241130170826458](figures/Screenshot_20241130170826458.jpg) |

<!--RP1-->
## Samples

The following samples are available for you to develop Drawing (ArkTS) applications:

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->
