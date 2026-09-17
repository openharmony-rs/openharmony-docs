# CanvasRenderingContext2D

CanvasRenderingContext2D allows you to draw rectangles, text, images, and other objects on a canvas. You can call getContext('2d') on canvas to obtain a CanvasRenderingContext2D object.

@interface CanvasRenderingContext2D

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arc

```TypeScript
arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void
```

Draws an arc on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the center point of the arc. |
| y | number | Yes | Y-coordinate of the center point of the arc. |
| radius | number | Yes | Radius of the arc. |
| startAngle | number | Yes | Start radian of the arc. |
| endAngle | number | Yes | End radian of the arc. |
| counterclockwise | boolean | No | Whether to draw the arc counterclockwise. |

## arcTo

```TypeScript
arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void
```

Draws an arc based on the radius and points on the arc.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | X-coordinate of the first point on the arc. |
| y1 | number | Yes | Y-coordinate of the first point on the arc. |
| x2 | number | Yes | X-coordinate of the second point on the arc. |
| y2 | number | Yes | Y-coordinate of the second point on the arc. |
| radius | number | Yes | Radius of the arc. |

## beginPath

```TypeScript
beginPath(): void
```

Creates a drawing path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void
```

Draws a cubic bezier curve on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cp1x | number | Yes | X-coordinate of the first parameter of the bezier curve. |
| cp1y | number | Yes | Y-coordinate of the first parameter of the bezier curve. |
| cp2x | number | Yes | X-coordinate of the second parameter of the bezier curve. |
| cp2y | number | Yes | Y-coordinate of the second parameter of the bezier curve. |
| x | number | Yes | End point x-coordinate of the bezier curve. |
| y | number | Yes | End point y-coordinate of the bezier curve. |

## clearRect

```TypeScript
clearRect(x: number, y: number, width: number, height: number): void
```

Clears the content in a rectangle on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the upper left corner of the rectangle. |
| y | number | Yes | Y-coordinate of the upper left corner of the rectangle. |
| width | number | Yes | Width of the rectangle. |
| height | number | Yes | Height of the rectangle. |

## clip

```TypeScript
clip(): void
```

Sets a path as the clipping path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closePath

```TypeScript
closePath(): void
```

Draws a closed path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## createImageData

```TypeScript
createImageData(width: number, height: number): ImageData
```

Creates an ImageData object.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the ImageData object. |
| height | number | Yes | Height of the ImageData object. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | Returns the newly created FunctionCallable object. |

## createImageData

```TypeScript
createImageData(imageData: ImageData): ImageData
```

Creates an ImageData object.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | ImageData object with the same width and height copied from the original ImageData object. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | Returns the newly created FunctionCallable object. |

## createLinearGradient

```TypeScript
createLinearGradient(x0: number, y0: number, x1: number, y1: number): CanvasGradient
```

Creates a linear gradient color.

**Since:** 6

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

**Since:** 4

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

**Since:** 4

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
createPattern(image: Image, repetition: string): object
```

Creates a pattern for image filling based on a specified source image and repetition mode.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | Source image. |
| repetition | string | Yes | Repetition mode. The value can be "repeat", "repeat-x", "repeat-y", or "no-repeat". |

**Return value:**

| Type | Description |
| --- | --- |
| object | Pattern of image filling. |

## createRadialGradient

```TypeScript
createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number): CanvasGradient
```

Creates a radial gradient color.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x0 | number | Yes | X-coordinate of the start point. |
| y0 | number | Yes | Y-coordinate of the start point. |
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
drawImage(image: Image, dx: number, dy: number, dWidth: number, dHeight: number): void
```

Draws an image.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | Image resource. |
| dx | number | Yes | X-coordinate of the upper left corner of the drawing area on the canvas. |
| dy | number | Yes | Y-coordinate of the upper left corner of the drawing area on the canvas. |
| dWidth | number | Yes | Width of the drawing area. |
| dHeight | number | Yes | Height of the drawing area. |

## drawImage

```TypeScript
drawImage(
    image: Image,
    sx: number,
    sy: number,
    sWidth: number,
    sHeight: number,
    dx: number,
    dy: number,
    dWidth: number,
    dHeight: number,
  ): void
