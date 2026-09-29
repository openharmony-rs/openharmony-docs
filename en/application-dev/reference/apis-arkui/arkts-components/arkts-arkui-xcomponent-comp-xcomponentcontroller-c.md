# XComponentController

```TypeScript
declare class XComponentController
```

Defines the controller of the **XComponent**. You can bind the controller to the **XComponent** to call the component APIs through the controller.

**Since:** 8

<!--Device-unnamed-declare class XComponentController--><!--Device-unnamed-declare class XComponentController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **XComponentController** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-constructor()--><!--Device-XComponentController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
xComponentController: XComponentController = new XComponentController();
```

## getXComponentContext

```TypeScript
getXComponentContext(): Object
```

Obtains the context of an **XComponent** object. This API works only when **type** of the **XComponent** is set to **SURFACE("surface")** or **TEXTURE**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-getXComponentContext(): Object--><!--Device-XComponentController-getXComponentContext(): Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Object | Context of the **XComponent** object. The APIs contained in the context are defined by developers. The context is passed as the first parameter of the **onLoad** callback. |

## getXComponentSurfaceId

```TypeScript
getXComponentSurfaceId(): string
```

Obtains the ID of the surface held by the **XComponent**. This API works only when **type** of the **XComponent** is **SURFACE("surface")** or **TEXTURE**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-getXComponentSurfaceId(): string--><!--Device-XComponentController-getXComponentSurfaceId(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the surface held by the **XComponent**. |

**Examples**

You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

```TypeScript
// xxx.ets

@Entry
  @Component
  struct Index {
    myXComponentController: XComponentController = new XComponentController();

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        XComponent({
          type: XComponentType.SURFACE,
          controller: this.myXComponentController
        })
          .onLoad(() => {
            let surfaceId: string = this.myXComponentController.getXComponentSurfaceId();
            console.info("XComponent SurfaceId: " + surfaceId);
          })
      }
    }
  }
```

## getXComponentSurfaceRect

```TypeScript
getXComponentSurfaceRect(): SurfaceRect
```

Obtains the display area for the surface held by the **XComponent**, including the width, height, and position coordinates relative to the upper left corner of the component. This API is only effective when the **XComponent** type is **SURFACE("surface")** or **TEXTURE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect--><!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | Rectangle of the surface held by the **XComponent**. |

## getXComponentSurfaceRotation

```TypeScript
getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>
```

Obtains whether the orientation of the surface held by this **XComponent** is locked when the screen rotates. This API is effective only when the **XComponent** type is **SURFACE** (**"surface"**).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>--><!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Required&lt;[SurfaceRotationOptions](arkts-arkui-xcomponent-comp-surfacerotationoptions-i.md)&gt; | Whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates. |

## lockCanvas

```TypeScript
lockCanvas(): DrawingCanvas | null
```

Obtains a canvas object for drawing content on the **XComponent** component. For details about the drawing methods, see [Canvas](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-canvas-c.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-XComponentController-lockCanvas(): DrawingCanvas | null--><!--Device-XComponentController-lockCanvas(): DrawingCanvas | null-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) &#124; null | Returns a Canvas for drawing into the surface created by XComponent. Returns null if the surface is not available. |

## onSurfaceChanged

```TypeScript
onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void
```

Triggered when the surface held by the **XComponent** has its size changed (including the time when the **XComponent** is created with the specified size). This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void--><!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | ID of the surface held by the **XComponent**. |
| rect | [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | Yes | Area for displaying the surface held by the **XComponent**. |

## onSurfaceCreated

```TypeScript
onSurfaceCreated(surfaceId: string): void
```

Triggered when the surface held by the **XComponent** is created. This API works only when **type** of the **XComponent** is set to **SURFACE("surface")** or **TEXTURE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void--><!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | ID of the surface held by the **XComponent**. |

## onSurfaceDestroyed

```TypeScript
onSurfaceDestroyed(surfaceId: string): void
```

Triggered when the surface held by the **XComponent** is destroyed. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void--><!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | ID of the surface held by the **XComponent**. |

## setXComponentSurfaceConfig

```TypeScript
setXComponentSurfaceConfig(config: SurfaceConfig):void
```

Sets the options of the surface created by the **XComponent**, which determine whether the surface held by the **XComponent** is considered opaque during rendering.

> **NOTE:** 
> 
> This API takes effect only when the type of **XComponent** is **TEXTURE** or **SURFACE**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void--><!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [SurfaceConfig](arkts-arkui-xcomponent-comp-surfaceconfig-i.md) | Yes | surface config |

## setXComponentSurfaceRect

```TypeScript
setXComponentSurfaceRect(rect: SurfaceRect): void
```

Sets the display area for the surface held by the **XComponent**, including the width, height, and position coordinates relative to the upper left corner of the component. This API is only effective when the **XComponent** type is **SURFACE("surface")** or **TEXTURE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void--><!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | Yes | Rectangle of the surface held by the **XComponent**. |

## setXComponentSurfaceRotation

```TypeScript
setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void
```

Sets whether to lock the orientation of the surface held by this **XComponent** when the screen rotates. This API is effective only when the **XComponent** type is **SURFACE** (**"surface"**).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void--><!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationOptions | [SurfaceRotationOptions](arkts-arkui-xcomponent-comp-surfacerotationoptions-i.md) | Yes | Whether to lock the orientation of the surface held by the current **XComponent** when the screen rotates. |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

Starts AI image analysis in the given settings. Before calling this API, make sure the AI image analyzer is [enabled](arkts-arkui-xcomponent-comp-attribute.md#enableanalyzer). This API uses a promise to return the result.

Because the image frame used for analysis is the one captured when this API is called, pay attention to the invoking time of this API.

If this API is repeatedly called before the execution is complete, an error callback is triggered.

> **NOTE:** 

> The image analysis type cannot be dynamically modified.
> 
> This API depends on device capabilities. If it is called on an incompatible device, an error code is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | Yes | Settings of the AI image analyzer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. It is used to indicate AI-based analysis is successfully executed. |

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

> If this API is called when the **startImageAnalyzer** API has not yet returned any result, an error callback is
> triggered.
> 
> This feature depends on device capabilities.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentController-stopImageAnalyzer(): void--><!--Device-XComponentController-stopImageAnalyzer(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## unlockCanvasAndPost

```TypeScript
unlockCanvasAndPost(canvas: DrawingCanvas):void
```

Submits the drawn content from a canvas object to the display area of the **XComponent** component and releases the canvas object.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas):void--><!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas):void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| canvas | [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) | Yes | The canvas previously obtained from lockCanvas. |

## setXComponentSurfaceSize

```TypeScript
setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void
```

Sets the width and height of the surface held by the **XComponent**. This API works only when **type** of the **XComponent** is set to **SURFACE("surface")** or **TEXTURE**.

Unit: px.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [setXComponentSurfaceRect](#setxcomponentsurfacerect)

<!--Device-XComponentController-setXComponentSurfaceSize(value: {    surfaceWidth: number;    surfaceHeight: number;  }): void--><!--Device-XComponentController-setXComponentSurfaceSize(value: {    surfaceWidth: number;    surfaceHeight: number;  }): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | {     surfaceWidth: number;     surfaceHeight: number;   } | Yes | Width and Height of the surface held by the XComponent. |
