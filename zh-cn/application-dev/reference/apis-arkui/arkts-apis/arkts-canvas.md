# canvas

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) | 除支持通用属性外，还支持以下属性：设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持attributeModifier动态设置属性方法。需要搭配[CanvasRenderingContext2D](arkts-arkui-canvas-con.md)中的 [startImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#startimageanalyzer)和 [stopImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#stopimageanalyzer)一起使用。不能和overlay属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力，可通过 [ImageAnalyzerController.getImageAnalyzerSupportTypes](arkts-arkui-imageanalyzercontroller-c.md#getimageanalyzersupporttypes)接口查 询设备支持的分析类型。除支持通用事件外，还支持如下事件： |
| [CanvasGradient](arkts-arkui-canvasgradient-c.md) | OffscreenCanvas支持以下属性： |
| [CanvasPath](arkts-arkui-canvaspath-c.md) | 路径对象，提供基本的路径绘制方法。路径相关API的详细说明请参见CanvasRenderingContext2D中的描述。 |
| [CanvasRenderer](arkts-arkui-canvasrenderer-c.md) | CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制，绘制对象可以是形状、文本、图片等。 |
| [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) | CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制，绘制对象可以是形状、文本、图片等。 |
| [DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) | DrawingRenderingContext对象与Canvas组件绑定后，可在Canvas组件上进行绘制，绘制对象可以是形状、文本、图片等。 |
| [ImageBitmap](arkts-arkui-imagebitmap-c.md) | ImageBitmap对象可以存储canvas渲染的像素数据。从API version 11开始，当应用创建 [Worker线程](../../../arkts-utils/worker-introduction.md)，支持使用postMessage将ImageBitmap实例传到 Worker中进行绘制，并使用onmessage接收Worker线程发送的绘制结果进行显示。 |
| [ImageData](arkts-arkui-imagedata-c.md) | ImageData对象可以存储canvas渲染的像素数据。 |
| [OffscreenCanvas](arkts-arkui-offscreencanvas-c.md) | OffscreenCanvas组件用于绘制自定义图形。使用[Canvas](arkts-arkui-canvas-con.md)组件或 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) 对象时，渲染、动画和用户交互通常发生在应用程序的主线程上，与画布动画和渲染相关的计算可能会影响 应用程序性能。OffscreenCanvas提供了一个可以在屏幕外渲染的画布，这样可以在单独的线程中运行一些任务， 从而避免影响应用程序主线程性能。 |
| [OffscreenCanvasRenderingContext2D](arkts-arkui-offscreencanvasrenderingcontext2d-c.md) |  |
| [Path2D](arkts-arkui-path2d-c.md) | 路径对象，支持通过对象的接口进行路径的描述，并通过Canvas的stroke接口或者fill接口进行绘制。 |
| [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 用于配置CanvasRenderingContext2D对象的参数，包括是否开启抗锯齿。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CanvasInterface](arkts-arkui-canvasinterface-i.md) | 提供画布组件，用于自定义绘制图形。 |
| [CanvasParams](arkts-arkui-canvasparams-i.md) | 定义Canvas的具体配置参数。 |
| [CanvasPattern](arkts-arkui-canvaspattern-i.md) | 一个Object对象，使用 [createPattern](arkts-arkui-canvasrenderer-c.md#createpattern) 方法创建，通过指定图像和重复方式创建图片填充的模板。 |
| [OffscreenCanvasRenderingContext2DInterface](arkts-arkui-offscreencanvasrenderingcontext2dinterface-i.md) | 使用OffscreenCanvasRenderingContext2D在Canvas上进行离屏绘制，绘制对象可以是形状、文本、图片等。 离屏绘制是指将需要绘制的内容先绘制在缓存区，然后将其转换成图片，一次性绘制到Canvas上。 离屏绘制使用CPU进行绘制，绘制速度较慢，对绘制速度有要求的场景应避免使用离屏绘制。 |
| [RenderingContextOptions](arkts-arkui-renderingcontextoptions-i.md) | 定义渲染上下文的具体配置参数。 |
| [Size](arkts-arkui-size-i.md) | DrawingRenderingContext的尺寸信息。 |
| [TextMetrics](arkts-arkui-textmetrics-i.md) | 文本的尺寸信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CanvasDirection](arkts-arkui-canvasdirection-t.md) | 定义当前文本方向的类型。取值类型为下表类型中的并集。 |
| [CanvasFillRule](arkts-arkui-canvasfillrule-t.md) | 定义用于确定点是在路径内还是路径外的填充样式算法的类型。取值类型为下表类型中的并集。 |
| [CanvasLineCap](arkts-arkui-canvaslinecap-t.md) | 定义绘制每条线段端点的类型。取值类型为下表类型中的并集。 |
| [CanvasLineJoin](arkts-arkui-canvaslinejoin-t.md) | 定义长度不为0的两个连接部分（线段、圆弧和曲线）的类型。取值类型为下表类型中的并集。 |
| [CanvasTextAlign](arkts-arkui-canvastextalign-t.md) | 定义文本对齐方式的类型。取值类型为下表类型中的并集。 |
| [CanvasTextBaseline](arkts-arkui-canvastextbaseline-t.md) | 定义文本基线类型。取值类型为下表类型中的并集。 |
| [DrawingCanvas](arkts-arkui-drawingcanvas-t.md) | 可用于向DrawingRenderingContext上绘制内容的画布对象。 |
| [FrameNode](arkts-arkui-framenode-t.md) | Import the frame node type object for Canvas. |
| [ImageSmoothingQuality](arkts-arkui-imagesmoothingquality-t.md) | 定义图片平滑度类型。取值类型为下表类型中的并集。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [Canvas](arkts-arkui-canvas-con.md) | 提供画布组件，用于自定义绘制图形。 |
| [CanvasInstance](arkts-arkui-canvas-con.md#canvasinstance) | 提供画布组件，用于自定义绘制图形。 |
