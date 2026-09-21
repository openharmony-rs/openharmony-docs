# CanvasRenderingContext2D

```TypeScript
declare class CanvasRenderingContext2D extends CanvasRenderer
```

**CanvasRenderingContext2D** is the 2D drawing context object of the **Canvas** component, used for custom drawing on the **Canvas** component. It supports drawing shapes (rectangles, circles, ellipses, paths, etc.), text, images, gradients, shadows, and many other drawing types, and is suitable for scenarios such as data visualization, game development, image editing, and custom UI drawing. With this object, developers can flexibly control the drawing process to achieve complex 2D graphic effects.

> **NOTE:** 
> 
> * It is recommended that the **CanvasRenderingContext2D** object and the **Canvas** component be encapsulated into the same custom component, ensuring a one-to-one correspondence and consistent lifecycle between them.
> 
> * When you call drawing APIs in this module, the commands are stored in the associated **Canvas**component's command queue. These commands are only executed when the current frame enters the rendering phase and the associated **Canvas** component is visible. Therefore, when the **Canvas**component is invisible (for example, off-screen or hidden), avoid frequent drawing calls to prevent command queue buildup and excessive memory usage. For best practices, see [Controlling Canvas Rendering Based on Component Visibility](../../../ui/arkts-drawing-customization-on-canvas.md#controlling-canvas-rendering-based-on-component-visibility).
> 
> * The following path-related APIs apply only to paths created within **CanvasRenderingContext2D**and do not affect paths defined in [OffscreenCanvasRenderingContext2D](arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2d-c.md)or [Path2D](arkts-arkui-canvas-comp-path2d-c.md):[beginPath](#beginpath), [moveTo](#moveto), [lineTo](#lineto), [closePath](#closepath),[bezierCurveTo](#beziercurveto), [quadraticCurveTo](#quadraticcurveto), [arc](#arc),[arcTo](#arcto), [ellipse](#ellipse), [rect](#rect), and [roundRect](#roundrect20).
> 
> * When the width or height of the **Canvas** component exceeds 8000 px and CPU rendering is used, significant performance degradation may occur. In this case, it is recommended to use custom render nodes (RenderNode).
> 
> * When the graphics transformation APIs (**rotate**, **scale**, **transform**, **setTransform**,
> **translate**) and the **getPixelMap** **toDataURL** APIs are executed in
> different frames, the content created by the latter does not have the graphics transformation
> effect.
> 
> * The common canvas drawing methods and common canvas drawing attributes are supported.

**Inheritance/Implementation:** CanvasRenderingContext2D extends [CanvasRenderer](arkts-arkui-canvas-comp-canvasrenderer-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(settings?: RenderingContextSettings)
```

Constructs a canvas object, which supports configuration of parameters for the **CanvasRenderingContext2D** object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| settings | [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) | No | Settings of the **CanvasRenderingContext2D** object. This parameter is passed when advanced configurations such as anti-aliasing need to be enabled. If not passed, the default configuration (anti-aliasing disabled) is used. For details, see [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md). <br>If abnormal values **undefined** and **null** are passed in, the default value of [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) is used. |

**Examples**

The following example shows how to specify the unit mode during the creation of a CanvasRenderingContext2D object. The default unit mode is LengthMetricsUnit.DEFAULT, which corresponds to the default unit vp. Once set, this unit mode cannot be changed dynamically. For details, see LengthMetricsUnit.

```TypeScript
// xxx.ets
import { LengthMetricsUnit } from '@kit.ArkUI'

@Entry
@Component
struct LengthMetricsUnitDemo {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private contextPX: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings, LengthMetricsUnit.PX);
  private contextVP: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.contextPX)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          // Draw graphics in px unit mode.
          this.contextPX.fillRect(10, 10, 100, 100)
          this.contextPX.clearRect(10, 10, 50, 50)
        })

      Canvas(this.contextVP)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.contextVP.fillRect(10, 10, 100, 100)
          this.contextVP.clearRect(10, 10, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)