```

Draws an image.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | Image | Yes | Image resource. |
| sx | number | Yes | X-coordinate of the upper left corner of the rectangle used to crop the source image. |
| sy | number | Yes | Y-coordinate of the upper left corner of the rectangle used to crop the source image. |
| sWidth | number | Yes | Target width of the image to crop. |
| sHeight | number | Yes | Target height of the image to crop. |
| dx | number | Yes | X-coordinate of the upper left corner of the drawing area on the canvas. |
| dy | number | Yes | Y-coordinate of the upper left corner of the drawing area on the canvas. |
| dWidth | number | Yes | Width of the drawing area. |
| dHeight | number | Yes | Height of the drawing area. |

## drawImage

```TypeScript
drawImage(image: image.PixelMap, dx: number, dy: number, dWidth: number, dHeight: number): void
```

Draws an image.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image resource. |
| dx | number | Yes | X-coordinate of the upper left corner of the drawing area on the canvas. |
| dy | number | Yes | Y-coordinate of the upper left corner of the drawing area on the canvas. |
| dWidth | number | Yes | Width of the drawing area. |
| dHeight | number | Yes | Height of the drawing area. |

## drawImage

```TypeScript
drawImage(
    image: image.PixelMap,
    sx: number,
    sy: number,
    sWidth: number,
    sHeight: number,
    dx: number,
    dy: number,
    dWidth: number,
    dHeight: number,
  ): void
```

Draws an image.

**Since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image resource. |
| sx | number | Yes | X-coordinate of the upper left corner of the rectangle used to crop the source image. |
| sy | number | Yes | Y-coordinate of the upper left corner of the rectangle used to crop the source image. |
| sWidth | number | Yes | Target width of the image to crop. |
| sHeight | number | Yes | Target height of the image to crop. |
| dx | number | Yes | X-coordinate of the upper left corner of the drawing area on the canvas. |
| dy | number | Yes | Y-coordinate of the upper left corner of the drawing area on the canvas. |
| dWidth | number | Yes | Width of the drawing area. |
| dHeight | number | Yes | Height of the drawing area. |

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
    counterclockwise?: number,
  ): void
```

Draws an ellipse based on the coordinate and radius.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the center point on the ellipse. |
| y | number | Yes | Y-coordinate of the center point on the ellipse. |
| radiusX | number | Yes | X-coordinate of the radius Length on the ellipse. |
| radiusY | number | Yes | Y-coordinate of the radius Length on the ellipse. |
| rotation | number | Yes | The rotation angle of the ellipse, in radians. |
| startAngle | number | Yes | Angle of the start point for ellipse drawing. |
| endAngle | number | Yes | End Point Angle for Ellipse Drawing. |
| counterclockwise | number | No | Indicates whether to draw an ellipse counterclockwise. 0: clockwise; 1: counterclockwise. The default value is 0. |

## fill

```TypeScript
fill(): void
```

Fills the area inside a closed path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillRect

```TypeScript
fillRect(x: number, y: number, width: number, height: number): void
```

Fills a rectangle on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the upper left corner of the rectangle. |
| y | number | Yes | Y-coordinate of the upper left corner of the rectangle. |
| width | number | Yes | Width of the rectangle. |
| height | number | Yes | Height of the rectangle. |

## fillText

```TypeScript
fillText(text: string, x: number, y: number): void
```

Draws filled text on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to draw. |
| x | number | Yes | X-coordinate of the lower left corner of the text. |
| y | number | Yes | Y-coordinate of the lower left corner of the text. |

## getImageData

```TypeScript
getImageData(sx: number, sy: number, sw: number, sh: number): ImageData
```

ImageData object created with pixels in the specified area on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | X-coordinate of the upper left corner of the output area. |
| sy | number | Yes | Y-coordinate of the upper left corner of the output area. |
| sw | number | Yes | Width of the output area. |
| sh | number | Yes | Height of the output area. |

**Return value:**

| Type | Description |
| --- | --- |
| ImageData | ImageData object that contains pixels in the specified area on the canvas. |

## getLineDash

```TypeScript
getLineDash(): Array<number>
```

Obtains the dash line style.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Interval of alternate line segments and the length of spacing. |

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

## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

Connects the current point to a target position using a straight line.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position. |
| y | number | Yes | Y-coordinate of the target position. |

## measureText

```TypeScript
measureText(text: string): TextMetrics
```

Returns a TextMetrics object used to obtain the width of specified text.

**Since:** 4

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

Moves a drawing path to a target position on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position. |
| y | number | Yes | Y-coordinate of the target position. |

## putImageData

```TypeScript
putImageData(imageData: ImageData, dx: number, dy: number): void
```

Puts the ImageData onto a rectangular area on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | ImageData object with pixels to put onto the canvas. |
| dx | number | Yes | X-axis offset of the rectangle area on the canvas. |
| dy | number | Yes | Y-axis offset of the rectangle area on the canvas. |

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

