# OffscreenCanvasRenderingContext2D

Provides a 2D rendering context for the drawing surface of the &lt; Canvas &gt; element. It is used to draw shapes, text, images and other objects.

@interface OffscreenCanvasRenderingContext2D

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arc

```TypeScript
arc(radius: number, x: number, y: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void
```

Draw an arc.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of an arc. |
| x | number | Yes | The X-axis coordinates of the center of the circle. |
| y | number | Yes | The Y-axis coordinates of the center of an arc (center of a circle). |
| startAngle | number | Yes | The starting point of the arc, in the X-axis direction, is calculated in radians. |
| endAngle | number | Yes | The end point of an arc, expressed in radians. |
| counterclockwise | boolean | No | An optional Boolean value. If true, the arc is drawn counterclockwise, and otherwise clockwise. |

## arcTo

```TypeScript
arcTo(x1: number, x2: number, y1: number, y2: number, radius: number): void
```

Draws an arc from the beginning to the end.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | The X-axis coordinates of the first control point. |
| x2 | number | Yes | The X-axis coordinates of the second control point. |
| y1 | number | Yes | The y-coordinate of the first control point. |
| y2 | number | Yes | The Y-axis coordinates of the second control point. |
| radius | number | Yes | Radius of an arc. |

## beginPath

```TypeScript
beginPath(): void
```