```

Creates a **CanvasRenderingContext2D** object, allowing for initial configuration of rendering parameters and unit mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| settings | [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) | No | Settings of the **CanvasRenderingContext2D** object. Pass this parameter when advanced configurations such as anti-aliasing need to be enabled. If not passed, the default configuration (anti-aliasing disabled) is used. For details, see [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md). <br>If abnormal values **undefined** and **null** are passed in, the default value of [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) is used. |
| unit | LengthMetricsUnit | No | Unit mode of the **CanvasRenderingContext2D** object. The configuration cannot be changed after being set. **DEFAULT**: default vp unit, suitable for most scenarios. **PX**: pixel unit, suitable for scenarios requiring precise pixel control.<br>If abnormal values **undefined**, **NaN**, and **Infinity** are passed in, the default value is used. <br>Default value: **DEFAULT** |

**Examples**

See [constructor](#constructor)

## getContext2DFromDrawingContext

```TypeScript
static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D
```

Obtains a **CanvasRenderingContext2D** object from a **DrawingRenderingContext** object. This **CanvasRenderingContext2D** object is bound to the same **Canvas** component as the input **DrawingRenderingContext** object.

> **NOTE:** 
> 
> - The **CanvasRenderingContext2D** object obtained via this API cannot be used as a parameter to create a [Canvas](arkts-arkui-canvas-comp.md#canvas)component. Otherwise, the application crashes.
> 
> - If the input **DrawingRenderingContext** object is not bound to a **Canvas** component,an error code is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawingContext | [DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) | Yes | A **DrawingRenderingContext** object.<br>The abnormal value **undefined** or **null** is treated as an invalid value. |
| options | [RenderingContextOptions](arkts-arkui-canvas-comp-renderingcontextoptions-i.md) | No | Configuration options of the rendering context.<br>The abnormal value **undefined** or **null** is treated as the default value. <br>Default value: { antialias: false } |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) | Returns a **CanvasRenderingContext2D** object that is bound to the same **Canvas** component as the input **DrawingRenderingContext**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103702](../errorcode-canvas.md#103702-drawing-context-is-not-bound-to-any-canvas-component) | The drawingContext is not bound to a canvas component. |

**Examples**

```TypeScript
// xxx.ets
import { LengthMetricsUnit } from '@kit.ArkUI';

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
          let context2D: CanvasRenderingContext2D =
            CanvasRenderingContext2D.getContext2DFromDrawingContext(drawingContext, { antialias: true })
          context2D.fillStyle = 'rgb(39,135,217)'
          context2D.fillRect(10, 30, 100, 100)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## off('onAttach')

```TypeScript
off(type: 'onAttach', callback?: Callback<void>): void
```

Unsubscribes from the event when a **CanvasRenderingContext2D** object is bound to a **Canvas** component.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'onAttach' | Yes | Event type for unsubscribing from the binding event between **CanvasRenderingContext2D** and the **Canvas** component. The value is fixed as **'onAttach'**.<br>Abnormal values such as **undefined** or **null** are treated as invalid. |
| callback | Callback&lt;void&gt; | No | If empty, cancels all callbacks subscribed for the binding event between **CanvasRenderingContext2D** and the **Canvas** component.<br>If not empty, cancels the callback subscribed for the binding event.<br>Abnormal values such as **undefined** or **null** are treated as invalid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## off('onDetach')

```TypeScript
off(type: 'onDetach', callback?: Callback<void>): void
```

Unsubscribes from the event when a **CanvasRenderingContext2D** object is unbound from a **Canvas** component.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'onDetach' | Yes | Event type for unsubscribing from the **CanvasRenderingContext2D** detach event. It is fixed as **'onDetach'**.<br>Abnormal values such as **undefined** or **null** are treated as invalid values. |
| callback | Callback&lt;void&gt; | No | If this parameter is empty, all callbacks subscribed for the **CanvasRenderingContext2D** detach event are unsubscribed.<br>If this parameter is not empty, the specific callback for the detach event is unsubscribed.<br>Abnormal values such as **undefined** or **null** are treated as invalid values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { FrameNode } from '@kit.ArkUI'