Puts the ImageData onto a rectangular area on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| imageData | ImageData | Yes | ImageData object with pixels to put onto the canvas. |
| dx | number | Yes | X-axis offset of the rectangle area on the canvas. |
| dy | number | Yes | Y-axis offset of the rectangle area on the canvas. |
| dirtyX | number | Yes | X-axis offset of the upper left corner of the rectangle area relative to that of the source image. |
| dirtyY | number | Yes | Y-axis offset of the upper left corner of the rectangle area relative to that of the source image. |
| dirtyWidth | number | Yes | Width of the rectangle area to cop the source image. |
| dirtyHeight | number | Yes | Height of the rectangle area to cop the source image. |

## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void
```

Draws a quadratic curve on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cpx | number | Yes | X-coordinate of the bezier curve parameter. |
| cpy | number | Yes | Y-coordinate of the bezier curve parameter. |
| x | number | Yes | End point x-coordinate of the bezier curve. |
| y | number | Yes | End point y-coordinate of the bezier curve. |

## rect

```TypeScript
rect(x: number, y: number, width: number, height: number): void
```

Creates a rectangular.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the upper left corner of the rectangle. |
| y | number | Yes | Y-coordinate of the upper left corner of the rectangle. |
| width | number | Yes | Width of the rectangle. |
| height | number | Yes | Height of the rectangle. |

## restore

```TypeScript
restore: () => void
```

Restores the saved drawing context.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate(rotate: number): void
```

Rotates a canvas clockwise around its coordinate axes.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotate | number | Yes | Clockwise rotation angle. You can use Math.PI / 180 to convert the angle to radian. |

## save

```TypeScript
save: () => void
```

Saves the current drawing context.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale(x: number, y: number): void
```

Scales a canvas based on scaling factors.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal scale factor. |
| y | number | Yes | Vertical scale factor. |

## setLineDash

```TypeScript
setLineDash(segments: Array<number>): void
```

Sets the dash line style.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| segments | Array&lt;number&gt; | Yes | Interval of alternate line segments and the length of spacing. |

## setTransform

```TypeScript
setTransform(
    scaleX: number,
    skewX: number,
    skewY: number,
    scaleY: number,
    translateX: number,
    translateY: number,
  ): void
```

Uses same parameters as the transform() function to reset the existing transformation matrix and create a new transformation matrix.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scaleX | number | Yes | X-axis scale. |
| skewX | number | Yes | X-axis skew. |
| skewY | number | Yes | Y-axis skew. |
| scaleY | number | Yes | Y-axis scale. |
| translateX | number | Yes | X-axis translation. |
| translateY | number | Yes | Y-axis translation. |

## stroke

```TypeScript
stroke(): void
```

Draws a border stroke.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stroke

```TypeScript
stroke(path: Path2D): void
```

Draws a path stroke.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | Yes | The object of Path2D. |

## strokeRect

```TypeScript
strokeRect(x: number, y: number, width: number, height: number): void
```

Draws a rectangle stroke on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the upper left corner of the rectangle stroke. |
| y | number | Yes | Y-coordinate of the upper left corner of the rectangle stroke. |
| width | number | Yes | Width of the rectangle stroke. |
| height | number | Yes | Height of the rectangle stroke. |

## strokeText

```TypeScript
strokeText(text: string, x: number, y: number): void
```

Draws a text stroke on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text stroke to draw. |
| x | number | Yes | X-coordinate of the lower left corner of the text stroke. |
| y | number | Yes | Y-coordinate of the lower left corner of the text stroke. |

## transferFromImageBitmap

```TypeScript
transferFromImageBitmap(bitmap: ImageBitmap): void
```

Draws the Bitmap to the current canvas.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bitmap | ImageBitmap | Yes |  |

## transform

```TypeScript
transform(scaleX: number, skewX: number, skewY: number, scaleY: number, translateX: number, translateY: number): void
```

Defines a transformation matrix. To transform a graph, you only need to set parameters of the matrix. The coordinates of the corresponding graph are multiplied by the matrix values to obtain new coordinates of the transformed graph. You can use the matrix to implement multiple transform effects.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scaleX | number | Yes | X-axis scale. |
| skewX | number | Yes | X-axis skew. |
| skewY | number | Yes | Y-axis skew. |
| scaleY | number | Yes | Y-axis scale. |
| translateX | number | Yes | X-axis translation. |
| translateY | number | Yes | Y-axis translation. |

## translate

```TypeScript
translate(x: number, y: number): void
```

Moves the origin of the coordinate system.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-axis translation. |
| y | number | Yes | Y-axis translation. |

## fillStyle

```TypeScript
fillStyle?: string | CanvasGradient | CanvasPattern
```

Sets the style of a paint to fill an area. Paint color used to fill the area. Canvas gradient object used by the paint. You can call createLinearGradient() to create a CanvasGradient object. Canvas pattern. You can call createPattern() to create a CanvasPattern object.

**Type:** string &#124; [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-canvaspattern-i.md)

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font: string
```