Creates a drawing path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void
```

Draw a third order Bezier curve.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cp1x | number | Yes | The X-axis coordinates of the first control point. |
| cp1y | number | Yes | The y-coordinate of the first control point. |
| cp2x | number | Yes | The X-axis coordinates of the second control point. |
| cp2y | number | Yes | The Y-axis coordinates of the second control point. |
| x | number | Yes | The x-coordinate of the end point. |
| y | number | Yes | The y-coordinate of the end point |

## clearRect

```TypeScript
clearRect(x: number, y: number, w: number, h: number): void
```

Clears the contents of the specified rectangular area.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates at the beginning of the rectangle. |
| y | number | Yes | The Y-axis coordinates at the beginning of the rectangle. |
| w | number | Yes | The width of a rectangle. |
| h | number | Yes | The height of a rectangle. |

## clip

```TypeScript
clip(): void
```

Crop the current canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closePath

```TypeScript
closePath(): void
```

Closing the current path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## createImageData

```TypeScript
createImageData(sw: number, sh: number): ImageData
```

Create an ImageData object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sw | number | Yes | The width of the new object. |
| sh | number | Yes | The height of the new object. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | ImageData New ImageData object with width and height specified. |

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

Create an ImageData object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | Copy an object of the same width and height from an existing ImageData object The image itself is not allowed to be copied. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | ImageData New ImageData object with width and height specified. |

## createLinearGradient

```TypeScript
createLinearGradient(x0: number, y0: number, x1: number, y1: number): CanvasGradient
```

Creates a linear gradient color.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x0 | number | Yes | X-coordinate of the start point. |
| y0 | number | Yes | Y-coordinate of the start point. |
| x1 | number | Yes | X-coordinate of the end point. |
| y1 | number | Yes | Y-coordinate of the end point. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) | LinearGradient object. |

## createPath2D

```TypeScript
createPath2D(path?: Path2D): Path2D
```

Creates a path that is later used by the CanvasRenderingContext2D object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | No | another created Path2D object. |

**Return value:**

| Type | Description |
| --- | --- |
| [Path2D](arkts-arkui-viewmodel-path2d-i.md) | the object of Path2D. |

## createPath2D

```TypeScript
createPath2D(cmds?: string): Path2D
```

Creates a path that is later used by the CanvasRenderingContext2D object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cmds | string | No | a string defined using the SVG path command. |

**Return value:**

| Type | Description |
| --- | --- |
| [Path2D](arkts-arkui-viewmodel-path2d-i.md) | the object of Path2D. |

## createPattern

```TypeScript
createPattern(image: Image, repetition: string): CanvasPattern
```

Create a drawing style template.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | The CanvasImageSource object that is the source of the duplicate image. |
| repetition | string | Yes | Specify how to repeat images. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasPattern](arkts-arkui-canvaspattern-canvaspattern-i.md) | CanvasPattern An opaque object that describes a schema. |

## createRadialGradient

```TypeScript
createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number): CanvasGradient
```

Create a radial tween object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x0 | number | Yes | The x coordinate of the circle at the beginning. |
| y0 | number | Yes | The y coordinate of the circle at the beginning. |
| r0 | number | Yes | The radius of the starting circle. |
| x1 | number | Yes | X-coordinate of the end point. |
| y1 | number | Yes | Y-coordinate of the end point. |
| r1 | number | Yes | The radius of End Circle. |

**Return value:**

| Type | Description |
| --- | --- |
| [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) | RadialGradient object. |

## drawImage

```TypeScript
drawImage(image: Image, dx: number, dy: number, dw: number, dh: number): void
```

Draw an Image object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | An element drawn to the context. |
| dx | number | Yes | The top left corner of the image is the X-axis coordinates on the target canvas. |
| dy | number | Yes | The top left corner of the image is the Y-axis coordinates on the target canvas. |
| dw | number | Yes | Image The width drawn on the target canvas. |
| dh | number | Yes | Image The height drawn on the target canvas. |

## drawImage

```TypeScript
drawImage(
    image: Image,
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

Draw an Image object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | An element drawn to the context. |
| sx | number | Yes | The upper-left X-axis coordinates of the image's rectangular (clipped) selection box that need to be drawn into the target context. |
| sy | number | Yes | The upper-left Y-axis coordinates of the image's rectangular (clipped) selection box that need to be drawn into the target context. |
| sw | number | Yes | The width of the image's rectangular (clipped) selection box that needs to be drawn into the target context. |
| sh | number | Yes | The height of the image's rectangular (clipped) selection box that needs to be drawn into the target context. |
| dx | number | Yes | The top left corner of the image is the X-axis coordinates on the target canvas. |
| dy | number | Yes | The top left corner of the image is the Y-axis coordinates on the target canvas. |
| dw | number | Yes | Image The width drawn on the target canvas. |
| dh | number | Yes | Image The height drawn on the target canvas. |

## drawImage

```TypeScript
drawImage(image: image.PixelMap, dx: number, dy: number, dw: number, dh: number): void
```

Draw an Image object.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | An element drawn to the context. |
| dx | number | Yes | The top left corner of the image is the X-axis coordinates on the target canvas. |
| dy | number | Yes | The top left corner of the image is the Y-axis coordinates on the target canvas. |
| dw | number | Yes | Image The width drawn on the target canvas. |
| dh | number | Yes | Image The height drawn on the target canvas. |

## drawImage

```TypeScript
drawImage(
    image: image.PixelMap,
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

Draw an Image object.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | An element drawn to the context. |
| sx | number | Yes | The upper-left X-axis coordinates of the image's rectangular (clipped) selection box that need to be drawn into the target context. |
| sy | number | Yes | The upper-left Y-axis coordinates of the image's rectangular (clipped) selection box that need to be drawn into the target context. |
| sw | number | Yes | The width of the image's rectangular (clipped) selection box that needs to be drawn into the target context. |
| sh | number | Yes | The height of the image's rectangular (clipped) selection box that needs to be drawn into the target context. |
| dx | number | Yes | The top left corner of the image is the X-axis coordinates on the target canvas. |
| dy | number | Yes | The top left corner of the image is the Y-axis coordinates on the target canvas. |
| dw | number | Yes | Image The width drawn on the target canvas. |
| dh | number | Yes | Image The height drawn on the target canvas. |

## ellipse

```TypeScript
ellipse(
    x: number,
    y: number,
    radiusX: number,
    radiusY: number,
    rotation: number,
    startAngle: number,
    endAngle: number,
    counterclockwise?: boolean,
  ): void
```

Draw an ellipse.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates of the center of the ellipse. |
| y | number | Yes | The Y-axis coordinates of the center of the ellipse. |
| radiusX | number | Yes | The radius of the major axis of an ellipse. |
| radiusY | number | Yes | The radius of the short axis of an ellipse. |
| rotation | number | Yes | The Angle of rotation of an ellipse, expressed in radians. |
| startAngle | number | Yes | The starting point Angle to be plotted, measured from the X-axis, is expressed in radians. |
| endAngle | number | Yes | The Angle, expressed in radians, at which the ellipse will be drawn. |
| counterclockwise | boolean | No | If true, the ellipse is drawn counterclockwise (counterclockwise) and clockwise otherwise. |

## fill

```TypeScript
fill(): void
```

Fills the current canvas with color.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillRect

```TypeScript
fillRect(x: number, y: number, w: number, h: number): void
```

Fills a rectangular area.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates at the beginning of the rectangle. |
| y | number | Yes | The Y-axis coordinates at the beginning of the rectangle. |
| w | number | Yes | The width of a rectangle. |
| h | number | Yes | The height of a rectangle. |

## fillText

```TypeScript
fillText(text: string, y: number, x: number /*, maxWidth?: number*/): void
```

Stroke a rectangular area.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Render text using the current values of font, textAlign, textBaseline, and direction. |
| y | number | Yes | The Y-axis coordinates of the starting point of the text. |
| x | number | Yes | The X-axis coordinates of the starting point of the text. |

## getImageData

```TypeScript
getImageData(sx: number, sy: number, sw: number, sh: number): ImageData
```

Get an ImageData object.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | The upper-left x-coordinate of the rectangular area of the image data to be extracted. |
| sy | number | Yes | The upper-left y coordinate of the rectangular region of the image data to be extracted. |
| sw | number | Yes | The width of the rectangular area of the image data to be extracted. |
| sh | number | Yes | The height of the rectangular area of the image data to be extracted. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | ImageData An ImageData object that contains the rectangular ImageData given by the canvas. |

## getPixelMap

```TypeScript
getPixelMap(sx: number, sy: number, sw: number, sh: number): image.PixelMap
```

Get an PixelMap object.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | The upper-left x-coordinate of the rectangular area of the image data to be extracted. |
| sy | number | Yes | The upper-left y coordinate of the rectangular region of the image data to be extracted. |
| sw | number | Yes | The width of the rectangular area of the image data to be extracted. |
| sh | number | Yes | The height of the rectangular area of the image data to be extracted. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | PixelMap A PixelMap object that contains the rectangular ImageData given by the canvas. |

## isPointInPath

```TypeScript
isPointInPath(x: number, y: number): boolean
```

Check whether the specified coordinate point is on the Path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X coordinate of the detection point. |
| y | number | Yes | The Y coordinate of the detection point. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean Return true if the detection point is contained within the current or specified path Otherwise return false. |

## isPointInPath

```TypeScript
isPointInPath(path: Path2D, x: number, y: number): boolean
```

Check whether the specified coordinate point is on the Path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | Yes | The Path2D path that needs to be populated. |
| x | number | Yes | The X coordinate of the detection point. |
| y | number | Yes | The Y coordinate of the detection point. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean Return true if the detection point is contained within the current or specified path Otherwise return false. |

## isPointInStroke

```TypeScript
isPointInStroke(x: number, y: number): boolean
```

Checks whether the specified coordinate point is on the stroke edge.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X coordinate of the detection point. |
| y | number | Yes | The Y coordinate of the detection point. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean A Boolean value that returns true when the point is on the line of the path, false otherwise. |

## isPointInStroke

```TypeScript
isPointInStroke(path: Path2D, x: number, y: number): boolean
```

Checks whether the specified coordinate point is on the stroke edge.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | Yes | Path2D path. |
| x | number | Yes | The X coordinate of the detection point. |
| y | number | Yes | The Y coordinate of the detection point. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean A Boolean value that returns true when the point is on the line of the path, false otherwise. |

## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

Draw a straight line.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates at the end of the line. |
| y | number | Yes | The Y-axis coordinates at the end of the line. |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

Returns a TextMetrics object used to obtain the width of specified text.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to be measured. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextMetrics](arkts-arkui-viewmodel-textmetrics-i.md) | Object that contains the text width. You can obtain the width by TextMetrics.width. |

## moveTo

```TypeScript
moveTo(x: number, y: number): void
```

Moves the current canvas to the specified coordinate point.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The x axis. |
| y | number | Yes | The y axis. |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: number, dy: number): void
```

Draws the specified ImageData object to the canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | An array object containing pixel values. |
| dx | number | Yes | The offset of the position of the source image data in the target canvas (the offset in the X-axis direction). |
| dy | number | Yes | The offset of the position of the source image data in the target canvas (the Y-axis offset). |

## putImageData

```TypeScript
putImageData(
    imageData: ImageData,
    dx: number,
    dy: number,
    dirtyX: number,
    dirtyY: number,
    dirtyWidth: number,
    dirtyHeight: number,
  ): void
```

Draws the specified ImageData object to the canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | An array object containing pixel values. |
| dx | number | Yes | The offset of the position of the source image data in the target canvas (the offset in the X-axis direction). |
| dy | number | Yes | he offset of the position of the source image data in the target canvas (the Y-axis offset). |
| dirtyX | number | Yes | In the source image data, the position of the upper left corner of the rectangular region Default is the upper left corner of the entire image data (x coordinate). |
| dirtyY | number | Yes | In the source image data, the position of the upper left corner of the rectangular region Default is the top left corner (y coordinate) of the entire image data. |
| dirtyWidth | number | Yes | In the source image data, the width of a rectangular region. Default is the width of the image data. |
| dirtyHeight | number | Yes | In the source image data, the height of a rectangular region. Default is the height of the image data. |

## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void
```

Draw a second order Bezier curve.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cpx | number | Yes | The X-axis coordinates of the control points. |
| cpy | number | Yes | The y-coordinate of the control point. |
| x | number | Yes | The X-axis of the end point. |
| y | number | Yes | The Y-axis of the end point. |

## rect

```TypeScript
rect(x: number, y: number, w: number, h: number): void
```

Draw a rectangle.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates at the beginning of the rectangle. |
| y | number | Yes | The Y-axis coordinates at the beginning of the rectangle. |
| w | number | Yes | The width of a rectangle. |
| h | number | Yes | The height of a rectangle. |

## resetTransform

```TypeScript
resetTransform(): void
```

Resets the current matrix transformation effect.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## restore

```TypeScript
restore(): void
```

Restores the configuration information of the last saved canvas context.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(angle: number): void
```

Adds a rotation effect to the current canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | The radian of clockwise rotation. |

## save

```TypeScript
save(): void
```

Saves configuration information for the current canvas context.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: number, y: number): void
```

Adds a zoom effect to the current canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The horizontal scaling factor. |
| y | number | Yes | The scaling factor in the vertical direction. |

## setLineDash

```TypeScript
setLineDash(segments: Array<number>): void
```

Sets the dotted spacing of a line.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| segments | Array&lt;number&gt; | Yes | A set of numbers describing the length of alternating drawn line segments and spacing (coordinate space units). |

## setTransform

```TypeScript
setTransform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

