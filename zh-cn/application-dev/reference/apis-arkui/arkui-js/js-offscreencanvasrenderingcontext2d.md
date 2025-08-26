# OffscreenCanvasRenderingContext2D对象
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

>  **说明：**
>  从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


使用OffscreenCanvasRenderingContext2D在[OffscreenCanvas对象](js-components-canvas-offscreencanvas.md)上进行绘制，绘制对象可以是矩形、文本、图片等。


## 属性

除支持与[CanvasRenderingContext2D对象](js-components-canvas-canvasrenderingcontext2d.md)相同的属性外，还支持如下属性：

| 属性     | 类型     | 描述                                       |
| ------ | ------ | ---------------------------------------- |
| filter | string | 设置图像的滤镜。<br/>支持的滤镜效果如下：<br/>-&nbsp;blur：给图像设置高斯模糊。<br/>-&nbsp;brightness：给图片应用一种线性乘法，使其看起来更亮或更暗。<br/>-&nbsp;contrast：调整图像的对比度。<br/>-&nbsp;drop-shadow：给图像设置一个阴影效果。<br/>-&nbsp;grayscale：将图像转换为灰度图像。<br/>-&nbsp;hue-rotate：给图像应用色相旋转。<br/>-&nbsp;invert：反转输入图像。<br/>-&nbsp;opacity：转化图像的透明程度。<br/>-&nbsp;saturate：转换图像饱和度。<br/>-&nbsp;sepia：将图像转换为深褐色。 |

**示例：** 
```html
<!-- xxx.hml -->
<div style="width: 500px; height: 500px;">
  <canvas ref="canvasId" style="width: 500px; height: 500px; background-color: #ffff00;"></canvas>
</div>
```

```js
// xxx.js
export default {
  onShow(){
    var ctx = this.$refs.canvasId.getContext('2d');
    var offscreen = new OffscreenCanvas(360, 500);
    var offCanvas2 = offscreen.getContext("2d");
    var img = new Image();
    img.src = 'common/images/flower.jpg';
    offCanvas2.drawImage(img, 0, 0, 100, 100);
    offCanvas2.filter = 'blur(5px)';
    offCanvas2.drawImage(img, 100, 0, 100, 100);

    offCanvas2.filter = 'grayscale(50%)';
    offCanvas2.drawImage(img, 200, 0, 100, 100);

    offCanvas2.filter = 'hue-rotate(90deg)';
    offCanvas2.drawImage(img, 0, 100, 100, 100);

    offCanvas2.filter = 'invert(100%)';
    offCanvas2.drawImage(img, 100, 100, 100, 100);

    offCanvas2.filter = 'drop-shadow(8px 8px 10px green)';
    offCanvas2.drawImage(img, 200, 100, 100, 100);

    offCanvas2.filter = 'brightness(0.4)';
    offCanvas2.drawImage(img, 0, 200, 100, 100);

    offCanvas2.filter = 'opacity(25%)';
    offCanvas2.drawImage(img, 100, 200, 100, 100);

    offCanvas2.filter = 'saturate(30%)';
    offCanvas2.drawImage(img, 200, 200, 100, 100);

    offCanvas2.filter = 'sepia(60%)';
    offCanvas2.drawImage(img, 0, 300, 100, 100);

    offCanvas2.filter = 'contrast(200%)';
    offCanvas2.drawImage(img, 100, 300, 100, 100);
    var bitmap = offscreen.transferToImageBitmap();
    ctx.transferFromImageBitmap(bitmap);
  }
}
```

## 方法

除支持与CanvasRenderingContext2D对象相同的方法外，还支持如下方法：


### isPointInPath

isPointInPath(path?: Path2D, x: number, y: number): boolean

判断指定点是否在路径的区域内。

**参数：** 
| 参数名  | 参数类型   | 必填   | 描述                            |
| ---- | ------ | ---- | ----------------------------- |
| path | Path2D | 否    | 可选对象，指定用来判断的路径。若没有设置，则使用当前路径。 |
| x    | number | 是    | 待判断点的x轴坐标。                    |
| y    | number | 是    | 待判断点的y轴坐标。                    |

**返回值：** 
| 类型      | 说明            |
| ------- | ------------- |
| boolean | 指定点是否在路径的区域内。返回true时，指定点在路径区域内。返回false时，指定点不在路径路径区域内。 |

**示例：** 
```html
<!-- xxx.hml -->
<div class="container" style="width: 500px; height: 500px;">
    <text class="textsize">In path:{{textValue}}</text>
    <canvas ref="canvas" style="width: 500px; height: 500px; background-color: #ffff00;"></canvas>
</div>
```

