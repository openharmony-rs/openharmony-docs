# Canvas

提供画布组件，用于自定义绘制图形。


## Canvas

```TypeScript
Canvas(context?: CanvasRenderingContext2D | DrawingRenderingContext)
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasInterface-(context?: CanvasRenderingContext2D | DrawingRenderingContext): CanvasAttribute--><!--Device-CanvasInterface-(context?: CanvasRenderingContext2D | DrawingRenderingContext): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) \| DrawingRenderingContext | 否 | CanvasRenderingContext2D：不支持多个Canvas共用一个CanvasRenderingContext2D对象， 具体描述见[CanvasRenderingContext2D](docroot://reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md) 对象。DrawingRenderingContext：不支持多个Canvas共用一个DrawingRenderingContext对象， 具体描述见[DrawingRenderingContext](docroot://reference/apis-arkui/arkui-ts/ts-drawingrenderingcontext.md) 对象。 <br>异常值null和undefined按未设置context处理。  |

## Canvas

```TypeScript
Canvas(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions)
```

创建Canvas组件，支持设置CanvasRenderingContext2D对象或DrawingRenderingContext对象，支持设置AI分析选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasInterface-(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions): CanvasAttribute--><!--Device-CanvasInterface-(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) \| DrawingRenderingContext | 是 | CanvasRenderingContext2D：不支持多个Canvas共用一个CanvasRenderingContext2D对象， 具体描述见[CanvasRenderingContext2D](docroot://reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md) 对象。DrawingRenderingContext：不支持多个Canvas共用一个DrawingRenderingContext对象， 具体描述见[DrawingRenderingContext](docroot://reference/apis-arkui/arkui-ts/ts-drawingrenderingcontext.md) 对象。 <br>异常值null和undefined按未设置context处理。  |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 <br>异常值null和undefined按 [ImageAIOptions](docroot://reference/apis-arkui/arkui-ts/ts-image-common.md#imageaioptions12) 的默认值处理，默认取值为{ type: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT], aiController: new ImageAnalyzerController() }，即开启主体识别和文字识别功能。  |

## Canvas

```TypeScript
Canvas(params: CanvasParams)
```

使用CanvasParams创建不缓存指令的Canvas组件。创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。

> **说明：**  
>  
> - 使用本接口创建的Canvas组件将在onReady回调的入参中返回一个  
> [DrawingRenderingContext](docroot://reference/apis-arkui/arkui-ts/ts-drawingrenderingcontext.md)  
> 对象，可用于在该Canvas组件上进行绘制。  
>  
> - 使用这个接口创建的Canvas组件在组件不可见时将不响应绘制指令。  
>  
> - 不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置  
> [visibility](docroot://reference/apis-arkui/arkui-ts/ts-universal-attributes-visibility.md#visibility)  
> 属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasInterface-(params: CanvasParams): CanvasAttribute--><!--Device-CanvasInterface-(params: CanvasParams): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [CanvasParams](arkts-arkui-canvasparams-i.md) | 是 | Canvas组件的构造参数。  |

## 汇总

- [CanvasParams](arkts-arkui-canvas-canvasparams-i.md)
- [CanvasPattern](arkts-arkui-canvas-canvaspattern-i.md)
- [RenderingContextOptions](arkts-arkui-canvas-renderingcontextoptions-i.md)
- [Size](arkts-arkui-canvas-size-i.md)
- [TextMetrics](arkts-arkui-canvas-textmetrics-i.md)
- [CanvasDirection](arkts-arkui-canvas-canvasdirection-t.md)
- [CanvasFillRule](arkts-arkui-canvas-canvasfillrule-t.md)
- [CanvasLineCap](arkts-arkui-canvas-canvaslinecap-t.md)
- [CanvasLineJoin](arkts-arkui-canvas-canvaslinejoin-t.md)
- [CanvasTextAlign](arkts-arkui-canvas-canvastextalign-t.md)
- [CanvasTextBaseline](arkts-arkui-canvas-canvastextbaseline-t.md)
- [DrawingCanvas](arkts-arkui-canvas-drawingcanvas-t.md)
- [FrameNode](arkts-arkui-canvas-framenode-t.md)
- [ImageSmoothingQuality](arkts-arkui-canvas-imagesmoothingquality-t.md)
