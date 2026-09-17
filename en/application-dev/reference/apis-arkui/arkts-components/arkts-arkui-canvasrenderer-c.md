# CanvasRenderer

After the **CanvasRenderingContext2D** object is bound to the **Canvas** component, you can draw shapes, texts, and images on the **Canvas** component.

> **NOTE:** 
> 
> * It is recommended that the **CanvasRenderingContext2D** object and the **Canvas** component be encapsulated into the same custom component, ensuring a one-to-one correspondence and consistent lifecycle between them.
> 
> * When you call drawing APIs in this module, the commands are stored in the associated **Canvas**component's command queue. These commands are only executed when the current frame enters the rendering phase and the associated **Canvas** component is visible. Therefore, when the **Canvas** component is invisible (for example, off-screen or hidden), avoid frequent drawing calls to prevent command queue buildup and excessive memory usage.
> 
> * When the width or height of the **Canvas** component exceeds 8000 px, rendering via the CPU causes significant performance degradation.

@extends CanvasPath

**Inheritance/Implementation:** CanvasRenderer extends [CanvasPath](arkts-arkui-canvaspath-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## beginPath

```TypeScript
beginPath(): void
```

Creates a drawing path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearRect

```TypeScript
clearRect(x: number, y: number, w: number, h: number): void
```

Clears the content in a rectangle on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |

## clip

```TypeScript
clip(fillRule?: CanvasFillRule): void
```

Sets the current path to a clipping path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-arkui-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to clip.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

## clip

```TypeScript
clip(path: Path2D, fillRule?: CanvasFillRule): void
```

Sets a specified path as the clipping path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | **Path2D** path to clip.<br>**undefined** and **null** are treated as invalid values. |
| fillRule | [CanvasFillRule](arkts-arkui-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to clip.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

## createConicGradient

```TypeScript
createConicGradient(
    startAngle: number,
    x: number,
    y: number
  ): CanvasGradient
```

Creates a conic gradient.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startAngle | number | Yes | Angle at which the gradient starts. The angle measurement starts horizontally from the right side of the center and moves clockwise.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid.<br>Unit: radian |
| x | number | Yes | X-coordinate of the center of the conic gradient.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the center of the conic gradient.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid.<br> Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient on the canvas. |

## createImageData

```TypeScript
createImageData(sw: number, sh: number): ImageData
```

Creates a blank ImageData object of a specified size. This API involves time-consuming memory copy. Therefore, avoid frequent calls to it. The createImageData example is identical to the putImageData example.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sw | number | Yes | Width of the **ImageData** object.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the **ImageData** object.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-imagedata-c.md) | New **ImageData** object. |

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

Creates an **ImageData** object with the same width and height of an existing **ImageData** object. This API involves time-consuming memory copy. Therefore, avoid frequent calls to it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-imagedata-c.md) | Yes | Existing **ImageData** object.<br>Values **undefined** and **null** are treated as **ImageData** with its width and height set to **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-imagedata-c.md) | New **ImageData** object. |

## createLinearGradient

```TypeScript
createLinearGradient(x0: number, y0: number, x1: number, y1: number): CanvasGradient
```

Creates a linear gradient.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x0 | number | Yes | X-coordinate of the start point.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br> Default unit: vp |
| y0 | number | Yes | Y-coordinate of the start point.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br> Default unit: vp |
| x1 | number | Yes | X-coordinate of the end point.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br> Default unit: vp |
| y1 | number | Yes | Y-coordinate of the end point.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br> Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient on the canvas. |

## createPattern

```TypeScript
createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null
```

Creates a pattern for image filling based on a specified source image and repetition mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-imagebitmap-c.md) | Yes | Source image. For details, see **ImageBitmap**.<br>**undefined** and **null** are treated as invalid values. |
| repetition | string &#124; null | Yes | Repetition mode.<br>**'repeat'**: The image is repeated along both the x-axis and y-axis.<br>**'repeat-x'**: The image is repeated along the x-axis.<br> **'repeat-y'**: The image is repeated along the y-axis.<br>**'no-repeat'**: The image is not repeated.<br>**'clamp'**: Coordinates outside the original bounds are clamped to the edge of the image.<br>**'mirror'**: The image is mirrored with each repetition along the x-axis and y-axis.<br> **undefined** and **null** are treated as invalid values. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasPattern](arkts-arkui-canvaspattern-i.md) &#124; null | Pattern for image filling based on a specified source image and repetition mode. |

