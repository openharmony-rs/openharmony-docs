# 自定义绘制修改器 (DrawModifier)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

## 概述

当某些组件本身的绘制内容不满足需求时，可使用组件自定义绘制功能，在原有组件基础上部分绘制、或者全部自行绘制，以达到预期效果。例如：独特的按钮形状、文字和图像混合的图标等。组件自定义绘制提供了自定义绘制修改器DrawModifier，来实现更自由的组件绘制。

## 使用DrawModifier接口

```ts
declare class DrawModifier {

  drawBehind?(drawContext: DrawContext): void;

  drawContent?(drawContext: DrawContext): void;

  drawFront?(drawContext: DrawContext): void;

  drawForeground?(drawContext: DrawContext): void;

  invalidate(): void;
}
```

DrawModifier可设置前景(drawForeground)、内容前景(drawFront)、内容(drawContent)和内容背景(drawBehind)的绘制方法，开发者需要重载这些方法，并通过[Canvas](arkts-drawing-customization-on-canvas.md)的接口进行自定义绘制。自定义绘制层级图如下所示。

![](figures/drawModifier.png)

DrawModifier还提供主动触发重绘的方法invalidate，该接口开发者无需也无法重载，调用会触发所绑定组件的重绘。

> **说明：**
>
> 每个DrawModifier实例只能设置到一个组件上，禁止进行重复设置。
>
> drawContent方法会替换组件原本的内容绘制函数。
>
> drawForeground方法从API version 20开始支持。
>
> NDK的自定义绘制能力和示例请参考[自定义绘制](./arkts-user-defined-draw.md)。

## 通过drawFront、drawContent、drawBehind进行自定义绘制

通过drawFront、drawContent、drawBehind接口，在内容前景、内容和内容背景三个层级上对Text组件进行了自定义绘制，从而按需改变组件的绘制效果。

<!-- @[drawFront_drawContent_drawBehind_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DrawModifier/entry/src/main/ets/pages/DrawFrontDrawContentDrawBehind.ets) -->

![drawModifier.gif](figures/drawModifier.gif)

## 通过drawForeground进行自定义绘制

通过drawForeground接口，在组件前景层级上对Column组件进行了自定义绘制，从而改变组件前景的绘制效果。

<!-- @[drawForeground_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DrawModifier/entry/src/main/ets/pages/DrawForeground.ets) -->

![drawForeground.png](figures/drawForeground.png)

## 调整自定义绘制Canvas的变换矩阵

从API version 12开始，通过重写DrawModifier中的[drawContent](../reference/apis-arkui/arkui-ts/ts-universal-attributes-draw-modifier.md#drawcontent)方法，可以替换组件原本的内容绘制函数。

通过[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)可以调整自定义绘制画布的变换矩阵。

> **说明：**
> 
> - [getTotalMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#gettotalmatrix12)获取的是用来记录绘制指令的临时canvas的变换矩阵。
> 
> - 如果开发者希望这个画布进行一个预期的变换，应该使用[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)而不是[setMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#setmatrix12)，因为setMatrix会覆盖原本真实canvas上存在的变换矩阵。

**ArkTS接口调用示例：**

<!-- @[Canvas_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DrawModifier/entry/src/main/ets/pages/Canvas.ets) -->

![drawModifier-canvas](./figures/drawModifier-canvas.png)