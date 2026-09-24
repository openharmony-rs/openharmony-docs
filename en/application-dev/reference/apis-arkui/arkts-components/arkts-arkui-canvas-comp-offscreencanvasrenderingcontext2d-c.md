# OffscreenCanvasRenderingContext2D

```TypeScript
declare class OffscreenCanvasRenderingContext2D extends CanvasRenderer
```

Use **OffscreenCanvasRenderingContext2D** to draw shapes, images, and text offscreen onto a canvas. Offscreen drawing is a process where content to draw is first drawn into a buffer, then converted into an image, and finally drawn onto the canvas at once. Offscreen drawing uses the CPU for rendering, which is relatively slow. Therefore, avoid using offscreen drawing in scenarios that require high rendering speed.

> **NOTE:** 
> 
> **OffscreenCanvasRenderingContext2D** cannot be used in **ServiceExtensionAbility**. In
> **ServiceExtensionAbility**, you are advised to use the
> [drawing module](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-graphics-drawing.md) for offscreen drawing.
> 
> The beginPath, [moveTo](arkts-arkui-canvas-comp-canvaspath-c.md#moveto),
> [lineTo](arkts-arkui-canvas-comp-canvaspath-c.md#lineto), [closePath](arkts-arkui-canvas-comp-canvaspath-c.md#closepath),
> [bezierCurveTo](arkts-arkui-canvas-comp-canvaspath-c.md#beziercurveto), [quadraticCurveTo](arkts-arkui-canvas-comp-canvaspath-c.md#quadraticcurveto),
> [arc](arkts-arkui-canvas-comp-canvaspath-c.md#arc),
> [arcTo](arkts-arkui-canvas-comp-canvaspath-c.md#arcto),
> [ellipse](arkts-arkui-canvas-comp-canvaspath-c.md#ellipse),
> [rect](arkts-arkui-canvas-comp-canvaspath-c.md#rect), and
> [roundRect](arkts-arkui-canvas-comp-canvaspath-c.md#roundrect)
> APIs take effect only on the path in **OffscreenCanvasRenderingContext2D**, and cannot take
> effect on the path set in [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md) and
> [Path2D](arkts-arkui-canvas-comp-path2d-c.md) objects.
> 
> The [common canvas drawing methods](arkts-arkui-canvas-comp-canvaspath-c.md) and [common canvas drawing properties](arkts-arkui-canvas-comp-canvasrenderer-c.md) are supported.

**Inheritance/Implementation:** OffscreenCanvasRenderingContext2D extends [CanvasRenderer](arkts-arkui-canvas-comp-canvasrenderer-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number, settings?: RenderingContextSettings)
```

Creates an offscreen canvas object. You can configure the canvas width, canvas height, and parameters of the **OffscreenCanvasRenderingContext2D** object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the offscreen canvas. The default unit is vp.<br> Invalid values **NaN** and **Infinity** are treated as invalid. |
| height | number | Yes | Height of the offscreen canvas. The default unit is vp.<br> Invalid values **NaN** and **Infinity** are treated as invalid. |
| settings | [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) | No | Used to configure the parameters of the **OffscreenCanvasRenderingContext2D** object. Pass this parameter when advanced configurations such as antialiasing need to be enabled. See the description of the **RenderingContextSettings** API.<br>The exception value **undefined** is handled as the default value of [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md).<br> Default value: **null** |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit)
```

Creates an offscreen canvas object. You can configure the canvas width, canvas height, and parameters and their unit of the **OffscreenCanvasRenderingContext2D** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the offscreen canvas. The default unit is vp.<br> Invalid values **NaN** and **Infinity** are treated as invalid. |
| height | number | Yes | Height of the offscreen canvas. The default unit is vp.<br> Invalid values **NaN** and **Infinity** are treated as invalid. |
| settings | [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) | No | Used to configure the parameters of the **OffscreenCanvasRenderingContext2D** object. Pass this parameter when advanced configurations such as antialiasing need to be enabled. See the description of the **RenderingContextSettings** API.<br>The exception value **undefined** is handled as the default value of [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md).<br> Default value: **null** |
| unit | LengthMetricsUnit | No | Used to configure the unit mode of the **OffscreenCanvasRenderingContext2D** object. **DEFAULT** (default vp unit, suitable for most scenarios) and PX (px pixel unit, suitable for scenarios that require precise pixel control). Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> The exception values **undefined**, **NaN**, and **Infinity** are handled as default values.<br> Default value: **DEFAULT** |

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
| type | string | No | Used to specify the image format.<br>Optional values: **image/png**, **image/jpeg**, and **image/webp**. <br>The exception values **undefined** and **null** are handled as the default value. <br>Default value: **image/png** |
| quality | any | No | When the image format is image/jpeg or image/webp, selects the image quality in the range [0, 1]. If the value is out of range, the default value **0.92** is used.<br>The exception values **undefined**, **null**, **NaN**, and **Infinity** are handled as the default value. <br>Default value: **0.92** |

**Return value:**

| Type | Description |
| --- | --- |
| string | Image URL. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct ToDataURL {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(100, 100);
  @State dataURL: string = "";

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width(100)
        .height(100)
        .onReady(() => {
          let offContext = this.offCanvas.getContext("2d", this.settings)
          offContext.fillRect(0, 0, 100, 100)
          this.dataURL = offContext.toDataURL()
        })
      Text(this.dataURL)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#ffff00')
  }
}
```

## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

Creates an **ImageBitmap** object from the most recently rendered image of the offscreen canvas.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) | Pixel data rendered on the offscreen canvas. |

**Examples**

```TypeScript
// xxx.ets
@Entry
@Component
struct PutImageData {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(600, 600);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('rgb(213,213,213)')
        .onReady(() => {
          let offContext = this.offCanvas.getContext("2d", this.settings)
          let imageData = offContext.createImageData(100, 100)
          for (let i = 0; i < imageData.data.length; i += 4) {
            imageData.data[i + 0] = 112
            imageData.data[i + 1] = 112
            imageData.data[i + 2] = 112
            imageData.data[i + 3] = 255
          }
          offContext.putImageData(imageData, 10, 10)
          let image = this.offCanvas.transferToImageBitmap()
          this.context.transferFromImageBitmap(image)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```
