# XComponent

**XComponent** provides a [surface](../../../ui/napi-xcomponent-guidelines.md#overview) for graphics rendering and media data input into your view. You can customize the position and size of the surface as needed. For details, see [Native XComponent](../../../ui/napi-xcomponent-guidelines.md).

> **NOTE**

## Child Components

Not supported

## XComponent

```TypeScript
XComponent(value: { id: string; type: string; libraryname?: string; controller?: XComponentController })
```

Constructor parameters

**Since:** 8

**Deprecated since:** 12

**Substitutes:** (value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController })

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { id: string; type: string; libraryname?: string; controller?: XComponentController } | Yes | Indicates the options of the xcomponent. |

## XComponent

```TypeScript
XComponent(value: { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController })
```

Creates an **XComponent** component, whose lifecycle callbacks can be triggered from the native side.

This API is deprecated since API version 12. You are advised to use [XComponent(options: XComponentOptions)](../../../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#xcomponent12) instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { id: string; type: XComponentType; libraryname?: string; controller?: XComponentController } | Yes | Indicates the options of the xcomponent. |

## XComponent

```TypeScript
XComponent(options: XComponentOptions)
```

Creates an **XComponent** component, allowing you to obtain the **SurfaceId** value on the ArkTS side, register the lifecycle callbacks for the surface held by the **XComponent** and the callbacks for component events such as touch, mouse, and key events, and configure the AI analyzer feature.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [XComponentOptions](arkts-arkui-xcomponent-comp-xcomponentoptions-i.md) | Yes | Options of the **XComponent**. |

## XComponent

```TypeScript
XComponent(params: NativeXComponentParameters)
```

Obtains an **XComponent** node instance on the native side, and registers the lifecycle callbacks for the surface held by the **XComponent** and the callbacks for component events, such as touch, mouse, and key events.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [NativeXComponentParameters](arkts-arkui-xcomponent-comp-nativexcomponentparameters-i.md) | Yes | Options of the **XComponent**. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [NativeXComponentParameters](arkts-arkui-xcomponent-comp-nativexcomponentparameters-i.md) | Defines the options of the **XComponent**. An XComponent created with such constructor parameters can pass its corresponding [FrameNode](../arkts-apis/arkts-arkui-typenode-n.md) object to the Native side, enabling the use of NDK APIs for surface lifecycle–related settings and [component event listening](../../../ui/ndk-listen-to-component-events.md). |
| [SurfaceConfig](arkts-arkui-xcomponent-comp-surfaceconfig-i.md) | Describes whether the surface held by the **XComponent** is treated as opaque during rendering. |
| [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | Describes the rectangle of the surface held by the **XComponent**. |
| [SurfaceRotationOptions](arkts-arkui-xcomponent-comp-surfacerotationoptions-i.md) | Defines whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates. |
| [XComponentOptions](arkts-arkui-xcomponent-comp-xcomponentoptions-i.md) | Defines the options of the **XComponent**. |

### Types

| Name | Description |
| --- | --- |
| [OnNativeLoadCallback](arkts-arkui-xcomponent-comp-onnativeloadcallback-t.md) | Triggered after the surface held by **XComponent** is created. |

### Enums

| Name | Description |
| --- | --- |
| [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md) | Sets the HDR type of the XComponent. |

## Examples

### Example 1: Enabling AI Image Analyzer

This example shows how to use the enableAnalyzer attribute to enable image AI analysis. You can use XComponentController to start or stop image AI analysis.

> NOTE
> 
> For details about the specific implementation of the drawing logic in this example (the implementation of functions related to nativeRender), see [ArkTS XComponent Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import nativeRender from 'libnativerender.so'; // The .so file implemented by the developer. For details, see the description above.

class CustomXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
    nativeRender.SetSurfaceId(BigInt(surfaceId));
  }

  onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
    console.info(`onSurfaceChanged surfaceId: ${surfaceId}, rect: ${JSON.stringify(rect)}`);
    nativeRender.ChangeSurface(BigInt(surfaceId), rect.surfaceWidth, rect.surfaceHeight);
  }

  onSurfaceDestroyed(surfaceId: string): void {
    console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    nativeRender.DestroySurface(BigInt(surfaceId));
  }
}