Set the rotation, pan, and zoom effects.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | The level of zoom. |
| b | number | Yes | Vertical tilt. |
| c | number | Yes | Horizontal tilt. |
| d | number | Yes | Vertical scaling. |
| e | number | Yes | The level of mobile. |
| f | number | Yes | Vertical movement. |

## stroke

```TypeScript
stroke(): void
```

Stroke draws the current path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stroke

```TypeScript
stroke(path: Path2D): void
```

Stroke draws the current path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | Yes | The object of Path2D. |

## strokeRect

```TypeScript
strokeRect(x: number, y: number, w: number, h: number): void
```

Stroke a rectangular area.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The X-axis coordinates at the beginning of the rectangle. |
| y | number | Yes | The Y-axis coordinates at the beginning of the rectangle. |
| w | number | Yes | The width of the rectangle. Positive values on the right, negative values on the left. |
| h | number | Yes | The height of the rectangle. Positive values are down, negative values are up. |

## strokeText

```TypeScript
strokeText(text: string, x: number, y: number /*, maxWidth?: number*/): void
```

Draws the stroke of a text string.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text stroke to draw. |
| x | number | Yes | X-coordinate of the lower left corner of the text stroke. |
| y | number | Yes | Y-coordinate of the lower left corner of the text stroke. |