## createRadialGradient

```TypeScript
createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number): CanvasGradient
```

Creates a radial gradient.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x0 | number | Yes | X-coordinate of the center of the start circle.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values. <br>Default unit: vp |
| y0 | number | Yes | Y-coordinate of the center of the start circle.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values. <br>Default unit: vp |
| r0 | number | Yes | Radius of the start circle, which must be a non-negative finite number.<br> If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |
| x1 | number | Yes | X-coordinate of the center of the end circle.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values. <br>Default unit: vp |
| y1 | number | Yes | Y-coordinate of the center of the end circle.<br>If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values. <br>Default unit: vp |
| r1 | number | Yes | Radius of the end circle, which must be a non-negative finite number.<br> If the value is **undefined** or **null**, this API returns **undefined**. **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient on the canvas. |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number): void
```

Draws an image on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number | Yes | X-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number, dw: number, dh: number): void
```

Draws an image by stretching or compressing it to the specified dimensions.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number | Yes | X-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dw | number | Yes | Width of the drawing area. If the width of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dh | number | Yes | Height of the drawing area. If the height of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |

## drawImage

```TypeScript
drawImage(
    image: ImageBitmap | PixelMap,
    sx: number,
    sy: number,
    sw: number,
    sh: number,
    dx: number,
    dy: number,
    dw: number,
    dh: number,
  ): void
```

Draws a cropped portion of an image by stretching or compressing it to the specified dimensions.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| sx | number | Yes | X-coordinate of the top-left corner of the rectangle used to crop the source image.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sy | number | Yes | Y-coordinate of the top-left corner of the rectangle used to crop the source image.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sw | number | Yes | Target width to crop the source image.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sh | number | Yes | Target height to crop the source image.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| dx | number | Yes | X-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-coordinate of the top-left corner of the drawing area on the canvas.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dw | number | Yes | Width of the drawing area.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed. If the width of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Default unit: vp |
| dh | number | Yes | Height of the drawing area.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed. If the height of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Default unit: vp |

## fill

```TypeScript
fill(fillRule?: CanvasFillRule): void
```

Fills the current path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-arkui-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to fill.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

## fill

```TypeScript
fill(path: Path2D, fillRule?: CanvasFillRule): void
```

Fills a specified path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | **Path2D** path to fill.<br>**undefined** and **null** are treated as invalid values. |
| fillRule | [CanvasFillRule](arkts-arkui-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to fill.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

## fillRect

```TypeScript
fillRect(x: number, y: number, w: number, h: number): void
```

Fills a rectangle on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |

## fillText

```TypeScript
fillText(text: string, x: number, y: number, maxWidth?: number): void
```

Draws filled text on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to draw.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| x | number | Yes | X-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| maxWidth | number | No | Maximum width allowed for the text.<br>**null** is treated as an invalid value and no rendering will be performed. **undefined**, **NaN**, or **Infinity** is treated as the default value.<br>Default value: no width restriction<br>Default unit: vp |

## getImageData

```TypeScript
getImageData(sx: number, sy: number, sw: number, sh: number): ImageData
```

Obtains the **ImageData** object created with the pixels within the specified area on the canvas. This API involves time-consuming memory copy. Therefore, avoid frequent calls to it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | X-coordinate of the top-left corner of the output area.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sy | number | Yes | Y-coordinate of the top-left corner of the output area.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sw | number | Yes | Width of the output area.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the output area.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-imagedata-c.md) | New **ImageData** object. |

## getLineDash

```TypeScript
getLineDash(): number[]
```

Obtains the dash line style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Interval of alternate line segments and the length of spacing.<br>Values undefined and null are treated as invalid.<br>Default unit: vp |

## getPixelMap

```TypeScript
getPixelMap(sx: number, sy: number, sw: number, sh: number): PixelMap
```

Obtains the **PixelMap** object created with the pixels within the specified area on the canvas. This API involves time-consuming memory copy. Therefore, avoid frequent calls to it.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | X-coordinate of the top-left corner of the output area.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sy | number | Yes | Y-coordinate of the top-left corner of the output area.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sw | number | Yes | Width of the output area.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the output area.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-arkui-pixelmap-t.md) | **PixelMap** object. |

## getTransform

