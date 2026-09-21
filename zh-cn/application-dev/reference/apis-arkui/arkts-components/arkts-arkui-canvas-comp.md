# Canvas

提供画布组件，用于自定义绘制图形。

## 子组件

不支持。

## Canvas

```TypeScript
Canvas(context?: CanvasRenderingContext2D | DrawingRenderingContext)
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。

使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置[visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility)属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) &#124; [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) | 否 | CanvasRenderingContext2D: 不支持多个Canvas共用一个CanvasRenderingContext2D对象，具体描述见[CanvasRenderingContext2D](#canvas)对象。DrawingRenderingContext: 不支持多个Canvas共用一个DrawingRenderingContext对象，具体描述见[DrawingRenderingContext](#canvas)对象。<br>异常值null和undefined按未设置context处理。 |

## Canvas

```TypeScript
Canvas(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions)
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。支持设置CanvasRenderingContext2D对象或DrawingRenderingContext对象，支持设置AI分析选项。

使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置[visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility)属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) &#124; [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) | 是 | CanvasRenderingContext2D: 不支持多个Canvas共用一个CanvasRenderingContext2D对象，具体描述见[CanvasRenderingContext2D](#canvas)对象。DrawingRenderingContext: 不支持多个Canvas共用一个DrawingRenderingContext对象，具体描述见[DrawingRenderingContext](#canvas)对象。<br>异常值null和undefined按未设置context处理。 |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。<br>异常值null和undefined按[ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)的默认值处理，默认取值为{ type: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT], aiController: new ImageAnalyzerController() }，即开启主体识别和文字识别功能。 |

## Canvas

```TypeScript
Canvas(params: CanvasParams)
```

使用CanvasParams创建不缓存指令的Canvas组件。创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。Canvas组件未设置固定尺寸时，默认扩展至其最大可用尺寸。

