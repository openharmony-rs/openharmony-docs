# ImageBitmap

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=0ac6eaf21c519d27b118617e6aaa0ba03069a649 translatedAt=2026-07-30T02:34:02.288Z pushedAt=2026-08-01T06:42:55.881Z -->

An **ImageBitmap** object stores pixel data rendered on a canvas. Since API version 11, when an application creates a [worker thread](../../../arkts-utils/worker-introduction.md), it can use **postMessage** to transfer the **ImageBitmap** instance to the worker thread for drawing, and use **onmessage** to receive the drawing results sent by the worker thread for display. 

> **NOTE**
>
> * The initial APIs of this module are supported since API version 8. Newly added APIs are marked with a superscript to indicate their earliest API version.
>
> * The **ImageBitmap** object only supports loading static images. To play animated images, use the [Image](./ts-basic-components-image.md) component.

## constructor

constructor(src: string)

Creates an **ImageBitmap** object using an image data source.

> **NOTE**
>
> Call the **close()** method to release resources after use to avoid image resource leaks.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

<!--Table: 10%; 10%; 10%; 70%-->

| Name | Type  | Mandatory | Description                                   |
| ---- | ------ | ---- | ---------------------------------------- |
| src | string | Yes | Image data source. Supports local images.<br>1. The string format is used to load local images, for example, `ImageBitmap("common/images/example.jpg")`. For modules of the "entry" and "feature" types, the starting point of the image loading path is the ets folder of the current module. For modules of the "har" and "shared" types, the starting point of the image loading path is the ets folder of the currently built "entry" or "feature" type module.<br>For modules of the "har" and "shared" types, it is recommended to use the [ImageSource](../../../media/image/image-decoding.md) image decoding method to decode resource images into a unified PixelMap for loading.<br>2. Supported local image types: bmp, jpg, png, svg, and webp.<br>**NOTE**<br>- In ArkTS widgets, strings with network-related path prefixes such as `http://`, the `datashare://` path prefix, and the `file://data/storage` path prefix are not supported. |

## constructor

constructor(data: PixelMap)

Creates an **ImageBitmap** object using a **PixelMap** object.