Sets the font style. Font style. The default value is 10px sans-serif in tv, phone, tablet, wearable. The default value is 30px SourceHanSansSC-Regular in smartVision.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalAlpha

```TypeScript
globalAlpha: number
```

Sets the alpha value. Global alpha value to set. The value ranges from 0.0 (completely transparent) to 1.0 (completely opaque).

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## globalCompositeOperation

```TypeScript
globalCompositeOperation: string
```

Sets the composite operation type. source-over Default value. Displays the new drawing above the existing drawing. source-atop Displays the new drawing on the top of the existing drawing. source-in Displays the new drawing inside the existing drawing. source-out Displays part of the new drawing that is outside of the existing drawing. destination-over Displays the existing drawing above the new drawing. destination-atop Displays the existing drawing above the new drawing. destination-in Displays the existing drawing inside the new drawing. destination-out Displays part of the existing drawing that is outside of the new drawing. lighter Displays both the new drawing and the existing drawing. copy Displays the new drawing and neglects the existing drawing. xor Combines the new drawing and existing drawing using the XOR operation.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSmoothingEnabled

```TypeScript
imageSmoothingEnabled: boolean
```

Sets whether an image is smooth. default value is true.

**Type:** boolean

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineCap

```TypeScript
lineCap: string
```

Sets the style of line endpoints. Style of line endpoints. Available values include: butt (default): The endpoints of the line are in square. round: The endpoints of the line are rounded. square: The endpoints of the line are in square, and each end of the line is added with a rectangle whose length is the same as the line thickness and whose width is half of the line thickness.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineDashOffset

```TypeScript
lineDashOffset: number
```

Sets the dash line offset. Dash line offset. The value is a float number starting from 0.0.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineJoin

```TypeScript
lineJoin: string
```

Sets the style for an intersection point where a line joins another. Style of the intersection point of lines. Available values include: round: The intersection part is a sector. The radius of a rounded corner is equal to the line width. bevel: The intersection part is a triangle. The rectangular corner of each line is independent. miter (default): The intersection part has a miter corner by extending the outside edges of the lines until they meet. You can view the effect of this attribute in miterLimit.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineWidth

```TypeScript
lineWidth?: number
```

Sets the width of a line.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## miterLimit

```TypeScript
miterLimit: number
```

Sets the maximum miter length. The miter length is the distance between the inner corner and the outer corner where two lines meet. Maximum miter length. The default value is 10.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowBlur

```TypeScript
shadowBlur: number
```

Sets the shadow blur degree. Shadow blur degree. A larger value indicates a more blurred shadow. The value is of the float type, and the default value is 0.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowColor

```TypeScript
shadowColor: string
```

Sets the shadow color.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetX

```TypeScript
shadowOffsetX: number
```

Sets the x-axis shadow offset relative to the original object. X-axis shadow offset relative to the original object.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadowOffsetY

```TypeScript
shadowOffsetY: number
```

Sets the y-axis shadow offset relative to the original object. Y-axis shadow offset relative to the original object.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeStyle

```TypeScript
strokeStyle?: string | CanvasGradient | CanvasPattern
```

Sets the stroke paint style. Color of the stroke paint. Canvas gradient object used by the paint. You can call createLinearGradient() to create a CanvasGradient object. Canvas pattern. You can call createPattern() to create a CanvasPattern object.

**Type:** string &#124; [CanvasGradient](arkts-arkui-viewmodel-canvasgradient-i.md) &#124; [CanvasPattern](arkts-arkui-canvaspattern-canvaspattern-i.md)

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign: "left" | "right" | "center" | "start" | "end"
```

Sets the text alignment mode. Text alignment mode. Available values include: left (default): The text is left-aligned. right: The text is right-aligned. center: The text is center-aligned. start: The text is aligned with the start bound. Can't be supported by smartVision. end: The text is aligned with the end bound. Can't be supported by smartVision. NOTE In the ltr layout mode, the value start equals to left. In the rtl layout mode, the value start equals to right.

**Type:** "left" &#124; "right" &#124; "center" &#124; "start" &#124; "end"

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textBaseline

```TypeScript
textBaseline: string
```

Sets a text baseline in the horizontal direction for text alignment. Text baseline. Available values include: alphabetic (default): The text baseline is the normal alphabetic baseline. top: The text baseline is on the top of the text bounding box. hanging: The text baseline is a hanging baseline over the text. middle: The text baseline is in the middle of the text bounding box. ideographic: The text baseline is the ideographic baseline. If a character exceeds the alphabetic baseline, the ideographic baseline is located at the bottom of the excessive character. bottom: The text baseline is at the bottom of the text bounding box. Its difference from the ideographic baseline is that the ideographic baseline does not consider letters in the next line.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