## transform

```TypeScript
transform(a: number, b: number, c: number, d: number, e: number, f: number): void
```

Set the rotation, pan, and zoom effects.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| a | number | Yes | The level of zoom. |
| b | number | Yes | Vertical tilt. |
| c | number | Yes | Horizontal tilt. |
| d | number | Yes | Vertical scaling. |
| e | number | Yes | The level of mobile. |
| f | number | Yes | Vertical movement. |

## translate

```TypeScript
translate(x: number, y: number): void
```

Adds a pan effect to the current canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal movement distance. |
| y | number | Yes | Vertical movement. |

## fillStyle

```TypeScript
fillStyle?: string | CanvasGradient | CanvasPattern
```

Fill style attribute. Paint color used to fill the area. Canvas gradient object used by the paint. You can call createLinearGradient() to create a CanvasGradient object. Canvas pattern. You can call createPattern() to create a CanvasPattern object.

**Type:** string &#124; [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-canvaspattern-i.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLineDash

```TypeScript
getLineDash: Array<number>
```

Gets the dotted spacing of a line. Returns the current line segment style array containing an even number of non-negative numbers.

**Type:** Array&lt;number&gt;

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeStyle

```TypeScript
strokeStyle?: string | CanvasGradient | CanvasPattern
```

Sets the stroke paint style. Color of the stroke paint. Canvas gradient object used by the paint. You can call createLinearGradient() to create a CanvasGradient object. Canvas pattern. You can call createPattern() to create a CanvasPattern object.

**Type:** string &#124; [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-canvaspattern-i.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
