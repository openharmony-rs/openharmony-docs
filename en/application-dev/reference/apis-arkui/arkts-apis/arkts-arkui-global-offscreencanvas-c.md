# OffscreenCanvas

OffscreenCanvas provides a Canvas object that can be rendered off-screen. It works in both window and Web worker environments.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number)
```

The width of the offScreen Canvas object The height of the offScreen Canvas object

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes |  |
| height | number | Yes |  |

## getContext

```TypeScript
getContext(contextId: "2d", options?: CanvasRenderingContext2DSettings): OffscreenCanvasRenderingContext2D
```

Gets the context object for off-screen drawing.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contextId | "2d" | Yes | creates a CanvasRenderingContext2D object representing a two-dimensional rendering context. |
| options | CanvasRenderingContext2DSettings | No | object representing a three-dimensional rendering context. |

**Return value:**

| Type | Description |
| --- | --- |
| OffscreenCanvasRenderingContext2D | a render canvas for the offScreen Canvas object. |

## toDataURL

```TypeScript
toDataURL(type?: string, quality?: number): string
```

Converts the draw contents of the current off-screen draw object to a string in the form of a Blob.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | No | indicating the image format. |
| quality | number | No | between 0 and 1 indicating image quality if the type option is image/jpeg or image/webp. |

**Return value:**

| Type | Description |
| --- | --- |
| string | A Promise returning a Blob object representing the image contained in the canvas. |

## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

Converts the draw content in the current off-screen draw object to a Bitmap object.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ImageBitmap](arkts-arkui-global-imagebitmap-c.md) | Returns An ImageBitmap object. |

## height

```TypeScript
height: number
```

The height of the offScreen Canvas object

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

The width of the offScreen Canvas object

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