```TypeScript
getTransform(): Matrix2D
```

Obtains the current transformation matrix being applied to the context.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](../arkts-apis/arkts-arkui-matrix2d-c.md) | Current transformation matrix applied to the context. |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

Returns a **TextMetrics** object used to obtain the width of specified text. Note that the width obtained may vary by device.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to measure. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextMetrics](arkts-arkui-textmetrics-i.md) | **TextMetrics** object.<br>If the input value is **undefined** or **null**, the value is calculated based on "undefined" or "null". |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: number | string, dy: number | string): void
```

Puts an **ImageData** object onto a rectangular area on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-imagedata-c.md) | Yes | **ImageData** object with pixels to put onto the canvas.<br> **undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number &#124; string | Yes | X-axis offset of the rectangular area on the canvas.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dy | number &#124; string | Yes | Y-axis offset of the rectangular area on the canvas.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |

## putImageData

```TypeScript
putImageData(
    imageData: ImageData,
    dx: number | string,
    dy: number | string,
    dirtyX: number | string,
    dirtyY: number | string,
    dirtyWidth: number | string,
    dirtyHeight: number | string
  ): void
```

Fills the new rectangular area with the **ImageData** data after cropping.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-imagedata-c.md) | Yes | **ImageData** object with pixels to put onto the canvas.<br> **undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number &#124; string | Yes | X-axis offset of the rectangular area on the canvas.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dy | number &#124; string | Yes | Y-axis offset of the rectangular area on the canvas.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dirtyX | number &#124; string | Yes | X-axis offset of the upper left corner of the rectangular area relative to that of the source image.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| dirtyY | number &#124; string | Yes | Y-axis offset of the upper left corner of the rectangular area relative to that of the source image.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| dirtyWidth | number &#124; string | Yes | Width of the rectangular area to crop the source image.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dirtyHeight | number &#124; string | Yes | Height of the rectangular area to crop the source image.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |

## reset

```TypeScript
reset(): void
```

Resets this **CanvasRenderingContext2D** object to its default state and clears the background buffer, drawing state stack, defined paths, and styles.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resetTransform

```TypeScript
resetTransform(): void
```

Resets the current transform to the identity matrix.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## restore

```TypeScript
restore(): void
```

Restores the saved drawing context.

> **NOTE:** 
> 
> When the number of calls to **restore()** does not exceed the number of calls to **save()**,
> this API pops the saved drawing state from the stack and restores the attributes, clipping
> path, and transformation matrix of the **CanvasRenderingContext2D** object.<br>
> If the number of calls to **restore()** exceeds the number of calls to **save()**, this API
> does nothing.<br>
> If there is no saved state, this API does nothing.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## restoreLayer

```TypeScript
restoreLayer(): void
```

Restores the image transformation and cropping state to the state before **saveLayer**, and then draws the layer onto the canvas. For the sample code, see the code for **saveLayer**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(angle: number): void
```

Rotates a canvas clockwise around its coordinate axes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Clockwise rotation angle. You can convert degrees to radians using the following formula: degree * Math.PI/180.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br>Unit: radian |

## save

```TypeScript
save(): void
```

Saves the current drawing context.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## saveLayer

```TypeScript
saveLayer(): void
```

Saves this layer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: number, y: number): void
```

Scales the canvas based on the given scale factors.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal scale factor.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| y | number | Yes | Vertical scaling factor. Negative numbers are not supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |

## setLineDash

```TypeScript
setLineDash(segments: number[]): void
```

Sets the dash line style.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| segments | number[] | Yes | An array of numbers that specify distances to alternately draw a line and a gap.<br>**undefined** and **null** are treated as invalid values.<br> Default unit: vp |

## setPixelMap

```TypeScript
setPixelMap(value?: PixelMap): void
```

Draws the input **PixelMap** object on the canvas. The example is the same as that of **getPixelMap**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PixelMap](arkts-arkui-pixelmap-t.md) | No | **PixelMap** object that contains pixel values.<br> **undefined** and **null** are treated as invalid values and no rendering will be performed.<br>Default value: **null** |

## setTransform

```TypeScript
setTransform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

Resets the existing transformation matrix and creates a new transformation matrix by using the same parameters as the **transform()** API.

