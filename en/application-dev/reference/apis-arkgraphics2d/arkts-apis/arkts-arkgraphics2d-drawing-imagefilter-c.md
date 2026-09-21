# ImageFilter

```TypeScript
class ImageFilter
```

Implements an image filter.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - This module uses the physical pixel unit, px.
> 
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlendImageFilter

```TypeScript
static createBlendImageFilter(mode: BlendMode, background: ImageFilter, foreground: ImageFilter): ImageFilter
```

Creates a filter by blending two existing filters in a certain way.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |
| background | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Yes | Filter that serves as the destination color in blend mode. |
| foreground | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Yes | Filter that serves as the source color in blend mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let dx = 15.0;
let dy = 10.0;
let offsetFilter1 = drawing.ImageFilter.createOffsetImageFilter(dx, dy, null);
let x = 15.0;
let y = 30.0;
let offsetFilter2 = drawing.ImageFilter.createOffsetImageFilter(x, y, null);
let blendImageFilter = drawing.ImageFilter.createBlendImageFilter(drawing.BlendMode.SRC_IN, offsetFilter1, offsetFilter2);
```

## createBlurImageFilter

```TypeScript
static createBlurImageFilter(sigmaX: number, sigmaY: number,
        tileMode: TileMode, imageFilter?: ImageFilter | null): ImageFilter
```

Creates an image filter with a given blur effect.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sigmaX | number | Yes | Standard deviation of the Gaussian blur along the X axis. The value must be a floating point number greater than 0. |
| sigmaY | number | Yes | Standard deviation of the Gaussian blur along the Y axis. The value must be a floating point number greater than 0. |
| tileMode | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode to apply to the edges. |
| imageFilter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) &#124; null | No | Filter to which the image filter will be applied. The default value is null, indicating that the image filter is directly applied to the original image. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let imgFilter = drawing.ImageFilter.createBlurImageFilter(5, 10, drawing.TileMode.CLAMP);
```

## createComposeImageFilter

```TypeScript
static createComposeImageFilter(cOuter: ImageFilter, cInner: ImageFilter): ImageFilter
```

Cascades two image filters to create a new image filter. The first filter's output becomes the second filter's input. The second filter then processes this input to produce the final result.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cOuter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Yes | The second filter in the cascade, which processes the first filter's output. If the second filter is empty and the first filter is not empty, the final result is the first filter's output. The two filters cannot be empty at the same time. |
| cInner | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Yes | The first filter in the cascade, which directly processes the original image content. If the first filter is empty and the second filter is not empty, the final result is the second filter's output. The two filters cannot be empty at the same time. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let blurSigmaX = 10.0;
let blurSigmaY = 10.0;
let blurFilter = drawing.ImageFilter.createBlurImageFilter(blurSigmaX, blurSigmaY, drawing.TileMode.CLAMP, null);
let colorMatrix:Array<number> = [
  0, 0, 0, 0, 0,
  0, 1, 0, 0, 0,
  0, 0, 1, 0, 0,
  0, 0, 0, 1, 0
];
let redRemovalFilter = drawing.ColorFilter.createMatrixColorFilter(colorMatrix);
let colorFilter = drawing.ImageFilter.createFromColorFilter(redRemovalFilter, null);
let composedImageFilter = drawing.ImageFilter.createComposeImageFilter(colorFilter, blurFilter);
```

## createFromColorFilter

```TypeScript
static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter | null): ImageFilter
```

Creates an image filter object with a given color filter effect.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorFilter | [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Yes | Color filter. |
| imageFilter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) &#124; null | No | Filter to which the image filter will be applied. The default value is null, indicating that the image filter is directly applied to the original image.<br>**Since:** 20 |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let imgFilter = drawing.ImageFilter.createBlurImageFilter(5, 10, drawing.TileMode.CLAMP);
let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
let imgFilter1 = drawing.ImageFilter.createFromColorFilter(colorFilter, imgFilter);
```

## createFromImage

```TypeScript
static createFromImage(pixelmap: image.PixelMap, srcRect?: common2D.Rect | null, dstRect?: common2D.Rect | null): ImageFilter
```

Creates an image filter from a given image. You are advised not to use the function for the canvas of the capture type because it affects the performance.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image object. |
| srcRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) &#124; null | No | (Optional) Pixel area of the image to be applied to the filter. This parameter is left empty by default, which means that the entire **PixelMap** area is applied. |
| dstRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) &#124; null | No | (Optional) Area to be rendered. This parameter is left empty by default, which means that the value is the same as that of **srcRect**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const width = 1000;
    const height = 1000;
    const bufferSize = width * height * 4;
    const color: ArrayBuffer = new ArrayBuffer(bufferSize);

    const colorData = new Uint8Array(color);
    for (let i = 0; i < colorData.length; i += 4) {
      colorData[i] = 255;
      colorData[i + 1] = 156;
      colorData[i + 2] = 0;
      colorData[i + 3] = 255;
    }

    let opts: image.InitializationOptions = {
      editable: true,
      pixelFormat: 3,
      size: { height, width }
    };

    let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
    let srcRect: common2D.Rect = {
      left: 10,
      top: 10,
      right: 80,
      bottom: 80
    };
    let dstRect: common2D.Rect = {
      left: 200,
      top: 200,
      right: 400,
      bottom: 400
    };
    if (pixelMap != null) {
      let filter = drawing.ImageFilter.createFromImage(pixelMap, srcRect, dstRect);
    }
  }
}
```

## createFromShaderEffect

```TypeScript
static createFromShaderEffect(shader: ShaderEffect): ImageFilter
```

Creates an **ImageFilter** object based on a shader.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | Yes | Shader effect to be applied to the image. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let shaderEffect = drawing.ShaderEffect.createColorShader(0xFF00FF00);
let renderEffect = drawing.ImageFilter.createFromShaderEffect(shaderEffect);
```

## createOffsetImageFilter

```TypeScript
static createOffsetImageFilter(dx: number, dy: number, input?: ImageFilter | null): ImageFilter
```

Creates an offset filter to translate the input filter based on the specified vector.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | number | Yes | Horizontal translation distance. The value is a floating point number. |
| dy | number | Yes | Vertical translation distance. The value is a floating point number. |
| input | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) &#124; null | No | Filter to be translated. This parameter is left empty by default, which means that the drawing result without the filtering effect is translated. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Image filter created. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let dx = 15.0;
let dy = 10.0;
let offsetFilter = drawing.ImageFilter.createOffsetImageFilter(dx, dy, null);
```
