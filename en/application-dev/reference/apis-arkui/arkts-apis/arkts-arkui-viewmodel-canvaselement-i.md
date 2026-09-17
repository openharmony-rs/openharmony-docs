# CanvasElement

&lt;canvas&gt; provides a rectangular canvas component for drawing graphics on the screen. You can control each pixel to draw on the canvas. &lt;canvas&gt; offers a variety of functions for drawing paths, rectangles, circles, text, and allows for adding images to it.

@extends Element @interface CanvasElement

**Inheritance/Implementation:** CanvasElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getContext("2d")

```TypeScript
getContext(type: "2d", options?: ContextAttrOptions): CanvasRenderingContext2D
```

Obtains the context of 2D canvas drawing. Only parameters related to 2D canvas drawing are supported. The return value is a 2D drawing object that provides specific 2D drawing operations.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "2d" | Yes | identifier defining the drawing context associated to the canvas. |
| options | [ContextAttrOptions](arkts-arkui-viewmodel-contextattroptions-i.md) | No | use this context attributes to creating rendering context. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasRenderingContext2D](arkts-arkui-viewmodel-canvasrenderingcontext2d-i.md) |  |

## getContext("webgl")

```TypeScript
getContext(type: "webgl", options?: WebGLContextAttributes): WebGLRenderingContext
```

Obtains the context of webgl canvas drawing. Only parameters related to webgl canvas drawing are supported. The return value is a webgl drawing object that provides specific webgl drawing operations.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "webgl" | Yes | identifier defining the drawing context associated to the canvas. |
| options | [WebGLContextAttributes](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-webgl-webglcontextattributes-i.md) | No | use this context attributes to creating rendering context. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLRenderingContext](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-webgl-webglrenderingcontext-i.md) |  |

## getContext("webgl2")

```TypeScript
getContext(type: "webgl2", options?: WebGLContextAttributes): WebGL2RenderingContext
```

Obtains the context of webgl2 canvas drawing. Only parameters related to webgl2 canvas drawing are supported. The return value is a webgl2 drawing object that provides specific webgl2 drawing operations.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "webgl2" | Yes | identifier defining the drawing context associated to the canvas. |
| options | [WebGLContextAttributes](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-webgl-webglcontextattributes-i.md) | No | use this context attributes to creating rendering context. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGL2RenderingContext](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-webgl2-webgl2renderingcontext-i.md) |  |

## toDataURL

```TypeScript
toDataURL(type?: string, quality?: number): string
```

Creates a data URI that contains the image display.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | No | A DOMString indicating the image format. The default type is image/png. |
| quality | number | No | A Number between 0 and 1 indicating image quality if the type option is image/jpeg or image/webp. If this argument is anything else, the default value for image quality is used. Other arguments are ignored. |

**Return value:**

| Type | Description |
| --- | --- |
| string |  |