> **说明：** 
> 
> - 使用本接口创建的Canvas组件将在[onReady&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkui-canvas-comp-attribute.md#onready-1)回调的入参中返回一个[DrawingRenderingContext&lt;sup&gt;12+&lt;/sup&gt;](#canvas)对象，可用于在该Canvas组件上进行绘制。
> 
> - 使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。
> 
> - 不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置[visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility)属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) | 是 | Canvas组件的构造参数，用于创建不缓存指令的Canvas组件。配置参数详见[CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md)。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) | 定义Canvas的具体配置参数。 |
| [CanvasPattern](arkts-arkui-canvas-comp-canvaspattern-i.md) | 一个Object对象，使用[createPattern](arkts-arkui-canvas-comp-canvasrenderer-c.md#createpattern)方法创建，通过指定图像和重复方式创建图片填充的模板。 |
| [OffscreenCanvasRenderingContext2DInterface](arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2dinterface-i.md) | 使用OffscreenCanvasRenderingContext2D在Canvas上进行离屏绘制，绘制对象可以是形状、文本、图片等。离屏绘制是指将需要绘制的内容先绘制在缓存区，然后将其转换成图片，一次性绘制到Canvas上。离屏绘制使用CPU进行绘制，绘制速度较慢，对绘制速度有要求的场景应避免使用离屏绘制。 |
| [RenderingContextOptions](arkts-arkui-canvas-comp-renderingcontextoptions-i.md) | 定义渲染上下文的具体配置参数。 |
| [Size](arkts-arkui-canvas-comp-size-i.md) | DrawingRenderingContext的尺寸信息。 |
| [TextMetrics](arkts-arkui-canvas-comp-textmetrics-i.md) | 文本的尺寸信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CanvasDirection](arkts-arkui-canvas-comp-canvasdirection-t.md) | 定义当前文本方向的类型。取值类型为下表类型中的并集。 |
| [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | 定义用于确定点是在路径内还是路径外的填充样式算法的类型。取值类型为下表类型中的并集。 |
| [CanvasLineCap](arkts-arkui-canvas-comp-canvaslinecap-t.md) | 定义绘制每条线段端点的类型。取值类型为下表类型中的并集。 |
| [CanvasLineJoin](arkts-arkui-canvas-comp-canvaslinejoin-t.md) | 定义长度不为0的两个连接部分（线段、圆弧和曲线）的类型。取值类型为下表类型中的并集。 |
| [CanvasTextAlign](arkts-arkui-canvas-comp-canvastextalign-t.md) | 定义文本对齐方式的类型。取值类型为下表类型中的并集。 |
| [CanvasTextBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) | 定义文本基线类型。取值类型为下表类型中的并集。 |
| [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) | 可用于向DrawingRenderingContext上绘制内容的画布对象。 |
| [FrameNode](arkts-arkui-canvas-comp-framenode-t.md) | Import the frame node type object for Canvas. |
| [ImageSmoothingQuality](arkts-arkui-canvas-comp-imagesmoothingquality-t.md) | 定义图片平滑度类型。取值类型为下表类型中的并集。 |

## 示例

### 示例1（使用CanvasRenderingContext2D中的方法）

该示例实现了如何在Canvas组件使用[CanvasRenderingContext2D](./ts-canvasrenderingcontext2d.md)中的方法进行绘制。



```TypeScript
// xxx.ets
@Entry
@Component
struct CanvasExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(0, 30, 100, 100)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（使用DrawingRenderingContext中的方法）

该示例实现了如何在Canvas组件使用[DrawingRenderingContext](./ts-drawingrenderingcontext.md)中的方法进行绘制。



```TypeScript
// xxx.ets
@Entry
@Component
struct CanvasExample {
  private context: DrawingRenderingContext = new DrawingRenderingContext();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('rgb(213,213,213)')
        .onReady(() => {
          this.context.canvas.drawCircle(200, 200, 100)
          this.context.invalidate()
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### 示例3（使用attributeModifier动态设置Canvas组件的属性及方法）

该示例展示了如何使用[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)动态设置Canvas组件的[enableAnalyzer](#enableanalyzer12)属性和[onReady](#onready)方法。

> 说明：
> 
> 此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2版本开始，新建工程或模块时，默认创建的模块不会对非resources目录下的资源进行打包，需启用相关开关：模块的build-profile.json5中buildOption > resOptions > copyCodeResource > enable设置为true，详见resOptions中[copyCodeResource](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)相关介绍。



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

class MyCanvasModifier implements AttributeModifier<CanvasAttribute> {
  context: CanvasRenderingContext2D = new CanvasRenderingContext2D()

  applyNormalAttribute(instance: CanvasAttribute): void {
    // 从（0，0）绘制一张宽高为200vp的图片
    instance.onReady(() => {
      // "common/img.png"需要替换为开发者所需的图像资源文件
      let image = new ImageBitmap("common/img.png")
      this.context.drawImage(image, 0, 0, 200, 200)
    })
    // 设置开启组件AI分析功能，点击start按钮调用startImageAnalyzer方法启动AI分析
    instance.enableAnalyzer(true)
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyCanvasModifier = new MyCanvasModifier()
  private settings: RenderingContextSettings = new RenderingContextSettings(true)
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)
  private config: ImageAnalyzerConfig = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
  }
  private aiController: ImageAnalyzerController = new ImageAnalyzerController()
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  }

  build() {
    Row() {
      Column() {
        Button('start')
          .width(100)
          .height(50)
          .margin(5)
          .onClick(() => {
            this.context.startImageAnalyzer(this.config)
              .then(() => {
                console.info("analysis complete")
              })
              .catch((error: BusinessError) => {
                console.error(`Error code: ${error.code}, message: ${error.message}`)
              })
          })
        Button('stop')
          .width(100)
          .height(50)
          .margin(5)
          .onClick(() => {
            this.context.stopImageAnalyzer()
          })
        Button('getTypes')
          .width(100)
          .height(50)
          .margin(5)
          .onClick(() => {
            this.aiController.getImageAnalyzerSupportTypes()
          })
        Canvas(this.context, this.options)
          .borderWidth(1)
          .height(200)
          .width(200)
          .attributeModifier(this.modifier)
          .onAppear(() => {
            this.modifier.context = this.context
          })
      }
    }
  }
}
```

### 示例4（创建不缓存指令Canvas并进行绘制）

该示例介绍了如何使用[CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md)创建不缓存指令的Canvas组件并进行绘制。

从API version 23开始，新增CanvasParams接口。

```TypeScript
// xxx.ets
import { LengthMetricsUnit } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct CanvasExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas({ unit: LengthMetricsUnit.DEFAULT })
        .onReady((drawingContext?: DrawingRenderingContext) => {
          if (!drawingContext) {
            return
          }
          // 使用DrawingRenderingContext进行绘制。
          let brush = new drawing.Brush()
          brush.setColor({
            alpha: 255,
            red: 39,
            green: 135,
            blue: 217
          })
          drawingContext.canvas.attachBrush(brush)
          drawingContext.canvas.drawCircle(200, 200, 100)
          drawingContext.invalidate()

          // 使用CanvasRenderingContext2D进行绘制。
          let context2D: CanvasRenderingContext2D =
            CanvasRenderingContext2D.getContext2DFromDrawingContext(drawingContext, { antialias: true })
          context2D.fillStyle = 'rgb(39,135,217)'
          context2D.fillRect(110, 30, 100, 100)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
