# CanvasRenderer

```TypeScript
declare class CanvasRenderer extends CanvasPath
```

After the **CanvasRenderingContext2D** object is bound to the **Canvas** component, you can draw shapes, texts, and images on the **Canvas** component.

> **NOTE:** 
> 
> * It is recommended that the **CanvasRenderingContext2D** object and the **Canvas** component be encapsulated into the same custom component, ensuring a one-to-one correspondence and consistent lifecycle between them.
> 
> * When you call drawing APIs in this module, the commands are stored in the associated **Canvas**component's command queue. These commands are only executed when the current frame enters the rendering phase and the associated **Canvas** component is visible. Therefore, when the **Canvas** component is invisible (for example, off-screen or hidden), avoid frequent drawing calls to prevent command queue buildup and excessive memory usage.
> 
> * When the width or height of the **Canvas** component exceeds 8000 px, rendering via the CPU causes significant performance degradation.

@extends CanvasPath

**Inheritance/Implementation:** CanvasRenderer extends [CanvasPath](arkts-arkui-canvas-comp-canvaspath-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## beginPath

```TypeScript
beginPath(): void
```

Creates a new drawing path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clearRect

```TypeScript
clearRect(x: number, y: number, w: number, h: number): void
```

Clears the drawn content in the specified area.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| y | number | Yes | Y coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |

## clip

```TypeScript
clip(fillRule?: CanvasFillRule): void
```

Sets the current path as the clipping path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to clip.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

<a id="clip-1"></a>

## clip

```TypeScript
clip(path: Path2D, fillRule?: CanvasFillRule): void
```

Sets the specified path as the clipping path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | **Path2D** path to clip.<br>**undefined** and **null** are treated as invalid values. |
| fillRule | [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to clip.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

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
| startAngle | number | Yes | Start angle of the gradient. The angle measurement starts from the right side of the center horizontally and moves clockwise.<br>Abnormal values **undefined** and **null** are processed as **0**, and **NaN** and **Infinity** are processed as invalid values. <br>Unit: radian |
| x | number | Yes | X-coordinate of the center of the conic gradient.<br>Abnormal values **undefined** and **null** are processed as **0**, and **NaN** and **Infinity** are processed as invalid values.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the center of the conic gradient.<br>Abnormal values **undefined** and **null** are processed as **0**, and **NaN** and **Infinity** are processed as invalid values.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-canvas-comp-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient effect on the offscreen canvas. |

## createImageData

```TypeScript
createImageData(sw: number, sh: number): ImageData
```

Creates a new **ImageData** object with the specified width and height based on the current **ImageData** object. For details, see **ImageData**. This API involves memory copy and is time-consuming. Avoid frequent use. The example for **createImageData** is the same as that for **putImageData**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sw | number | Yes | Width of the **ImageData**.<br>The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the **ImageData**.<br>The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | New **ImageData** object. |

<a id="createimagedata-1"></a>

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

Creates a new **ImageData** object based on an existing **ImageData** object (without copying the image data). See **ImageData**. This API involves memory copy and is time-consuming. Avoid frequent use. For the **createImageData** example, see **putImageData**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | Yes | **ImageData** object to be copied.<br>The abnormal values **undefined** and **null** are processed as an **ImageData** object with width and height being **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | New **ImageData** object. |

## createLinearGradient

```TypeScript
createLinearGradient(x0: number, y0: number, x1: number, y1: number): CanvasGradient
```

Creates a linear gradient.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

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
| [CanvasGradient](arkts-arkui-canvas-comp-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient effect on the offscreen canvas. |

## createPattern

```TypeScript
createPattern(image: ImageBitmap, repetition: string | null): CanvasPattern | null
```

Creates a pattern for image filling based on a specified image and repetition mode.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) | Yes | Image source object. For details, see **ImageBitmap**.<br>An invalid value, such as **undefined** or **null**, is processed as an invalid value. |
| repetition | string &#124; null | Yes | Image repetition mode:<br>**'repeat'**: repeats the image along both the x-axis and y-axis;<br>**'repeat-x'**: repeats the image along the x-axis;<br> **'repeat-y'**: repeats the image along the y-axis;<br>**'no-repeat'**: does not repeat the image;<br>**'clamp'**: uses the edge color for the part that exceeds the original boundary when drawing outside it;<br>**'mirror'**: repeats and flips the image along both the x-axis and y-axis.<br>An invalid value, such as **undefined** or **null**, is processed as an invalid value. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasPattern](arkts-arkui-canvas-comp-canvaspattern-i.md) &#124; null | Pattern object created by specifying an image and repetition mode. |

## createRadialGradient

```TypeScript
createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number): CanvasGradient
```

Creates a radial gradient color.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

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
| [CanvasGradient](arkts-arkui-canvas-comp-canvasgradient-c.md) | New **CanvasGradient** object used to create a gradient effect on the offscreen canvas. |

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number): void
```

Draws an image.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number | Yes | X-coordinate of the upper left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-coordinate of the upper left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |

<a id="drawimage-1"></a>

## drawImage

```TypeScript
drawImage(image: ImageBitmap | PixelMap, dx: number, dy: number, dw: number, dh: number): void
```

Draws the image by stretching or compressing it.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| dx | number | Yes | X-axis position of the upper left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-axis position of the upper left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dw | number | Yes | Width of the drawing area. If the width of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dh | number | Yes | Height of the drawing area. If the height of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |

<a id="drawimage-2"></a>

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

Draws the image after cropping, stretching, or compressing it.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image resource. For details, see **ImageBitmap** or **PixelMap**.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| sx | number | Yes | X-coordinate of the top-left corner of the rectangle used to crop the source image.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sy | number | Yes | Y-coordinate of the top-left corner of the rectangle used to crop the source image.<br>Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sw | number | Yes | Target width to crop the source image.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| sh | number | Yes | Target height to crop the source image.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>If the type of **image** is **ImageBitmap**, the default unit is vp.<br>If the type of **image** is **PixelMap**, the default unit is px in versions earlier than API version 18 and vp in API version 18 and later. |
| dx | number | Yes | X-coordinate of the upper-left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dy | number | Yes | Y-coordinate of the upper-left corner of the drawing area.<br> Invalid values **undefined** and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed.<br>Default unit: vp |
| dw | number | Yes | Width of the drawing area.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed. If the width of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Default unit: vp |
| dh | number | Yes | Height of the drawing area.<br>Negative values, **undefined**, and **null** are treated as **0**. **NaN** and **Infinity** are treated as invalid and no rendering will be performed. If the height of the drawing area is different from that of the cropped image, the latter will be stretched or compressed to the former.<br>Default unit: vp |

## fill

```TypeScript
fill(fillRule?: CanvasFillRule): void
```

Fills the current path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillRule | [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to fill.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

<a id="fill-1"></a>

## fill

```TypeScript
fill(path: Path2D, fillRule?: CanvasFillRule): void
```

Fills the specified path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | **Path2D** path to fill.<br>**undefined** and **null** are treated as invalid values. |
| fillRule | [CanvasFillRule](arkts-arkui-canvas-comp-canvasfillrule-t.md) | No | Rule by which to determine whether a point is inside or outside the area to fill.<br>The options are **"nonzero"** and **"evenodd"**.<br>Invalid values **undefined** and **null** are treated as the default value.<br>Default value: **"nonzero"** |

## fillRect

```TypeScript
fillRect(x: number, y: number, w: number, h: number): void
```

Fills a rectangle.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| y | number | Yes | Y coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |

## fillText

```TypeScript
fillText(text: string, x: number, y: number, maxWidth?: number): void
```

Draws filled text.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to draw.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| x | number | Yes | X-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| maxWidth | number | No | Maximum width allowed for the text.<br>**null** is treated as an invalid value and no rendering will be performed. **undefined**, **NaN**, or **Infinity** is treated as the default value.<br>Default value: no width restriction<br>Default unit: vp |

## getImageData

```TypeScript
getImageData(sx: number, sy: number, sw: number, sh: number): ImageData
```

Creates an **ImageData** object from the pixels in the specified area of the current canvas. This API involves memory copy and is time-consuming. Avoid frequent use.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | X coordinate of the upper left corner of the output area.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **0**.<br>Default unit: vp |
| sy | number | Yes | Y coordinate of the upper left corner of the output area.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **0**.<br>Default unit: vp |
| sw | number | Yes | Width of the area to output.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the area to output.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | New **ImageData** object. |

## getLineDash

```TypeScript
getLineDash(): number[]
```

Obtains the dash line style of the current canvas.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Array that describes how line segments alternate and the spacing length.<br> The abnormal values **undefined** and **null** are treated as invalid values.<br>Default unit: vp |

## getPixelMap

```TypeScript
getPixelMap(sx: number, sy: number, sw: number, sh: number): PixelMap
```

Creates a **PixelMap** object from the pixels in the specified area of the current canvas. This API involves memory copy and is time-consuming. Avoid frequent use.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | X coordinate of the upper left corner of the area to output.<br> The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sy | number | Yes | Y coordinate of the upper left corner of the area to output.<br> The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| sw | number | Yes | Width of the area to output.<br>The abnormal values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| sh | number | Yes | Height of the area to output.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | New **PixelMap** object. |

## getTransform

```TypeScript
getTransform(): Matrix2D
```

Obtains the transform matrix currently applied to the context.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Matrix2D | The transformation matrix currently applied to the context. |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

Returns a text measurement object, through which the width of the specified text can be obtained.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

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
| [TextMetrics](arkts-arkui-canvas-comp-textmetrics-i.md) | Text metrics.<br>If an invalid value (**undefined** or **null**) is passed in, the text is processed as "undefined" or "null". |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: number | string, dy: number | string): void
```

Fills a new rectangular area with **ImageData** data.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | Yes | **ImageData** object that contains pixel values.<br> **undefined** and **null** are treated as invalid values and no drawing is performed. |
| dx | number &#124; string | Yes | Offset of the fill area on the x-axis.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dy | number &#124; string | Yes | Offset of the fill area on the y-axis.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |

<a id="putimagedata-1"></a>

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

Uses **ImageData** data to clip and fill a new rectangular area.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | [ImageData](arkts-arkui-canvas-comp-imagedata-c.md) | Yes | **ImageData** object that contains pixel values.<br> **undefined** and **null** are treated as invalid values and no drawing is performed. |
| dx | number &#124; string | Yes | Offset of the fill area on the x-axis.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dy | number &#124; string | Yes | Offset of the fill area on the y-axis.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dirtyX | number &#124; string | Yes | X-axis offset from the upper-left corner of the source image to the upper-left corner of the rectangular clipping region of the source image data.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| dirtyY | number &#124; string | Yes | Y-axis offset from the upper-left corner of the source image to the upper-left corner of the rectangular clipping region of the source image data.<br>Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br>Default unit: vp |
| dirtyWidth | number &#124; string | Yes | Width of the rectangular clipping region of the source image data.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |
| dirtyHeight | number &#124; string | Yes | Height of the rectangular clipping region of the source image data.<br> Invalid values **undefined**, **null**, **NaN**, and **Infinity** are treated as **0**.<br> Default unit: vp |

## reset

```TypeScript
reset(): void
```

Resets the **CanvasRenderingContext2D** to its default state, clearing the back buffer, drawing state stack, drawing path, and styles.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## resetTransform

```TypeScript
resetTransform(): void
```

Resets the current matrix to the identity matrix.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## restoreLayer

```TypeScript
restoreLayer(): void
```

Restores the image transform and clipping state to the state before **saveLayer**, and draws the layer on the canvas. The example for **restoreLayer** is the same as that for **saveLayer**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(angle: number): void
```

Rotates the current coordinate axes clockwise.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Clockwise rotation angle. You can convert degrees to radians using the following formula: degree * Math.PI/180.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br>Default unit: radian |

## save

```TypeScript
save(): void
```

Saves the current drawing context.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## saveLayer

```TypeScript
saveLayer(): void
```

Creates a layer.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: number, y: number): void
```

Sets the scaling transformation property of the canvas. Subsequent drawing operations are scaled according to the scaling ratio.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal scale factor.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |
| y | number | Yes | Vertical scaling factor. Negative numbers are not supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **0**, **null**, **undefined**, and negative numbers cause the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |

## setLineDash

```TypeScript
setLineDash(segments: number[]): void
```

Sets the dash line style of the canvas.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| segments | number[] | Yes | Array describing how line segments alternate and the length of the spacing between segments.<br>Anomalous values **undefined** or **null** are treated as invalid values.<br>Default unit: vp |

## setPixelMap

```TypeScript
setPixelMap(value?: PixelMap): void
```

Draws the currently passed-in **PixelMap** object on the canvas. For the **setPixelMap** example, see **getPixelMap**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | No | **PixelMap** object that contains pixel values.<br>Abnormal values **undefined** and **null** are treated as invalid values and will not be drawn.<br> Default value: **null** |

## setTransform

```TypeScript
setTransform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

The **setTransform** method uses the same parameters as the **transform()** method, but the **setTransform()** method resets the existing transformation matrix and creates a new one.

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | **scaleX**: horizontal scaling value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| b | number | Yes | **skewY**: vertical skewing value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| c | number | Yes | **skewX**: horizontal skewing value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| d | number | Yes | **scaleY**: vertical scaling value. A negative value is supported.<br> In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid arguments continue to render correctly. |
| e | number | Yes | **translateX**: horizontal translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br>Default unit: vp |
| f | number | Yes | **translateY**: vertical translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** values cause the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br>Default unit: vp |

<a id="settransform-1"></a>

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

Resets the existing transform matrix and creates a new one with the **Matrix2D** object as a template.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | Matrix2D | No | Transformation matrix.<br>Exception values **undefined** and **null** are treated as invalid values.<br>Default value: **null** |

## stroke

```TypeScript
stroke(): void
```

Performs a stroke operation based on the current path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="stroke-1"></a>

## stroke

```TypeScript
stroke(path: Path2D): void
```

Performs stroke drawing based on the specified path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | Path2D to draw.<br>If an invalid value (**undefined** or **null**) is passed, no drawing will be performed. |

## strokeRect

```TypeScript
strokeRect(x: number, y: number, w: number, h: number): void
```

Draws a rectangle with a border, without filling the interior.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| y | number | Yes | Y coordinate of the upper left corner of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br>Default unit: vp |

## strokeText

```TypeScript
strokeText(text: string, x: number, y: number, maxWidth?: number): void
```

Draws stroked text.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to draw.<br>**undefined** and **null** are treated as invalid values and no rendering will be performed. |
| x | number | Yes | X-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| y | number | Yes | Y-coordinate of the start point for text rendering.<br>**undefined**, **null**, **NaN**, and **Infinity** are treated as invalid values and no drawing is performed.<br> Default unit: vp |
| maxWidth | number | No | Maximum width of the text.<br>**null** is treated as an invalid value and no rendering will be performed. **undefined**, **NaN**, or **Infinity** is treated as the default value.<br>Default unit: vp<br>Default value: no width restriction |

## transferFromImageBitmap

```TypeScript
transferFromImageBitmap(bitmap: ImageBitmap): void
```

Displays the given **ImageBitmap** object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bitmap | [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) | Yes | **ImageBitmap** object to be displayed. |

## transform

```TypeScript
transform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

Corresponds to a transformation matrix. When you want to transform a shape, simply set the corresponding parameters of this transformation matrix, multiply the coordinates of each vertex of the shape by this matrix, and you can obtain the new vertex coordinates. Matrix transformation effects can be superimposed.

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | Cell at row 1, column 1 of the transformation matrix. **scaleX**: horizontal scaling value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |
| b | number | Yes | Cell at row 2, column 1 of the transformation matrix. **skewY**: vertical skewing value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |
| c | number | Yes | Cell at row 1, column 2 of the transformation matrix. **skewX**: horizontal skewing value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |
| d | number | Yes | Cell at row 2, column 2 of the transformation matrix. **scaleY**: vertical scaling value. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly. |
| e | number | Yes | Cell at row 1, column 3 of the transformation matrix. **translateX**: horizontal translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br> Default unit: vp |
| f | number | Yes | Cell at row 2, column 3 of the transformation matrix. **translateY**: vertical translation distance. A negative value is supported.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br> Default unit: vp |

## translate

```TypeScript
translate(x: number, y: number): void
```

Moves the origin of the current coordinate system.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Distance to translate on the x-axis.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Distance to translate on the y-axis.<br>In versions earlier than API version 18, values **NaN** and **Infinity** cause the failure to call the drawing APIs following this API for rendering. Values **null** and **undefined** cause the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other drawing APIs with valid parameters continue to render correctly.<br>Default unit: vp |

## antialias

```TypeScript
antialias: boolean | undefined
```

Sets whether to enable anti-aliasing when drawing graphics and text. Setting this API overrides the anti-aliasing effect in [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md). When not set through this API, the default value is **undefined**, and the anti-aliasing effect is consistent with that in [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md).

Whether to enable anti-aliasing when drawing graphics and text.

**true** indicates that anti-aliasing is enabled; **false** indicates that anti-aliasing is not enabled.

When the value is **undefined**, the anti-aliasing effect is consistent with that in [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md).

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

Sets the text direction used for text drawing. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

For details, see [CanvasDirection](arkts-arkui-canvas-comp-canvasdirection-t.md).

Default value: "inherit"

**Type:** [CanvasDirection](arkts-arkui-canvas-comp-canvasdirection-t.md)

**Default:** inherit

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillStyle

```TypeScript
fillStyle: string | number | CanvasGradient | CanvasPattern
```

Specifies the fill color for drawing. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

- When the type is string, this property sets the color of the fill area. For details about  
the color format, see the string type description in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is number, this property sets the color of the fill area. Fully transparent  
colors are not supported. For details about the color format, see the number type description in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is CanvasGradient, this property specifies a gradient object created using  
the [createLinearGradient](#createlineargradient) method.

- When the type is CanvasPattern, this property specifies a pattern object created using  
the [createPattern](#createpattern) method.

Default value: '#000000' (black)

Invalid values are ignored.

**Type:** string &#124; number &#124; [CanvasGradient](arkts-arkui-canvas-comp-canvasgradient-c.md) &#124; [CanvasPattern](arkts-arkui-canvas-comp-canvaspattern-i.md)

**Default:** #000000 (black)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## filter

```TypeScript
filter: string
```

Sets image filters. Any number of filters can be combined. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** will be returned.

Available values are as follows:

- **'none'**: No filter effect.  
- **'blur(`&lt;length&gt;`)'**: Applies Gaussian blur to the image. The value range is  
> = 0. Supported units: px, vp, rem. Default value: **blur(0px)**.
- **'brightness([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Applies a linear multiplier to the  
image, making it appear brighter or darker. Supports numeric and percentage parameters. The value range is &gt;= 0. Default value: **brightness(1)**.  
- **'contrast([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Adjusts the contrast of the image. Supports  
numeric and percentage parameters. The value range is &gt;= 0. Default value: **contrast(1)**.  
- **'grayscale([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Converts the image to grayscale. Supports  
numeric and percentage parameters. The value range is [0, 1]. Default value: **grayscale(0)**.  
- **'hue-rotate(`&lt;angle&gt;`)'**: Applies hue rotation to the image. The value range is  
0deg-360deg. Default value: **hue-rotate(0deg)**.  
- **'invert([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Inverts the input image. Supports numeric and  
percentage parameters. The value range is [0, 1]. Default value: **invert(0)**.  
- **'opacity([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Adjusts the transparency of the image. Supports  
numeric and percentage parameters. The value range is [0, 1]. Default value: **opacity(1)**.  
- **'saturate([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Adjusts the saturation of the image. Supports  
numeric and percentage parameters. The value range is &gt;= 0. Default value: **saturate(1)**.  
- **'sepia([`&lt;number&gt;`\|`&lt;percentage&gt;`])'**: Converts the image to sepia. Supports numeric and  
percentage parameters. The value range is [0, 1]. Default value: **sepia(0)**.

**Type:** string

**Default:** none

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font: string
```

Sets the font style for text drawing. This property is a write-only property. Its value can be set through an assignment statement, but its current value cannot be obtained through a read operation. Attempting to read it will return **undefined**.

Syntax: ctx.font = 'font-style font-weight font-size font-family'

- (Optional) **font-style**: specifies the font style. The following styles are  
supported: 'normal' and 'italic'.

- (Optional) **font-weight**: specifies the font weight. The following types are  
supported: 'normal', 'bold', 'bolder', 'lighter', 100, 200, 300, 400, 500, 600, 700, 800, 900.

- (Optional) **font-size**: specifies the font size and line height. The unit can be  
px or vp. A unit must be appended when used.

- (Optional) **font-family**: specifies the font family. The following types are  
supported: 'sans-serif', 'serif', 'monospace'.

Since API version 20, this API can be used to set a registered custom font (only available in the main thread, not supported in worker threads; the DevEco Studio previewer does not support displaying custom fonts). There are two ways to register a custom font. One is through the ArkUI asynchronous API

this.uiContext.getFont().[registerFont](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md#registerfont). Drawing immediately after calling this API may cause the custom font to not take effect.

The other is to directly call the font engine's fontCollection.[loadFontSync](../../../reference/apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync) API to register the custom font with the font engine. When directly calling the font engine API to register a custom font, the **fontCollection** instance must be **text.FontCollection.getGlobalInstance()**, because the component loads fonts from this instance by default. Using other instances may cause the custom font to not take effect.

**Type:** string

**Default:** normal normal 14px sans-serif

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalAlpha

```TypeScript
globalAlpha: number
```

Sets the transparency. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

The value range is [0.0, 1.0], where 0.0 means fully transparent and 1.0 means fully opaque. If the given value is less than 0.0, the value 0.0 is used; if the given value is greater than 1.0, the value 1.0 is used.

Before API version 18, when **NaN** or **Infinity** is set, drawing methods executed after this method cannot draw. Since API version 18, when **NaN** or **Infinity** is set, the current API does not take effect, and other drawing methods with valid parameters draw normally.

Default value: 1.0

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalCompositeOperation

```TypeScript
globalCompositeOperation: string
```

Sets the composite operation mode. This is a write-only property, which can be set through an assignment statement but cannot be read; attempting to read it returns **undefined**.

Available values are as follows:

| Name | Description |  
| ------ | ------ |  
| source-over | Displays the new drawing content over the existing drawing content. This is the default value. |
| source-atop | Displays the new drawing content on top of the existing drawing content. |
| source-in | Displays the new drawing content inside the existing drawing content. |
| source-out | Displays the new drawing content outside the existing drawing content. |
| destination-over | Displays the existing drawing content over the new drawing content. |
| destination-atop | Displays the existing drawing content on top of the new drawing content. |
| destination-in | Displays the existing drawing content inside the new drawing content. |
| destination-out | Displays the existing drawing content outside the new drawing content. |
| lighter | Displays both the new and existing drawing content. |
| copy | Displays the new drawing content and ignores the existing drawing content. |
| xor | Blends the new drawing content with the existing drawing content using an XOR operation. |

Default value: 'source-over'

**Type:** string

**Default:** source-over

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingEnabled

```TypeScript
imageSmoothingEnabled: boolean
```

Sets whether to perform image smoothing adjustment when drawing images. The value **true** enables it, and **false** disables it. This is a write-only property. Its value can be set through an assignment statement, but cannot be obtained through a read operation. If a read is attempted, **undefined** is returned.

Whether to perform image smoothing adjustment when drawing images.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingQuality

```TypeScript
imageSmoothingQuality: ImageSmoothingQuality
```

When **imageSmoothingEnabled** is set to true, this property is used to set the image smoothness. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** will be returned.

Image smoothness.

Default value: "low"

**Type:** [ImageSmoothingQuality](arkts-arkui-canvas-comp-imagesmoothingquality-t.md)

**Default:** low

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing: LengthMetrics | string
```

Specifies the spacing between letters when drawing text. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

Spacing between letters when drawing text.

When **LengthMetrics** is used:

The letter spacing is set in the specified unit.

**FP**, **PERCENT**, and **LPX** are not supported (treated as invalid values).

Negative numbers and decimals are supported. When set to a decimal, the letter spacing is not rounded.

When string is used:

Percentage values are not supported (treated as invalid values).

Negative numbers and decimals are supported. When set to a decimal, the letter spacing is not rounded.

If the value assigned to **letterSpacing** does not specify a unit (for example, letterSpacing='10') and **LengthMetricsUnit** is not specified, the default unit is vp.

If **LengthMetricsUnit** is specified as px, the default unit is px.

When the value assigned to **letterSpacing** specifies a unit (for example, letterSpacing='10vp'), the letter spacing is set in the specified unit.

Default value: **0** (when an invalid value is input, the letter spacing is set to the default value)

> **NOTE:** 
> 
> **LengthMetrics** is recommended for better performance.

**Type:** LengthMetrics &#124; string

**Default:** 0vp

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineCap

```TypeScript
lineCap: CanvasLineCap
```

Specifies the style of the line endpoint. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

Style of the line endpoint.

Default value: 'butt'

**Type:** [CanvasLineCap](arkts-arkui-canvas-comp-canvaslinecap-t.md)

**Default:** butt

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineDashOffset

```TypeScript
lineDashOffset: number
```

Sets the dash offset of the canvas, with float precision. This property takes effect only when **setLineDash** is set. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

Default value: 0.0

Unit: vp

Abnormal values **NaN** and **Infinity** are handled as the default value.

**Type:** number

**Default:** 0.0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineJoin

```TypeScript
lineJoin: CanvasLineJoin
```

Specifies the style of the intersection point where line segments meet. This attribute is a write-only property, which can be set through an assignment statement but cannot be read. Attempting to read it returns **undefined**. For details, see [CanvasLineJoin](arkts-arkui-canvas-comp-canvaslinejoin-t.md). <br>Available values are as follows: <br>- **'round'**: The shape used to join line segments is a sector, whose radius at the rounded corner is equal to the line width. <br>- **'bevel'**: The shape used to join line segments is a triangle. The rectangular corner of each line is independent. <br>- **'miter'**: The shape used to join line segments has a mitered corner by extending the outside edges of the lines until they meet. You can view the effect of this attribute in **miterLimit**. <br>Default value: 'miter'

**Type:** [CanvasLineJoin](arkts-arkui-canvas-comp-canvaslinejoin-t.md)

**Default:** miter

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineWidth

```TypeScript
lineWidth: number
```

Sets the width of drawn lines. This is a write-only property. You can set its value through an assignment statement, but cannot obtain its current value through a read operation. Attempting to read it will return **undefined**.

Default value: 1 (px)

Default unit: vp

The value of **lineWidth** does not support 0 or negative numbers. **0**, negative numbers, and **NaN** are processed as the default value. Infinity causes APIs related to the **lineWidth** property to be unable to draw.

**Type:** number

**Default:** 1(px)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## miterLimit

```TypeScript
miterLimit: number
```

Sets the miter limit, which specifies the distance between the inner corner and outer corner at the intersection of lines. This property takes effect only when **lineJoin** is set to **miter**. It is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

Default value: 10px

Unit: px

The value of **miterLimit** does not support 0 or negative numbers. **0**, negative numbers, and **NaN** are processed as the default value. **Infinity** causes APIs related to the **miterLimit** property to fail to draw.

**Type:** number

**Default:** 10(px)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowBlur

```TypeScript
shadowBlur: number
```

Sets the blur level for drawing shadows. This property is a write-only property. Its value can be set through an assignment statement, but its current value cannot be obtained through a read operation. If a read is attempted, **undefined** is returned.

Blur level for drawing shadows. A larger value indicates a higher blur level. The precision is float, and the value range is &gt;= 0.

Default value: 0.0

Unit: px

Negative values are not supported for **shadowBlur**. Negative values, **NaN**, and **Infinity** are treated as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowColor

```TypeScript
shadowColor: string
```

Sets the shadow color for drawing shadows. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

For details about the color format, see the description of the string type in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

Default value: transparent black

**Type:** string

**Default:** transparent black

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetX

```TypeScript
shadowOffsetX: number
```

Sets the horizontal offset between the shadow and the original object when drawing a shadow. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** is returned.

Default value: 0.0

Default unit: vp

Abnormal values **NaN** and **Infinity** are processed as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetY

```TypeScript
shadowOffsetY: number
```

Sets the vertical offset of the shadow from the original object during shadow drawing. This is a write-only property. Its value can be set through an assignment statement, but cannot be obtained through a read operation. If a read is attempted, **undefined** is returned.

Default value: 0.0

Default unit: vp

The abnormal values **NaN** and **Infinity** are handled as the default value.

**Type:** number

**Default:** 0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeStyle

```TypeScript
strokeStyle: string | number | CanvasGradient | CanvasPattern
```

Sets the color of the stroke. This is a write-only property. Its value can be set through an assignment statement, but the current value cannot be obtained through a read operation. If a read is attempted, **undefined** is returned.

- When the type is string, it indicates the color used for the stroke. For details about  
the color format, see the string type description in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is number, it indicates the color used for the stroke. Fully transparent  
colors are not supported. For details about the color format, see the number type description in [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md).

- When the type is CanvasGradient, it indicates a gradient object created using the [createLinearGradient](#createlineargradient) method.

- When the type is CanvasPattern, it indicates a pattern object created using the [createPattern](#createpattern) method.

Default value: '#000000' (black)

Invalid values are ignored.

**Type:** string &#124; number &#124; [CanvasGradient](arkts-arkui-canvas-comp-canvasgradient-c.md) &#124; [CanvasPattern](arkts-arkui-canvas-comp-canvaspattern-i.md)

**Default:** #000000 (black)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign: CanvasTextAlign
```

Sets the text alignment mode in text drawing. This is a write-only property. Its value can be set through an assignment statement, but cannot be obtained through a read operation. If a read is attempted, **undefined** is returned.

In LTR layout mode, 'start' is the same as 'left'; in RTL layout mode, 'start' is the same as 'right'.

Default value: 'left'

**Type:** [CanvasTextAlign](arkts-arkui-canvas-comp-canvastextalign-t.md)

**Default:** left

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textBaseline

```TypeScript
textBaseline: CanvasTextBaseline
```

Sets the baseline alignment mode in text drawing. This is a write-only property. You can set its value through an assignment statement, but you cannot obtain its current value through a read operation. If you attempt to read it, **undefined** will be returned.

Default value: 'alphabetic'

**Type:** [CanvasTextBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md)

**Default:** alphabetic

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