> **NOTE:** 
> 
> The coordinates of each point in the graph after transformation can be calculated
> using the following formula:
> 
> **x** and **y** represent coordinates before transformation, and **x'** and **y'**
> represent coordinates after transformation.
> 
> - x' = `a * x + c * y + e`
> 
> - y' = `b * x + d * y + f`

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | **scaleX**: horizontal scaling value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| b | number | Yes | **skewY**: vertical skewing value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| c | number | Yes | **skewX**: horizontal skewing value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| d | number | Yes | **scaleY**: vertical scaling value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| e | number | Yes | **translateX**: horizontal translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| f | number | Yes | **translateY**: vertical translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

Resets the current transformation to the identity matrix, and then creates a new transformation matrix based on the specified **Matrix2D** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | [Matrix2D](../arkts-apis/arkts-arkui-matrix2d-c.md) | No | Transformation matrix.<br>**undefined** and **null** are treated as invalid values.<br>Default value: **null** |

## stroke

```TypeScript
stroke(): void
```

Strokes (outlines) this path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stroke

```TypeScript
stroke(path: Path2D): void
```

Strokes (outlines) a specified path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | Specified stroke path object |

## strokeRect

```TypeScript
strokeRect(x: number, y: number, w: number, h: number): void
```

Draws an outlined rectangle on the canvas without filling its interior.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the rectangle's top-left corner.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br>Default unit: vp |

## strokeText

```TypeScript
strokeText(text: string, x: number, y: number, maxWidth?: number): void
```

Draws stroked text on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to draw.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| x | number | Yes | X-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no rendering will be performed.<br> Default unit: vp |
| maxWidth | number | No | Maximum width of the text.<br>**null** is treated as an invalid value and no rendering will be performed. **undefined**, **NaN**, or **Infinity** is treated as the default value.<br>Default unit: vp<br>Default value: no width restriction |

## transferFromImageBitmap

```TypeScript
transferFromImageBitmap(bitmap: ImageBitmap): void
```

Displays the specified **ImageBitmap** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bitmap | [ImageBitmap](arkts-arkui-imagebitmap-c.md) | Yes | **ImageBitmap** object to display. |

## transform

```TypeScript
transform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

Defines a transformation matrix. To transform a graph, you only need to set parameters of the matrix. The coordinates of the graph are multiplied by the matrix values to obtain new coordinates of the transformed graph. You can use the matrix to implement multiple transform effects.

> **NOTE:** 
> 
> The coordinates of each point in the graph after transformation can be calculated
> using the following formula:
> 
> **x** and **y** represent coordinates before transformation, and **x'** and **y'**
> represent coordinates after transformation.
> 
> - x' = `a * x + c * y + e`
> 
> - y' = `b * x + d * y + f`

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | Cell at row 1, column 1 of the transformation matrix. **scaleX**: horizontal scaling value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| b | number | Yes | Cell at row 2, column 1 of the transformation matrix. **skewY**: vertical skewing value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| c | number | Yes | Cell at row 1, column 2 of the transformation matrix. **skewX**: horizontal skewing value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| d | number | Yes | Cell at row 2, column 2 of the transformation matrix. **scaleY**: vertical scaling value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| e | number | Yes | Cell at row 1, column 3 of the transformation matrix. **translateX**: horizontal translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br> Default unit: vp |
| f | number | Yes | Cell at row 2, column 3 of the transformation matrix. **translateY**: vertical translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br> Default unit: vp |

## translate

```TypeScript
translate(x: number, y: number): void
```

Moves the origin of the coordinate system.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance to translate on the x-axis.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Distance to translate on the y-axis.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## antialias

```TypeScript
antialias: boolean | undefined
```

Sets whether to enable anti-aliasing for drawing graphics and text. Setting this API overrides the anti-aliasing effect in [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md). If this API is not specified, the default value is **undefined** and the anti-aliasing effect in [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) is used.

Whether to enable anti-aliasing for drawing graphics and text.

**true**: Anti-aliasing is enabled. **false**: Anti-aliasing is disabled.

When the value is **undefined**, the anti-aliasing effect in [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) is used.

**Type:** boolean &#124; undefined

**Default:** undefined

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: CanvasDirection
```

Sets the text direction. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

For details, see [CanvasDirection](arkts-arkui-canvasdirection-t.md).

Default value: **"inherit"**

**Type:** [CanvasDirection](arkts-arkui-canvasdirection-t.md)

**Default:** inherit

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillStyle

