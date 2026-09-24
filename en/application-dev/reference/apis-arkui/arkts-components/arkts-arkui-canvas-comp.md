# Canvas

The **Canvas** component can be used to customize drawings.

## Canvas

```TypeScript
Canvas(context?: CanvasRenderingContext2D | DrawingRenderingContext)
```

Creates a **Canvas** component. The maximum allowed size cannot exceed 10000 px × 10000 px. If the size exceeds this limit, the **Canvas** component will fail to be created.

The **Canvas** component created using this API does not respond to drawing instructions when the component is invisible. Invisible scenarios mainly include the page where the component is located entering the background, the component sliding out of the window, and setting the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute to hidden. Scenarios where the component is obscured by other components or other windows are not included.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) &#124; [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) | No | 2D rendering context for a canvas. <br>**CanvasRenderingContext2D**: Canvases cannot share one **CanvasRenderingContext2D** object. For details, see [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md). **DrawingRenderingContext**: Canvases cannot share one **DrawingRenderingContext** object. For details, see [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md). <br>If the value is **null** or **undefined**, **context** is considered unset. |

## Canvas

```TypeScript
Canvas(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions)
```

When creating a **Canvas** component, the maximum area cannot exceed 10000 px × 10000 px. If the size exceeds this limit, the **Canvas** component will fail to be created. You can specify a **CanvasRenderingContext2D** or **DrawingRenderingContext** object, along with AI analysis options.

The **Canvas** component created using this API does not respond to drawing instructions when the component is invisible. Invisible scenarios mainly include the page where the component is located entering the background, the component sliding out of the window, and setting the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute to hidden. Scenarios where the component is obscured by other components or other windows are not included.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) &#124; [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) | Yes | 2D rendering context for a canvas. <br>**CanvasRenderingContext2D**: Canvases cannot share one **CanvasRenderingContext2D** object. For details, see [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md). **DrawingRenderingContext**: Canvases cannot share one **DrawingRenderingContext** object. For details, see [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md). <br>If the value is **null** or **undefined**, **context** is considered unset. |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | Yes | AI image analysis options. You can configure the analysis type or bind an analyzer controller through this parameter.<br>If the value is **null** or **undefined**, the default value of **ImageAIOptions** is used. The default value is **{ type: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT], aiController: new ImageAnalyzerController() }**, indicating that subject recognition and text recognition are enabled. |

## Canvas

```TypeScript
Canvas(params: CanvasParams)
```

Creates a **Canvas** component that does not cache commands using **CanvasParams**. When creating a **Canvas** component, the maximum area cannot exceed 10000 px × 10000 px. If the area exceeds this limit, the **Canvas** component cannot be created properly. When the **Canvas** component does not have a fixed size set, it expands to its maximum available size by default.

> **NOTE:** 
> 
> * The **Canvas** component created using this API returns a [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) object in the input parameter of the [onReady](arkts-arkui-canvas-comp-attribute.md#onready) callback, which can be used for drawing on the **Canvas** component.
> 
> * The **Canvas** component created using this API does not respond to drawing instructions when the component is invisible.
> 
> * Invisible scenarios mainly include the page where the component is located entering the background, the component sliding out of the window, and setting the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute to hidden. Scenarios where the component is obscured by other components or other windows are not included.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) | Yes | Construction parameters of the **Canvas** component, used to create a **Canvas** component that does not cache drawing instructions. For details about the configuration parameters, see [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md). |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) | Defines the parameters of the **Canvas** component. |
| [CanvasPattern](arkts-arkui-canvas-comp-canvaspattern-i.md) | **CanvasPattern** represents an object, created by the [createPattern](../arkts-apis/arkts-arkui-viewmodel-canvasrenderingcontext2d-i.md#createpattern) API, describing an image filling pattern based on the image and repetition mode. It is suitable for scenarios where pattern filling or background textures are needed on a canvas, simplifying pattern filling implementation and improving drawing efficiency. |
| [RenderingContextOptions](arkts-arkui-canvas-comp-renderingcontextoptions-i.md) | Defines the specific configuration parameters for the rendering context. |
| [Size](arkts-arkui-canvas-comp-size-i.md) | Provides size information of the **DrawingRenderingContext** object. |
| [TextMetrics](arkts-arkui-canvas-comp-textmetrics-i.md) | Size information of the text. |

### Types

| Name | Description |
| --- | --- |
| [CanvasDirection](arkts-arkui-canvas-comp-canvasdirection-t.md) | Defines the current text direction. The value type is a union of the types listed in the table below. |
| [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | Defines the fill pattern algorithm used to determine whether a point is inside or outside a path. The value type is a union of the types listed in the table below. |
| [CanvasLineCap](arkts-arkui-canvas-comp-canvaslinecap-t.md) | Specifies the attribute of drawing the end of each line segment. |
| [CanvasLineJoin](arkts-arkui-canvas-comp-canvaslinejoin-t.md) | Defines the type of join between two non-zero-length segments (lines, arcs, and curves). The value type is a union of the types listed in the table below. |
| [CanvasTextAlign](arkts-arkui-canvas-comp-canvastextalign-t.md) | Defines the type of text alignment. The value type is a union of the types listed in the table below. |
| [CanvasTextBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) | Defines the text baseline type. The value type is a union of the types listed in the table below. |
| [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) | Defines a canvas object for drawing content on the **XComponent** component. |
| [FrameNode](arkts-arkui-canvas-comp-framenode-t.md) | Import the frame node type object for Canvas. |
| [ImageSmoothingQuality](arkts-arkui-canvas-comp-imagesmoothingquality-t.md) | Sets the image smoothness attribute. |

## Examples

### Example 1: Using APIs in CanvasRenderingContext2D

This example describes how to use the APIs in [CanvasRenderingContext2D](./ts-canvasrenderingcontext2d.md) for drawing on a canvas.



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

### Example 2: Using APIs in DrawingRenderingContext

This example demonstrates how to use the APIs in [DrawingRenderingContext](./ts-drawingrenderingcontext.md) for drawing on a canvas.



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

### Example 3: Dynamically Setting Attributes and Methods of the Canvas Component Using attributeModifier

This example demonstrates how to use [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) to dynamically set the [enableAnalyzer](#enableanalyzer12) attribute and [onReady](#onready) method of the Canvas component.

> NOTE
> 
> The resources in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, when creating a project or module, the default module does not package resources outside the resources directory. You need to enable the related switch: set buildOption > resOptions > copyCodeResource > enable to true in the module's build-profile.json5. For details, see [copyCodeResource](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348) in resOptions.



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

class MyCanvasModifier implements AttributeModifier<CanvasAttribute> {
  context: CanvasRenderingContext2D = new CanvasRenderingContext2D()

  applyNormalAttribute(instance: CanvasAttribute): void {
    // Draw an image with the width and height of 200 vp from (0, 0).
    instance.onReady(() => {
      // Replace "common/img.png" with the image resource file you use.
      let image = new ImageBitmap("common/img.png")
      this.context.drawImage(image, 0, 0, 200, 200)
    })
    // Enable the component AI analysis function, and click the start button to call the startImageAnalyzer method to start AI analysis.
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

### Example 4: Creating a Canvas Component That Does Not Cache Commands for Drawing

This example demonstrates how to use [CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md) to create a Canvas component that does not cache commands for drawing.

The CanvasParams API is supported since API version 23.

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
          // Use DrawingRenderingContext for drawing.
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

          // Use CanvasRenderingContext2D for drawing.
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