// xxx.ets
@Entry
@Component
struct AttachDetachExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true)
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)
  private scroller: Scroller = new Scroller()
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
  private node: FrameNode | null = null
  attachCallback = () => {
    console.info('CanvasRenderingContext2D attached to the canvas frame node.')
    this.node = this.context.canvas
  }
  detachCallback = () => {
    console.info('CanvasRenderingContext2D detach from the canvas frame node.')
    this.node = null
  }

  aboutToAppear(): void {
    try {
      this.context.on('onAttach', this.attachCallback)
      this.context.on('onDetach', this.detachCallback)
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`Error code: ${e.code}, message: ${e.message}`);
    }
  }

  aboutToDisappear(): void {
    try {
      this.context.off('onAttach')
      this.context.off('onDetach')
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`Error code: ${e.code}, message: ${e.message}`);
    }
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Scroll(this.scroller) {
        Flex({ direction: FlexDirection.Column }) {
          ForEach(this.arr, (item: number) => {
            Row() {
              if (item == 3) {
                Canvas(this.context)
                  .width('100%')
                  .height(150)
                  .backgroundColor('rgb(213,213,213)')
                  .onReady(() => {
                    this.context.font = '30vp sans-serif'
                    this.node?.commonEvent.setOnVisibleAreaApproximateChange(
                      { ratios: [0, 1], expectedUpdateInterval: 10 },
                      (isVisible: boolean, currentRatio: number) => {
                        if (!isVisible && currentRatio <= 0.0) {
                          console.info('Canvas is completely invisible.')
                        }
                        if (isVisible && currentRatio >= 1.0) {
                          console.info('Canvas is fully visible.')
                        }
                      }
                    )
                  })
              } else {
                Text(item.toString())
                  .width('100%')
                  .height(150)
                  .backgroundColor('rgb(39,135,217)')
                  .borderRadius(15)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .margin({ top: 5 })
              }
            }
          }, (item: number) => item.toString())
        }
      }
      .width('90%')
      .scrollBar(BarState.Off)
      .scrollable(ScrollDirection.Vertical)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('onAttach')

```TypeScript
on(type: 'onAttach', callback: Callback<void>): void
```

Subscribes to the event when a **CanvasRenderingContext2D** object is bound to a **Canvas** component.