```TypeScript
fillStyle: string | number | CanvasGradient | CanvasPattern
```

Sets the fill color for rendering. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

- When the type is string, this attribute indicates the color of the fill area. For details about  
the color format, see the description for the string type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is number, this attribute indicates the color of the fill area. Fully transparent  
colors are not supported. For details about the color format, see the description for the number type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is **CanvasGradient**, this attribute indicates a gradient object, which is created  
via the [createLinearGradient](#createlineargradient) API.

- When the type is **CanvasPattern**, this attribute indicates a pattern, which is created via the [createPattern](#createpattern) API.

Default value: **'#000000'** (black)

Invalid values do not take effect. The effect before the setting is retained.

**Type:** string &#124; number &#124; [CanvasGradient](arkts-arkui-canvasgradient-c.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-i.md)

**Default:** #000000 (black)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## filter

```TypeScript
filter: string
```

Sets the filter for an image. Any number of filters can be combined. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

> **NOTE:** 
> 
> The resources used in this example are not located in the **src**
> **main**
> **resource** directory. Starting
> from DevEco Studio 6.0.0 Beta2, the resources that are located outside the **resources** directory are not
> packaged by default when a project or module is created. To package these resources, go to **buildOption** in the
> module's **build-profile.json5** file
> **resOptions**
> **copyCodeResource**, and set **enable** to **true**.
> For details, see the description of copyCodeResource.

Available values are as follows:

- **'none'**: no filter effect.  
- **'blur(`&lt;length&gt;`)'**: applies the Gaussian blur to the image. The value must be greater  
than or equal to 0. The unit can be px, vp, or rem. The default value is **blur(0px)**.  
- **'brightness([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: applies a linear multiplier to the image to  
adjust its brightness. The value can be a number or a percentage, and must be greater than or equal to 0. The default value is **brightness(1)**.  
- **'contrast([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: adjusts the contrast of the image. The value  
can be a number or a percentage, and must be greater than or equal to 0. The default value is **contrast(1)**.  
- **'grayscale([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: converts the image to grayscale. The value can  
be a number or a percentage, and must be within the range of [0, 1]. The default value is **grayscale(0)**.  
- **'hue-rotate(`&lt;angle&gt;`)'**: applies hue rotation to the image. The value ranges from  
**0deg** to **360deg**. The default value is **hue-rotate(0deg)**.  
- **'invert([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: inverts the input image. The value can be a number  
or a percentage, and must be within the range of [0, 1]. The default value is **invert(0)**.  
- **'opacity([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: adjusts the opacity of the image. The value can be  
a number or a percentage, and must be within the range of [0, 1]. The default value is **opacity(1)**.  
- **'saturate([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: adjusts the saturation of the image. The value  
can be a number or a percentage, and must be greater than or equal to 0. The default value is **saturate(1)**.  
- **'sepia([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: converts the image to sepia. The value can be a  
number or a percentage, and must be within the range of [0, 1]. The default value is **sepia(0)**.

**Type:** string

**Default:** none

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font: string
```

Sets the text font. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Syntax: ctx.font = 'font-style font-weight font-size font-family'

- (Optional) **font-style**: font style. Available values are **normal** and **italic**.

- (Optional) **font-weight**: font weight. Available values are as follows: **normal**,  
**bold**, **bolder**, **lighter**, **100**, **200**, **300**, **400**, **500**, **600**, **700**, **800**, **900**.

- (Optional) **font-size**: font size and line height. The unit can be px or vp and must  
be specified.

- (Optional) **font-family**: font family. Available values are **sans-serif**,  
**serif**, and **monospace**.

Starting from API version 20, this API is used to set registered custom fonts (the DevEco Studio Previewer does not support custom fonts). You can register a custom font in either of the following ways:

Register a custom font by calling the asynchronous API this.uiContext.getFont().registerFont of ArkUI. Immediate rendering after calling this API may result in the custom font not taking effect.

Directly call the fontCollection.[loadFontSync](../../../reference/apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) API of the font engine to register the custom font. In this case, the **fontCollection** instance must be **text.FontCollection.getGlobalInstance()** because the component loads fonts from this instance by default. If you use another instance, the custom font may not take effect.

**Type:** string

**Default:** normal normal 14px sans-serif

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalAlpha

```TypeScript
globalAlpha: number
```

Sets the opacity. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

The value range is [0.0, 1.0]. **0.0** indicates completely transparent, and **1.0** indicates completely opaque. If the set value is less than 0.0, **0.0** will be used. If the set value is greater than 1.0, **1.0** will be used.

In versions earlier than API version 18, if **NaN** or **Infinity** is set, rendering APIs cannot be called for rendering after this API. In API version 18 and later versions, if **NaN** or **Infinity** is set, the current API does not take effect, and other rendering APIs with valid arguments can be called normally.

Default value: **1.0**

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalCompositeOperation

```TypeScript
globalCompositeOperation: string
```

Sets the composite operation. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Available values are as follows:

| Name | Description |  
| ------ | ------ |  
| source-over | Displays the new drawing above the existing drawing. Default value. |
| source-atop | Displays the new drawing on the top of the existing drawing. |
| source-in | Displays the new drawing inside the existing drawing. |
| source-out | Displays part of the new drawing that is outside of the existing drawing. |
| destination-over | Displays the existing drawing above the new drawing. |
| destination-atop | Displays the existing drawing on the top of the new drawing. |
| destination-in | Displays the existing drawing inside the new drawing. |
| destination-out | Displays the existing drawing outside the new drawing. |
| lighter | Displays both the new and existing drawing. |
| copy | Displays the new drawing and neglects the existing drawing. |
| xor | Combines the new drawing and existing drawing using the XOR operation. |

Default value: **'source-over'**

**Type:** string

**Default:** source-over

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingEnabled

```TypeScript
imageSmoothingEnabled: boolean
```

Indicates whether to apply image smoothing adjustments when drawing images. The value **true** means to enable smoothing, and **false** means to disable it. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned. Default value: **true**.  
> **NOTE:** 
> 
> The resources used in this example are not located in the **src**
> **main**
> **resource** directory. Starting
> from DevEco Studio 6.0.0 Beta2, the resources that are located outside the **resources** directory are not
> packaged by default when a project or module is created. To package these resources, go to **buildOption** in the
> module's **build-profile.json5** file
> **resOptions**
> **copyCodeResource**, and set **enable** to **true**.
> For details, see the description of copyCodeResource in **resOptions**.

**Type:** boolean

**Default:** true

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingQuality

```TypeScript
imageSmoothingQuality: ImageSmoothingQuality
```

Sets the image smoothing quality when **imageSmoothingEnabled** is set to **true**. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned. For details, see [ImageSmoothingQuality](arkts-arkui-imagesmoothingquality-t.md). Default value: **"low"**  
> **NOTE:** 
> 
> The resources used in this example are not located in the **src**
> **main**
> **resource** directory. Starting
> from DevEco Studio 6.0.0 Beta2, the resources that are located outside the **resources** directory are not
> packaged by default when a project or module is created. To package these resources, go to **buildOption** in the
> module's **build-profile.json5** file
> **resOptions**
> **copyCodeResource**, and set **enable** to **true**.
> For details, see the description of copyCodeResource in **resOptions**.

**Type:** [ImageSmoothingQuality](arkts-arkui-imagesmoothingquality-t.md)

**Default:** low

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing: LengthMetrics | string
```

Sets the letter spacing. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Spacing between characters.

When the LengthMetrics type is used:

The spacing is set according to the specified unit.

The FP, PERCENT, and LPX units are not supported and will be treated as invalid values.

Negative and fractional values are supported. When set to a fraction, the spacing is not rounded.

When the string type is used:

Percentage values are not supported and will be treated as invalid.

Negative and decimal values are supported. When set to a decimal value, the spacing is not rounded.

If no unit is specified (for example, **letterSpacing = '10'**) and **LengthMetricsUnit** is not set, the default unit is vp.

If **LengthMetricsUnit** is set to px, the default unit is px.

If the value of **letterSpacing** is specified with a unit (for example, **letterSpacing='10vp'**), the letter spacing is set based on the specified unit.

Default value: **0** (Invalid values are treated as the default value.)

> **NOTE:** 
> 
> The LengthMetrics type is recommended for better performance.

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) &#124; string

**Default:** 0vp

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineCap

```TypeScript
lineCap: CanvasLineCap
```

Sets the line caps. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, undefined will be returned.

**Type:** [CanvasLineCap](arkts-arkui-canvaslinecap-t.md)

**Default:** butt

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineDashOffset

```TypeScript
lineDashOffset: number
```

Sets the dashed line offset of the canvas. The value is of the float type. This attribute takes effect only when **setLineDash** is set. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **0.0**

Default unit: vp

Invalid values **NaN** and **Infinity** are treated as the default value.

**Type:** number

**Default:** 0.0

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineJoin

```TypeScript
lineJoin: CanvasLineJoin
```

Sets the line join. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned. For details, see [CanvasLineJoin](arkts-arkui-canvaslinejoin-t.md). <br>Available values are as follows: <br>- **'round'**: The shape used to join line segments is a sector, whose radius at the rounded corner is equal to the line width. <br>- **'bevel'**: The shape used to join line segments is a triangle. The rectangular corner of each line is independent. <br>- **'miter'**: The shape used to join line segments has a mitered corner by extending the outside edges of the lines until they meet. You can view the effect of this attribute in **miterLimit**. <br>Default value: **'miter'**

**Type:** [CanvasLineJoin](arkts-arkui-canvaslinejoin-t.md)

**Default:** miter

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineWidth

```TypeScript
lineWidth: number
```

Sets the line width. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **1** (px)

Default unit: vp

The value does not support **0** or negative numbers. **0**, negative numbers, and **NaN** are handled as the default value. The value **Infinity** is invalid and no drawing is performed.

**Type:** number

**Default:** 1(px)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## miterLimit

```TypeScript
miterLimit: number
```

Sets the miter limit, which specifies the distance between the inner and outer angles at line joins. This attribute takes effect only when **lineJoin** is set to **miter**. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **10px**

Unit: px

The value of **miterLimit** cannot be **0** or a negative number. Values of **0**, negative numbers, and **NaN** are handled with the default value. **Infinity** will cause an exception on the **miterLimit** attribute.

**Type:** number

**Default:** 10(px)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowBlur

```TypeScript
shadowBlur: number
```

Sets the blur level for drawing shadows. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Blur level. A larger value produces a greater blur effect. The value is of float type and must be greater than or equal to 0.

Default value: **0.0**

Unit: px

The value of **shadowBlur** cannot be a negative number. A negative number, **NaN**, and **Infinity** are treated as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowColor

```TypeScript
shadowColor: string
```

Sets the shadow color. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

For details about the color format, see the description for the string type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

Default value: **'#00000000'** (transparent black)

**Type:** string

**Default:** transparent black

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetX

```TypeScript
shadowOffsetX: number
```

Sets the horizontal offset between the drawn shadow and the original object. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **0.0**

Default unit: vp

Invalid values **NaN** and **Infinity** are treated as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetY

```TypeScript
shadowOffsetY: number
```

Sets the vertical offset between the drawn shadow and the original object. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **0.0**

Default unit: vp

Invalid values **NaN** and **Infinity** are treated as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeStyle

```TypeScript
strokeStyle: string | number | CanvasGradient | CanvasPattern
```

Sets the stroke color. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

- When the type is string, this attribute indicates the stroke color. For details about  
the color format, see the description for the string type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is number, this attribute indicates the stroke color. Fully transparent  
colors are not supported. For details about the color format, see the description for the number type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is **CanvasGradient**, this attribute indicates a gradient object, which is  
created via the [createLinearGradient](#createlineargradient) API.

- When the type is **CanvasPattern**, this attribute indicates a pattern, which is created  
via the createPattern API.

Default value: **'#000000'** (black)

Invalid values do not take effect. The effect before the setting is retained.

**Type:** string &#124; number &#124; [CanvasGradient](arkts-arkui-canvasgradient-c.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-i.md)

**Default:** #000000 (black)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign: CanvasTextAlign
```

Sets the text alignment type. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

In the **ltr** layout mode, the value **'start'** equals **'left'**. In the **rtl** layout mode, the value **'start'** equals **'right'**.

Default value: **'left'**

**Type:** [CanvasTextAlign](arkts-arkui-canvastextalign-t.md)

**Default:** left

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textBaseline

```TypeScript
textBaseline: CanvasTextBaseline
```

Sets the horizontal alignment baseline for text rendering. This attribute is write-only. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. If you attempt to read its current value, **undefined** will be returned.

Default value: **'alphabetic'**

**Type:** [CanvasTextBaseline](arkts-arkui-canvastextbaseline-t.md)

**Default:** alphabetic

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
