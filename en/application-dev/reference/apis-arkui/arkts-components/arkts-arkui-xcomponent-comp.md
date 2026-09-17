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
| options | [XComponentOptions](arkts-arkui-xcomponentoptions-i.md) | Yes | Options of the **XComponent**. |

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
| params | [NativeXComponentParameters](arkts-arkui-nativexcomponentparameters-i.md) | Yes | Options of the **XComponent**. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [NativeXComponentParameters](arkts-arkui-nativexcomponentparameters-i.md) | Defines the options of the **XComponent**. An XComponent created with such constructor parameters can pass its corresponding FrameNode object to the Native side, enabling the use of NDK APIs for surface lifecycle–related settings and [component event listening](../../../ui/ndk-listen-to-component-events.md). |
| [SurfaceConfig](arkts-arkui-surfaceconfig-i.md) | Describes whether the surface held by the **XComponent** is treated as opaque during rendering. |
| [SurfaceRect](arkts-arkui-surfacerect-i.md) | Describes the rectangle of the surface held by the **XComponent**. |
| [SurfaceRotationOptions](arkts-arkui-surfacerotationoptions-i.md) | Defines whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates. |
| [XComponentOptions](arkts-arkui-xcomponentoptions-i.md) | Defines the options of the **XComponent**. |

### Types

| Name | Description |
| --- | --- |
| [OnNativeLoadCallback](arkts-arkui-onnativeloadcallback-t.md) | Triggered after the surface held by **XComponent** is created. |

### Enums

| Name | Description |
| --- | --- |
| [HdrType](arkts-arkui-hdrtype-e.md) | Sets the HDR type of the XComponent. |

## Examples

```TypeScript
### Example 1: Enabling AI Image Analyzer

This example shows how to use the enableAnalyzer attribute to enable image AI analysis. You can use XComponentController to start or stop image AI analysis.

> NOTE
> 
> For details about the specific implementation of the drawing logic in this example (the implementation of functions related to nativeRender), see [ArkTS XComponent Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).


```

```TypeScript
### Example 2 (Locking During Surface Rotation)

Uses setXComponentSurfaceRotation to lock the Surface orientation during screen rotation so that it does not rotate with the screen.

> NOTE
> 
> For details about the implementation of the drawing logic in this example (the function implementation related to nativeRender), see [ArkTS XComponent Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).
```

```TypeScript
### Example 3: Drawing Content on the XComponent Using a Canvas Object

From API version 20, this example returns a canvas object by calling [lockCanvas](arkts-arkui-xcomponentcontroller-c.md#lockcanvas), calls the corresponding drawing API via the canvas object, and then calls [unlockCanvasAndPost](arkts-arkui-xcomponentcontroller-c.md#unlockcanvasandpost) to draw content on the XComponent.


```

```TypeScript
### Example 4: Implementing an Immersive Effect

From API version 20, the setXComponentSurfaceRect API is called to set the surface display area to achieve the immersive effect.


```

```TypeScript
### Example 5 (Setting Whether the Surface Held by XComponent Needs to Be Deemed Opaque During Rendering)

From API version 22, this example calls the [setXComponentSurfaceConfig](arkts-arkui-xcomponentcontroller-c.md#setxcomponentsurfaceconfig) API to set whether the surface held by the XComponent is considered opaque during rendering.

> NOTE
> 
> For details about the implementation of the drawing logic in this example (the function implementation related to nativeRender), see [ArkTS XComponent Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).
```
