# ShaderEffect

Implements the shader effect. After a shader effect is set for a pen or brush, the shader effect instead of the color attribute is used for drawing. In this case, the alpha value set for the pen or brush still takes effect.

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

## createColorShader

```TypeScript
static createColorShader(color: number): ShaderEffect
```

Creates a **ShaderEffect** object with a single color.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | number | Yes | Color in the ARGB format. The value is a 32-bit unsigned integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object with a single color. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## createComposeShader

```TypeScript
static createComposeShader(dstShaderEffect: ShaderEffect, srcShaderEffect: ShaderEffect,
        blendMode: BlendMode): ShaderEffect
```

Creates a shader by blending two existing shaders in a certain way.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dstShaderEffect | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | Yes | Shader that serves as the destination color in blend mode. |
| srcShaderEffect | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | Yes | Shader that serves as the source color in blend mode. |
| blendMode | [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

## createConicalGradient

```TypeScript
static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point,
        endRadius: number, colors: Array<number>, mode: TileMode,
        pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect
```

Creates a **ShaderEffect** object that generates a conical gradient between two given circles.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Center of the start circle of the gradient. |
| startRadius | number | Yes | Radius of the start circle of the gradient. A negative number is invalid. The value is a floating point number. |
| endPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Center of the end circle of the gradient. |
| endRadius | number | Yes | Radius of the end circle of the gradient. A negative value is invalid. The value is a floating point number. |
| colors | Array&lt;number&gt; | Yes | Array of colors to distribute between the start circle and end circle. The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode of the shader effect. |
| pos | Array&lt;number&gt; &#124; null | No | Relative position of each color in the color array. The array length must be the same as that of **colors**. The first element in the array must be 0.0, the last element must be 1.0, and the middle elements must be between 0.0 and 1.0 and increase by index. The default value is null, indicating that colors are evenly distributed between the two circles. |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) &#124; null | No | **Matrix** object used to perform matrix transformation on the shader effect. The default value is null, indicating the identity matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageShader

```TypeScript
static createImageShader(pixelmap: image.PixelMap, tileX: TileMode, tileY: TileMode,
        samplingOptions: SamplingOptions, matrix?: Matrix | null): ShaderEffect
```

Creates a shader based on an image. You are advised not to use the function for the canvas of the capture type because it affects the performance.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image object to be sampled. |
| tileX | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode in the horizontal direction. |
| tileY | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode in the vertical direction. |
| samplingOptions | [SamplingOptions](arkts-arkgraphics2d-drawing-samplingoptions-c.md) | Yes | Image sampling options. |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) &#124; null | No | (Optional) Matrix transformation applied to an image. If this parameter is left empty, no transformation is applied. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

## createLinearGradient

```TypeScript
static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array<number>,
        mode: TileMode, pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect
```

Creates a **ShaderEffect** object that generates a linear gradient between two points.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Start point. |
| endPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | End point. |
| colors | Array&lt;number&gt; | Yes | Array of colors to distribute between the two points. The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode of the shader effect. |
| pos | Array&lt;number&gt; &#124; null | No | Relative position of each color in the color array. The array length must be the same as that of **colors**. The first element in the array must be 0.0, the last element must be 1.0, and the middle elements must be between 0.0 and 1.0 and increase by index. The default value is null, indicating that colors are evenly distributed between the two points. |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) &#124; null | No | **Matrix** object used to perform matrix transformation on the shader effect. The default value is null, indicating the identity matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createRadialGradient

```TypeScript
static createRadialGradient(centerPt: common2D.Point, radius: number, colors: Array<number>,
      mode: TileMode, pos?: Array<number> | null, matrix?: Matrix | null): ShaderEffect
```

Creates a **ShaderEffect** object that generates a radial gradient based on the center and radius of a circle. A radial gradient refers to the color transition that spreads out gradually from the center of a circle.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| centerPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Center of the circle. |
| radius | number | Yes | Radius of the gradient. A negative number is invalid. The value is a floating point number. |
| colors | Array&lt;number&gt; | Yes | Array of colors to distribute between the center and ending shape of the circle. The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode of the shader effect. |
| pos | Array&lt;number&gt; &#124; null | No | Relative position of each color in the color array. The array length must be the same as that of **colors**. The first element in the array must be 0.0, the last element must be 1.0, and the middle elements must be between 0.0 and 1.0 and increase by index. The default value is null, indicating that colors are evenly distributed between the center and ending shape of the circle. |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) &#124; null | No | **Matrix** object used to perform matrix transformation on the shader effect. The default value is null, indicating the identity matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createSweepGradient

```TypeScript
static createSweepGradient(centerPt: common2D.Point, colors: Array<number>,
        mode: TileMode, startAngle: number, endAngle: number, pos?: Array<number> | null,
        matrix?: Matrix | null): ShaderEffect
```

Creates a **ShaderEffect** object that generates a color sweep gradient around a given center point, either in a clockwise or counterclockwise direction.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| centerPt | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Center of the circle. |
| colors | Array&lt;number&gt; | Yes | Array of colors to distribute between the start angle and end angle. The values in the array are 32-bit (ARGB) unsigned integers. |
| mode | [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Yes | Tile mode of the shader effect. |
| startAngle | number | Yes | Start angle of the sweep gradient, in degrees. The value 0 indicates the positive direction of the X axis. A positive number indicates an offset towards the positive direction, and a negative number indicates an offset towards the negative direction. The value is a floating point number. |
| endAngle | number | Yes | End angle of the sweep gradient, in degrees. The value 0 indicates the positive direction of the X axis. A positive number indicates an offset towards the positive direction, and a negative number indicates an offset towards the negative direction. A value less than the start angle is invalid. The value is a floating point number. |
| pos | Array&lt;number&gt; &#124; null | No | Relative position of each color in the color array. The array length must be the same as that of **colors**. The first element in the array must be 0.0, the last element must be 1.0, and the middle elements must be between 0.0 and 1.0 and increase by index. The default value is null, indicating that the colors are evenly distributed between the start angle and end angle. |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) &#124; null | No | **Matrix** object used to perform matrix transformation on the shader effect. The default value is null, indicating the identity matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | **ShaderEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