> **NOTE:** 
> 
> A **CanvasRenderingContext2D** object can only be bound to one **Canvas** component
> at a time.<br>
> When a **CanvasRenderingContext2D** object is bound to a **Canvas** component, the
> **onAttach** callback is triggered, indicating that the
> [canvas](#canvas)
> object is accessible.<br>
> Avoid performing drawing operations in the **onAttach** callback. Make sure the
> **Canvas** component has completed its
> [onReady](arkts-arkui-canvas-comp-attribute.md#onready)
> event before performing any drawing.<br>
> The **onAttach** callback is triggered when:<br>
> 1. A **Canvas** component is created and bound to a **CanvasRenderingContext2D**object.<br>
> 2. A **CanvasRenderingContext2D** object is bound to a new **Canvas** component.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'onAttach' | Yes | Event type for subscribing to the binding event between **CanvasRenderingContext2D** and the **Canvas** component. Fixed as **'onAttach'**.<br> Abnormal values such as **undefined** or **null** are treated as invalid values. |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when **CanvasRenderingContext2D** is bound to the **Canvas** component.<br>Abnormal values such as **undefined** or **null** are treated as invalid values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## on('onDetach')

```TypeScript
on(type: 'onDetach', callback: Callback<void>): void
```

Subscribes to the event when a **CanvasRenderingContext2D** object is unbound from a **Canvas** component.

> **NOTE:** 
> 
> When a **CanvasRenderingContext2D** object is unbound from a **Canvas** component,
> the **onDetach** callback is triggered. In this case, cease any drawing operations.<br>
> The **onDetach** callback is triggered when:<br>
> 1. A **Canvas** component is destroyed and unbound from a **CanvasRenderingContext2D**object.<br>
> 2. A **CanvasRenderingContext2D** object is bound to a different **Canvas** component,causing the existing binding to be released.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'onDetach' | Yes | Event type for subscribing to the event of the **CanvasRenderingContext2D** being detached from the **Canvas** component. The value is fixed as **'onDetach'**.<br>Abnormal values **undefined** and **null** are treated as invalid values. |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when the **CanvasRenderingContext2D** is detached from the **Canvas** component.<br>Abnormal values **undefined** and **null** are treated as invalid values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

Configures and starts the AI analyzer. This API uses a promise to return the result. Before use, set [enableAnalyzer](arkts-arkui-canvas-comp-attribute.md#enableanalyzer) to **true** to enable the image AI analyzer.<br>Because the image frame used for analysis is the one captured when this API is called, pay attention to the invoking time of this API.<br> Repeated calls to this method before completion trigger an error callback. For the sample code, see the code for **stopImageAnalyzer**.

> **NOTE:** 
> 
> The image analysis type cannot be dynamically modified.
> When image changes are detected, the analysis result is automatically destroyed. You can
> call this API again to start analysis.
> This API depends on device capabilities. If it is called on an incompatible device, an
> error code is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | Yes | Input parameter required for performing AI analysis, used to configure the type of AI analysis (such as subject recognition, text recognition, etc.). For details, see **ImageAnalyzerConfig**.<br>Abnormal values **undefined** or **null** are treated as invalid values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [110001](../arkui-ts/errorcode-image-analyzer.md#110001-ai-image-analysis-not-supported) | Image analysis feature is unsupported. |
| [110002](../arkui-ts/errorcode-image-analyzer.md#110002-ai-image-analysis-already-in-progress) | Image analysis is currently being executed. |
| [110003](../arkui-ts/errorcode-image-analyzer.md#110003-ai-image-analysis-terminated) | Image analysis is stopped. |

## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

Stops AI image analysis. The content displayed by the AI image analyzer will be destroyed.

> **NOTE:** 
> 
> If this API is called when the **startImageAnalyzer** API has not yet returned any result,
> an error is reported.
> This feature depends on device capabilities.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ImageAnalyzerExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true)
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)
  private config: ImageAnalyzerConfig = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
  }
  // Replace 'common/images/example.png' with the image resource file you use.
  private img = new ImageBitmap('common/images/example.png')
  private aiController: ImageAnalyzerController = new ImageAnalyzerController()
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('start')
        .width(100)
        .height(50)
        .margin(5)
        .onClick(() => {
          this.context.startImageAnalyzer(this.config)
            .then(() => {
              console.info('analysis complete');
            })
            .catch((error: BusinessError) => {
              let e: BusinessError = error as BusinessError
              console.error(`Error code: ${e.code}, message: ${e.message}`)
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
        .width(200)
        .height(200)
        .enableAnalyzer(true)
        .onReady(() => {
          this.context.drawImage(this.img, 0, 0, 200, 200)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## toDataURL

```TypeScript
toDataURL(type?: string, quality?: any): string
```

Creates a data URL that contains a representation of an image. This API involves time-consuming memory copy. Therefore, avoid frequent calls to it.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | No | Used to specify the image format.<br>Available options: **"image/png"** (lossless compression, suitable for scenarios requiring precise pixels), **"image/jpeg"** (lossy compression, suitable for photo-like images), **"image/webp"** (efficient compression, suitable for network transmission scenarios). <br>If abnormal values **undefined** and **null** are passed in, the default value is used. <br>Default value: **image/png** |
| quality | any | No | When the image format is set to **image/jpeg** or **image/webp**, specifies the image quality in the range from 0 to 1. 0-0.5 is suitable for fast transmission or low-bandwidth scenarios, 0.6-0.8 is suitable for common scenarios, and 0.9-1.0 is suitable for high-quality requirements. If the value is out of range, the default value 0.92 is used.<br>If abnormal values **undefined**, **null**, **NaN**, and **Infinity** are passed in, the default value is used. <br>Default value: **0.92** |

**Return value:**

| Type | Description |
| --- | --- |
| string | Image URL. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct CanvasExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true)
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)
  @State toDataURL: string = ""

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width(100)
        .height(100)
        .onReady(() =>{
          this.context.fillStyle = "#00ff00"
          this.context.fillRect(0,0,100,100)
          // Generate the image URL in PNG format.
          this.toDataURL = this.context.toDataURL("image/png", 0.92)
        })
      Text(this.toDataURL)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#ffff00')
  }
}
```

## canvas

```TypeScript
readonly canvas: FrameNode
```

FrameNode instance of the **Canvas** component associated with **CanvasRenderingContext2D**. It can be used to listen for the visibility status of the associated **Canvas** component.

Default value: **null**

**Type:** [FrameNode](arkts-arkui-canvas-comp-framenode-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

Component height.

Default unit: vp

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

Component width.

Default unit: vp

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