> **NOTE**
>
> Call the **close()** method to release resources after use to avoid image resource leaks.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory | Description                                   |
| ---- | ------ | ---- | ---------------------------------------- |
| data  | [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes    | Image data source, set through a **PixelMap** object. Applicable to scenarios where images need to be decoded and processed before drawing, which can improve image loading performance. |

## constructor<sup>12+</sup>

constructor(src: string, unit: LengthMetricsUnit)

Creates an **ImageBitmap** object using an image data source. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE**
>
> Call the **close()** method to release resources after use to avoid image resource leaks.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory | Description                                   |
| ---- | ------ | ---- | ---------------------------------------- |
| src  | string | Yes  | Image data source, which supports local images.<br>1. The string format is used to load local images, for example, `ImageBitmap("common/images/example.jpg")`. For modules of the "entry" and "feature" types, the image loading path starts from the ets folder of the current module. For modules of the "har" and "shared" types, the image loading path starts from the ets folder of the currently built "entry" or "feature" type module.<br>For modules of the "har" and "shared" types, you are advised to use the [ImageSource](../../../media/image/image-decoding.md) image decoding method to decode resource images into a unified PixelMap for loading.<br>2. Supported local image types: bmp, jpg, png, svg, and webp.<br>**Note:**<br>- ArkTS widgets do not support strings with network-related path prefixes such as `http://`, the `datashare://` path prefix, or the `file://data/storage` path prefix. |
| unit  | [LengthMetricsUnit](../js-apis-arkui-graphics.md#lengthmetricsunit12) | Yes  | Unit mode for configuring the **ImageBitmap** object. The mode cannot be dynamically changed after configuration. The configuration method is the same as that of [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md).<br>Default value: **LengthMetricsUnit.DEFAULT**.<br>Abnormal values such as **undefined**, **NaN**, and **Infinity** are processed as the default value. |

## constructor<sup>12+</sup>

constructor(data: PixelMap, unit: LengthMetricsUnit)

Creates an **ImageBitmap** object using a **PixelMap** object. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE**
>
> Call the **close()** method to release resources after use to avoid image resource leaks.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory | Description                                   |
| ---- | ------ | ---- | ---------------------------------------- |
| data  | [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes    | Image data source, set through a **PixelMap** object. This is suitable for scenarios where images need to be decoded and processed before drawing, which can improve image loading performance. |
| unit   | [LengthMetricsUnit](../js-apis-arkui-graphics.md#lengthmetricsunit12) | Yes | Used to configure the unit mode of the **ImageBitmap** object. Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md).<br>Default value: **LengthMetricsUnit.DEFAULT**.<br>Abnormal values such as **undefined**, **NaN**, and **Infinity** are processed as the default value. |

## constructor

constructor(data: Resource, unit?: LengthMetricsUnit)

Creates an **ImageBitmap** object using a **Resource** object. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE**
>
> Call the **close()** method to release resources after use to avoid image resource leaks.

**Since:** 26.0.0

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory  | Description                                    |
| ---- | ------ | ---- | ---------------------------------------- |
| data  | [Resource](ts-types.md#resource) | Yes    | Image data source, set by referencing a **Resource** object. This is used to reference image resources in the app resource directory, for example, **$r('app.media.example')**, which avoids hardcoding paths.<br>Supported image types: bmp, jpg, png, svg, and webp. |
| unit   | [LengthMetricsUnit](../js-apis-arkui-graphics.md#lengthmetricsunit12) | No | Unit mode of the **ImageBitmap** object. Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md).<br>Default value: **LengthMetricsUnit.DEFAULT**.<br>Abnormal values **undefined**, **NaN**, and **Infinity** are processed as the default value. |

## close

close(): void

Releases all image resources associated with the **ImageBitmap** object and sets its width and height to **0**.

> **NOTE**
>
> - This method must be used together with the [constructor()](#constructor) method. After creating an **ImageBitmap** object, call **close()** to release resources when they are no longer needed. Failure to call **close()** may cause image resource leaks and affect app performance.
> - It is recommended to call this method after **Canvas** drawing is complete, for example, at the end of the [onReady](ts-components-canvas-canvas.md#onready) callback.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type| Read Only| Optional| Description|
| ------ | ------ | ----- | -------- | --------------------------- |
| width | number | Yes | No | Width of the **ImageBitmap**.<br>Unit: vp. |
| height | number | Yes | No | Height of the **ImageBitmap**.<br>Unit: vp. |

## Example

### Example 1: Loading an Image

This example demonstrates how to load a local image using the **ImageBitmap** object.

> **NOTE**
>
> The resources in this example are not located in the **src > main > resource** directory. Starting from DevEco Studio 6.0.0 Beta2, when creating a new project or module, the default module does not package resources outside the resources directory. You need to enable the related switch: set **buildOption > resOptions > copyCodeResource > enable** to **true** in the module's **build-profile.json5**. For details, see [copyCodeResource](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348) in **resOptions**.

```ts
// xxx.ets
@Entry
@Component
struct ImageExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  // Replace "common/images/example.jpg" with the image resource file required by the developer.
  private img: ImageBitmap = new ImageBitmap('common/images/example.jpg');

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.drawImage(this.img, 0, 0, 500, 500, 0, 0, 400, 200)
          this.img.close()
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![imageBitmap](figures/imageBitmap.png)

### Example 2: Creating an ImageBitmap Object

This example shows how to create an **ImageBitmap** object using a **PixelMap** object.

> **NOTE**
>
> The DevEco Studio Previewer does not support the **getPixelMap** API and cannot display content drawn by **PixelMap**.

```ts
// xxx.ets
@Entry
@Component
struct Demo {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('50%')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillStyle = '#00ff00'
          this.context.fillRect(0, 0, 100, 100)
          let pixel = this.context.getPixelMap(0, 0, 100, 100)
          let image = new ImageBitmap(pixel)
          this.context.drawImage(image, 100, 100)
        })

    }
    .width('100%')
    .height('100%')
  }
}
```

  ![imageBitmap2](figures/imageBitmap2.png)

### Example 3: Supporting Concurrent Thread Drawing

This example demonstrates how to implement concurrent thread drawing by creating a Worker thread.

> **NOTE**
>
> The content drawn in the Worker thread cannot be previewed in DevEco Studio Previewer.

```ts
import { worker } from '@kit.ArkTS';

@Entry
@Component
struct imageBitmapExamplePage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private myWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
  // Replace "common/images/example.jpg" with the image resource file you use.
  private img: ImageBitmap = new ImageBitmap("common/images/example.jpg");

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.myWorker.postMessage({ myImage: this.img });
          this.myWorker.onmessage = (e): void => {
            if (e.data.myImage) {
              let image: ImageBitmap = e.data.myImage
              this.context.transferFromImageBitmap(image)
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

In the worker thread, the application uses **onmessage** to receive the **ImageBitmap** object sent by the main thread through **postMessage** and proceeds with rendering.

```ts
import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  if (e.data.myImage) {
    let img: ImageBitmap = e.data.myImage
    let offCanvas = new OffscreenCanvas(600, 600)
    let offContext = offCanvas.getContext('2d')
    offContext.drawImage(img, 0, 0, 500, 500, 0, 0, 400, 200)
    let image = offCanvas.transferToImageBitmap()
    workerPort.postMessage({ myImage: image });
  }
}
```

  ![imageBitmap](figures/imageBitmap.png)

### Example 4: Loading a Resource Image

Create an **ImageBitmap** object of the **Resource** type using the **constructor** API for canvas drawing.

Since API version 26.0.0, the [constructor](#constructor-2) API is added.

```ts
// xxx.ets
@Entry
@Component
struct ImageBitmapResourceExample {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  // Replace "app.media.example" with the image resource file required by the developer.
  private img: ImageBitmap = new ImageBitmap($r("app.media.example"));

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('#ffff00')
        .onReady(() => { 
          this.context.drawImage(this.img, 0, 0, 500, 500, 0, 0, 400, 200)
          this.img.close()
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![imageBitmap4](figures/imageBitmap4.png)