@Entry
@Component
struct XComponentExample {
  xComponentController: XComponentController = new CustomXComponentController();
  private config: ImageAnalyzerConfig = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
  };
  private aiController: ImageAnalyzerController = new ImageAnalyzerController();
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  };
  @State xcWidth: string = "720px";
  @State xcHeight: string = "720px";
  @State currentStatus: string = "index";

  build() {
    Column({ space: 5 }) {
      Row() {
        Text('Native XComponent Sample')
          .fontSize('24fp')
          .fontWeight(500)
          .margin({
            left: 24,
            top: 12
          })
      }
      .margin({ top: 24 })
      .width('100%')
      .height(56)

      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController,
        imageAIOptions: this.options
      })
        .width(this.xcWidth)
        .height(this.xcHeight)
        .enableAnalyzer(true)
        .onClick(() => {
          let surfaceId = this.xComponentController.getXComponentSurfaceId();
          nativeRender.ChangeColor(BigInt(surfaceId));
          let hasChangeColor: boolean = false;
          let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
          if (status) {
            hasChangeColor = status.hasChangeColor;
          }
          if (hasChangeColor) {
            this.currentStatus = "change color";
          }
        })
      Text(this.currentStatus)
        .fontSize('24fp')
        .fontWeight(500)
      Column() {
        Button('start AI analyze')
          .onClick(() => {
            this.xComponentController.startImageAnalyzer(this.config)
              .then(() => {
                console.info("analysis complete");
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to start image analyzer. Code: ${error.code}, message: ${error.message}`);
              })
          })
          .margin(2)
        Button('stop AI analyze')
          .onClick(() => {
            this.xComponentController.stopImageAnalyzer();
          })
          .margin(2)
        Button('get analyzer types')
          .onClick(() => {
            this.aiController.getImageAnalyzerSupportTypes();
          })
          .margin(2)
        Button('Draw Star')
          .fontSize('16fp')
          .fontWeight(500)
          .onClick(() => {
            let surfaceId = this.xComponentController.getXComponentSurfaceId();
            console.info(`surface rect is ${this.xComponentController.getXComponentSurfaceRect()}`);
            nativeRender.DrawPattern(BigInt(surfaceId));
            let hasDraw: boolean = false;
            let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
            if (status) {
              hasDraw = status.hasDraw;
            }
            if (hasDraw) {
              this.currentStatus = "draw star";
            }
          })
          .margin(2)
      }.justifyContent(FlexAlign.Center)
    }
    .width('100%')
  }
}
```

### Example 2 (Locking During Surface Rotation)

Uses setXComponentSurfaceRotation to lock the Surface orientation during screen rotation so that it does not rotate with the screen.

> NOTE
> 
> For details about the implementation of the drawing logic in this example (the function implementation related to nativeRender), see [ArkTS XComponent Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).

```TypeScript
// xxx.ets
import nativeRender from 'libnativerender.so';

class MyXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
    nativeRender.SetSurfaceId(BigInt(surfaceId));
  }

  onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
    console.info(`onSurfaceChanged surfaceId: ${surfaceId}, rect: ${JSON.stringify(rect)}`);
    nativeRender.ChangeSurface(BigInt(surfaceId), rect.surfaceWidth, rect.surfaceHeight);
  }

  onSurfaceDestroyed(surfaceId: string): void {
    console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    nativeRender.DestroySurface(BigInt(surfaceId));
  }
}

@Entry
@Component
struct Index {
  @State isLock: boolean = true;
  @State xcWidth: number = 500;
  @State xcHeight: number = 700;
  myXComponentController: XComponentController = new MyXComponentController();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Start }) {
      XComponent({
        id: "XComponent",
        type: XComponentType.SURFACE,
        controller: this.myXComponentController
      })
        .onLoad(() => {
          let surfaceRotation: SurfaceRotationOptions = { lock: this.isLock };
          this.myXComponentController.setXComponentSurfaceRotation(surfaceRotation);
          console.info("Surface getXComponentSurfaceRotation lock = " +
          this.myXComponentController.getXComponentSurfaceRotation().lock);
        })
        .width(this.xcWidth)
        .height(this.xcHeight)
      Button("Draw")
        .onClick(() => {
          let surfaceId = this.myXComponentController.getXComponentSurfaceId();
          nativeRender.DrawPattern(BigInt(surfaceId));
        })
    }
  }
}
```

### Example 3: Drawing Content on the XComponent Using a Canvas Object

From API version 20, this example returns a canvas object by calling [lockCanvas](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#lockcanvas), calls the corresponding drawing API via the canvas object, and then calls [unlockCanvasAndPost](arkts-arkui-xcomponent-comp-xcomponentcontroller-c.md#unlockcanvasandpost) to draw content on the XComponent.



```TypeScript
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  private xcController: XComponentController = new XComponentController();
  private mCanvas: DrawingCanvas | null = null;

  build() {
    Column() {
      XComponent({ type: XComponentType.SURFACE, controller: this.xcController })
        .width("80%")
        .height("80%")
        .onLoad(() => {
          this.mCanvas = this.xcController.lockCanvas();
          if (this.mCanvas) {
            this.mCanvas.drawColor(255, 240, 250, 255); // The entire XComponent area must be completely redrawn before each drawing. You can call this method to implement it.
            const brush = new drawing.Brush(); // Create a brush object.
            brush.setColor({ // Set the color of the brush.
              alpha: 255,
              red: 39,
              green: 135,
              blue: 217
            });
            this.mCanvas.attachBrush(brush); // Attach the brush to the canvas.
            this.mCanvas.drawRect({ // Draw a rectangle.
              left: 300,
              right: 800,
              top: 100,
              bottom: 800
            });
            this.mCanvas.detachBrush(); // Detach the brush from the canvas.
            this.xcController.unlockCanvasAndPost(this.mCanvas);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 4: Implementing an Immersive Effect

From API version 20, the setXComponentSurfaceRect API is called to set the surface display area to achieve the immersive effect.



```TypeScript
// xxx.ets
import { display } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  private xcController: XComponentController = new XComponentController();
  private mCanvas: DrawingCanvas | null = null;
  @State screenWidth: number = 0;
  @State screenHeight:number = 0;
  aboutToAppear() {
    try {
      const displayClass = display.getDefaultDisplaySync();
      this.screenWidth = displayClass.width;
      this.screenHeight = displayClass.height;
    } catch (error) {
      console.error(`Failed to get default display. Code: ${error.code}, message: ${error.message}`);
    }
  }

  build() {
    Column() {
      XComponent({ type: XComponentType.SURFACE, controller: this.xcController })
        .width('100%')
        .height('100%')
        .onLoad(() => {
          // Set the surface size. If the size is too large, the drawing time may be long.
          this.xcController.setXComponentSurfaceRect({surfaceWidth: this.screenWidth, surfaceHeight: this.screenHeight, offsetX: 0, offsetY: 0});
          this.mCanvas = this.xcController.lockCanvas();
          if (this.mCanvas) {
            this.mCanvas.drawColor(255, 39, 135, 217); // This method must be called to redraw the entire XComponent area before each drawing.
            this.xcController.unlockCanvasAndPost(this.mCanvas);
          }
        })
        .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]);
    }
    .height('100%')
    .width('100%')
  }
}
```