```css
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    background-color: #F1F3F5;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
}

canvas {
    width: 600px;
    height: 600px;
    background-color: #fdfdfd;
    border: none;
}

.textsize {
    font-size: 40px;
}
```

```js
// xxx.js
export default {
  data: {
    textValue: 0
  },
  onShow(){
    var canvas = this.$refs.canvas.getContext('2d');
    var offscreen = new OffscreenCanvas(500,500);
    var offscreenCanvasCtx = offscreen.getContext("2d");

    offscreenCanvasCtx.rect(10, 10, 100, 100);
    offscreenCanvasCtx.fill();
    this.textValue = offscreenCanvasCtx.isPointInPath(30, 70);

    var bitmap = offscreen.transferToImageBitmap();
    canvas.transferFromImageBitmap(bitmap);
  }
}
```

![zh-cn_image_0000001224354967](figures/zh-cn_image_0000001224354967.png)

### isPointInStroke

isPointInStroke(path?: Path2D, x: number, y: number): boolean

判断指定点是否在路径的边缘线上。

**参数：** 
| 参数名  | 参数类型   | 必填   | 描述                            |
| ---- | ------ | ---- | ----------------------------- |
| path | Path2D | 否    | 可选对象，指定用来判断的路径。若没有设置，则使用当前路径。 |
| x    | number | 是    | 待判断点的x轴坐标。                    |
| y    | number | 是    | 待判断点的y轴坐标。                    |

**返回值：** 
| 类型      | 说明            |
| ------- | ------------- |
| boolean | 指定点是否在路径的区域内。 |

**示例：** 
```html
<!-- xxx.hml -->
<div class="container" style="width: 500px; height: 500px;">
    <text class="textsize">In stroke:{{textValue}}</text>
    <canvas ref="canvas" style="width: 500px; height: 500px; background-color: #ffff00;"></canvas>
</div>
```

```css
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    background-color: #F1F3F5;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
}

canvas {
    width: 600px;
    height: 600px;
    background-color: #fdfdfd;
    border: none;
}

.textsize {
    font-size: 40px;
}
```

```js
// xxx.js
export default {
  data: {
    textValue: 0
  },
  onShow(){
    var canvas = this.$refs.canvas.getContext('2d');
    var offscreen = new OffscreenCanvas(500,500);
    var offscreenCanvasCtx = offscreen.getContext("2d");

    offscreenCanvasCtx.rect(10, 10, 100, 100);
    offscreenCanvasCtx.stroke();
    this.textValue = offscreenCanvasCtx.isPointInStroke(50, 10);

    var bitmap = offscreen.transferToImageBitmap();
    canvas.transferFromImageBitmap(bitmap);
  }
}
```

![zh-cn_image_0000001178875308](figures/zh-cn_image_0000001178875308.png)

### resetTransform

resetTransform(): void

**示例：** 
```html
<!-- xxx.hml -->
<div class="container" style="width: 500px; height: 500px;">
    <text class="textsize">In path:{{textValue}}</text>
    <canvas ref="canvas" style="width: 500px; height: 500px; background-color: #ffff00;"></canvas>
</div>
```

```css
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    background-color: #F1F3F5;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
}

canvas {
    width: 600px;
    height: 600px;
    background-color: #fdfdfd;
    border: none;
}

.textsize {
    font-size: 40px;
}
```

```js
// xxx.js
export default {
  data:{
   textValue:0
  },
  onShow(){
   var canvas = this.$refs.canvas.getContext('2d');
   var offscreen = new OffscreenCanvas(500,500);
   var offscreenCanvasCtx = offscreen.getContext("2d");

   offscreenCanvasCtx.transform(1, 0, 1.7, 1, 0, 0);
   offscreenCanvasCtx.fillStyle = '#a9a9a9';
   offscreenCanvasCtx.fillRect(40, 40, 50, 20);
   offscreenCanvasCtx.fillRect(40, 90, 50, 20);

   // Non-skewed rectangles
   offscreenCanvasCtx.resetTransform();
   offscreenCanvasCtx.fillStyle = '#ff0000';
   offscreenCanvasCtx.fillRect(40, 40, 50, 20);
   offscreenCanvasCtx.fillRect(40, 90, 50, 20);

   var bitmap = offscreen.transferToImageBitmap();
   canvas.transferFromImageBitmap(bitmap);
  } 
}
```

![zh-cn_image_0000001179035242](figures/zh-cn_image_0000001179035242.png)