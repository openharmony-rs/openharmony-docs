# Pen

Defines a pen, which is used to describe the style and color to outline a shape.

> **NOTE:** 
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Pen** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(pen: Pen)
```

Copies a **Pen** object to create a new one.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pen | [Pen](arkts-arkgraphics2d-drawing-pen-c.md) | Yes | **Pen** object to copy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## getAlpha

```TypeScript
getAlpha(): number
```

Obtains the alpha value of this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Alpha value of the pen. The return value is an integer ranging from 0 to 255. |

## getCapStyle

```TypeScript
getCapStyle(): CapStyle
```

Obtains the cap style of this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | Cap style. |

## getColor

```TypeScript
getColor(): common2D.Color
```

Obtains the color of this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Color of the pen. |

## getColor4f

```TypeScript
getColor4f(): common2D.Color4f
```

Obtains the pen color. The difference between this method and [getColor](#getcolor) is that this method returns a floating point number.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Color4f](arkts-arkgraphics2d-common2d-color4f-i.md) | Color of the pen. |

## getColorFilter

```TypeScript
getColorFilter(): ColorFilter
```

Obtains the color filter of this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

## getFillPath

```TypeScript
getFillPath(src: Path, dst: Path): boolean
```

Obtains the source path outline drawn using this pen and represents it using a destination path.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | Source path. |
| dst | [Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | Destination path. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the source path outline is obtained, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## getHexColor

```TypeScript
getHexColor(): number
```

Obtains the color of this pen.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Color, represented as a 32-bit unsigned integer in hexadecimal ARGB format. |

## getJoinStyle

```TypeScript
getJoinStyle(): JoinStyle
```

Obtains the join style of this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | Join style. |

## getMiterLimit

```TypeScript
getMiterLimit(): number
```

Obtains the maximum ratio allowed between the sharp corner length of a polyline and its line width.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum ratio obtained. |

## getWidth

```TypeScript
getWidth(): number
```

Obtains the stroke width of this pen. The width describes the thickness of the outline of a shape.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Stroke width for the pen, in px. |

## isAntiAlias

```TypeScript
isAntiAlias(): boolean
```

Checks whether anti-aliasing is enabled for this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that anti-aliasing is enabled, and **false** means the opposite. |

## reset

```TypeScript
reset(): void
```

Resets this pen to the initial state.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## setAlpha

```TypeScript
setAlpha(alpha: number): void
```

Sets an alpha value for this pen.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alpha | number | Yes | Alpha value. The value is an integer in the range [0, 255]. If a floating point number is passed in, the value is rounded down. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setAntiAlias

```TypeScript
setAntiAlias(aa: boolean): void
```

Enables anti-aliasing for this pen. Anti-aliasing makes the edges of the content smoother. If this API is not called, anti-aliasing is disabled by default.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aa | boolean | Yes | Whether to enable anti-aliasing. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setBlendMode

```TypeScript
setBlendMode(mode: BlendMode): void
```

Sets a blend mode for this pen.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setCapStyle

```TypeScript
setCapStyle(style: CapStyle): void
```

Sets the cap style for this pen. If this API is not called, the default cap style is **FLAT_CAP**.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | Yes | Cap style. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor

```TypeScript
setColor(color: common2D.Color): void
```

Sets a color for this pen.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | Color in ARGB format. The value of each color channel is an integer ranging from 0 to 255. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor

```TypeScript
setColor(alpha: number, red: number, green: number, blue: number): void
```

Sets a color for this pen. This API provides better performance than [setColor](#setcolor) and is recommended.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alpha | number | Yes | Alpha channel value of the color in ARGB format. The value is an integer ranging from 0 to 255. Any passed-in floating point number is rounded down. |
| red | number | Yes | Red channel value of the color in ARGB format. The value is an integer ranging from 0 to 255. Any passed-in floating point number is rounded down. |
| green | number | Yes | Green channel value of the color in ARGB format. The value is an integer ranging from 0 to 255. Any passed-in floating point number is rounded down. |
| blue | number | Yes | Blue channel value of the color in ARGB format. The value is an integer ranging from 0 to 2 55. Any passed-in floating point number is rounded down. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setColor

```TypeScript
setColor(color: number): void
```

Sets a color for this pen.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | number | Yes | Color in hexadecimal ARGB format. |

## setColor4f

```TypeScript
setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void
```

Sets the color and standard color gamut for this pen. The difference between this method and [setColor](#setcolor) is that the color gamut can be set separately.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color4f | [common2D.Color4f](arkts-arkgraphics2d-common2d-color4f-i.md) | Yes | Color in the ARGB format. The value of each color channel is a floating point number ranging from 0.0 to 1.0. Values above 1.0 default to **1.0**, and values below 0.0 default to **0.0**. |
| colorSpace | [colorSpaceManager.ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) &#124; null | Yes | Standard color gamut object. **null** indicates SRGB. |

## setColorFilter

```TypeScript
setColorFilter(filter: ColorFilter | null): void
```

Sets a color filter for this pen.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) &#124; null | Yes | Defines a color filter. If **null** is passed in, the color filter is cleared.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setDither

```TypeScript
setDither(dither: boolean): void
```

Enables dithering for this pen. Dithering make the drawn color more realistic.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dither | boolean | Yes | Whether to enable dithering. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setImageFilter

```TypeScript
setImageFilter(filter: ImageFilter | null): void
```

Sets an image filter for this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) &#124; null | Yes | Image filter. If **null** is passed in, the image filter effect of the pen will be cleared. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setJoinStyle

```TypeScript
setJoinStyle(style: JoinStyle): void
```

Sets the join style for this pen. If this API is not called, the default join style is **MITER_JOIN**.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | Yes | Join style. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setMaskFilter

```TypeScript
setMaskFilter(filter: MaskFilter | null): void
```

Adds a mask filter for this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) &#124; null | Yes | Mask filter. If **null** is passed in, the mask filter is cleared.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setMiterLimit

```TypeScript
setMiterLimit(miter: number): void
```

Sets the maximum ratio allowed between the sharp corner length of a polyline and its line width. When drawing a polyline with the pen, if [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) is set to **MITER_JOIN** and this maximum ratio is exceeded, the corner will be displayed as beveled instead of mitered.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| miter | number | Yes | Maximum ratio of the sharp corner length of the polyline to the line width. A negative number is processed as **4.0** during drawing. Non-negative numbers take effect normally. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setPathEffect

```TypeScript
setPathEffect(effect: PathEffect | null): void
```

Sets the path effect for this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) &#124; null | Yes | Implements a path effect. If **null** is passed in, the path filter is cleared.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setShaderEffect

```TypeScript
setShaderEffect(shaderEffect: ShaderEffect | null): void
```

Sets the shader effect for this pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shaderEffect | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) &#124; null | Yes | **ShaderEffect** object. If **null** is passed in, the shader effect will be cleared.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setShadowLayer

```TypeScript
setShadowLayer(shadowLayer: ShadowLayer | null): void
```

Sets a shadow layer for this pen. The shadow layer effect takes effect only when text is drawn.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shadowLayer | [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) &#124; null | Yes | Implements a shadow layer. If **null** is passed in, the shadow layer is cleared.<br>**Since:** 20 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setStrokeWidth

```TypeScript
setStrokeWidth(width: number): void
```

Sets the stroke width for this pen. The value **0** is treated as an unusually thin width. During drawing, the width of 0 is always drawn as 1 pixel wide, regardless of any scaling applied to the canvas. Negative values are also regarded as the value **0** during the drawing process.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Stroke width. The value is a floating point number. If a value less than 1 is passed in, the value **1** is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
