# Class (Brush)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T07:54:00.476Z pushedAt=2026-08-25T01:39:20.241Z -->

Defines a brush object, which is used to set the fill style of a shape, including color, anti-aliasing, blend mode, color filter, mask filter, shader effect, shadow layer effect, and image filter. It also supports obtaining properties such as color, transparency, and anti-aliasing, and resetting the brush to its initial state.

A brush takes effect only after it is bound to the canvas through the [attachBrush](arkts-apis-graphics-drawing-Canvas.md#attachbrush) method of Canvas, and it is unbound through the [detachBrush](arkts-apis-graphics-drawing-Canvas.md#detachbrush) method after drawing is complete. A brush is used for shape filling, while a pen is used for shape stroking. For details, see [Pen](arkts-apis-graphics-drawing-Pen.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>12+</sup>

constructor()

Constructs a new brush object. Default configuration: a newly created brush has anti-aliasing disabled and the blend mode set to SRC_OVER by default, and no color filter, mask filter, shader effect, shadow layer effect, or image filter is set.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
```

## constructor<sup>12+</sup>

constructor(brush: Brush)

Copies a **Brush** object to create a new one.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type       | Mandatory| Description             |
| ------| ----------- | ---- | ---------------- |
| brush     | [Brush](arkts-apis-graphics-drawing-Brush.md) | Yes  | **Brush** object to copy.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
const brushColor: common2D.Color = { alpha: 255, red: 0, green: 255, blue: 0 };
brush.setColor(brushColor);
const newBrush = new drawing.Brush(brush);
```

## setColor

setColor(color: common2D.Color) : void

Sets the color of the brush. The set color is used as the base color for shape filling. When no ShaderEffect is set, rendering and filling are performed with this color.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) | Yes   | Color in ARGB format. The value range of each color channel is an integer in [0, 255]. Floating-point numbers within the range are rounded down. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const brush = new drawing.Brush();
brush.setColor(color);
```

## setColor<sup>12+</sup>

setColor(alpha: number, red: number, green: number, blue: number): void

Sets a color for this brush. This API provides better performance than [setColor](#setcolor) and is recommended.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description                                              |
| ------ | ------ | ---- | -------------------------------------------------- |
| alpha  | number | Yes   | Transparency channel value of the ARGB format color. The value is an integer in the range [0, 255]. Floating-point numbers within the range are rounded down. |
| red    | number | Yes   | Red channel value of the ARGB format color. The value is an integer in the range [0, 255]. Floating-point numbers within the range are rounded down.   |
| green  | number | Yes   | Green channel value of the ARGB format color. The value is an integer in the range [0, 255]. Floating-point numbers within the range are rounded down.   |
| blue   | number | Yes   | Blue channel value of the ARGB format color. The value is an integer in the range [0, 255]. Floating-point numbers within the range are rounded down.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setColor(255, 255, 0, 0);
```

## setColor<sup>18+</sup>

setColor(color: number) : void

Sets the color of the brush. The difference from [setColor](#setcolor) is that the color can be set directly through a hexadecimal ARGB value.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | number | Yes   | Color in hexadecimal ARGB format, represented as a 32-bit unsigned integer in the format 0xAARRGGBB, where AA is the alpha channel, RR is the red channel, GG is the green channel, and BB is the blue channel. Each channel ranges from 0x00 to 0xFF, and the overall value range is [0x00000000, 0xFFFFFFFF]. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setColor(0xffff0000);
```

## setColor4f<sup>20+</sup>

setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager \| null): void

Sets the color and standard color gamut of the brush. The difference from [setColor](#setcolor) is that the color gamut can be set separately, which applies to scenarios where the color gamut needs to be set independently.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color4f  | [common2D.Color4f](js-apis-graphics-common2D.md#color4f20) | Yes   | Color in ARGB format. The value of each color channel is a floating-point number between 0.0 and 1.0. Values greater than 1.0 are set to 1.0, and values less than 0.0 are set to 0.0. The color value is mapped in the color gamut specified by the colorSpace parameter.|
| colorSpace  | [colorSpaceManager.ColorSpaceManager](js-apis-colorSpaceManager.md#colorspacemanager) \| null | Yes   | Standard color gamut object, which must be created through the [colorSpaceManager.create()](js-apis-colorSpaceManager.md#colorspacemanagercreate) method. It is used together with color4f to determine the color gamut in which the color4f color value is mapped. null indicates that the sRGB color gamut is used.|

**Example**

```ts
import { common2D, drawing, colorSpaceManager } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = { alpha: 1, red: 0.5, green: 0.4, blue: 0.7 };
brush.setColor4f(color4f, colorSpace);
```

## getColor<sup>12+</sup>

getColor(): common2D.Color

Obtains the color of this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
| common2D.Color | Color of the brush, which is a color object in ARGB format containing four channel values: alpha, red, green, and blue. Each channel value is an integer in the range [0, 255]. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const brush = new drawing.Brush();
brush.setColor(color);
let currentColor = brush.getColor();
```

## getColor4f<sup>20+</sup>

getColor4f(): common2D.Color4f

Obtains the brush color. The difference between this method and [getColor](#getcolor12) is that this method returns a floating point number.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
| [common2D.Color4f](js-apis-graphics-common2D.md#color4f20) | Color of the brush, which is an ARGB color object in floating-point format, with each channel value being a floating-point number in the range [0.0, 1.0]. |

**Example**

```ts
import { common2D, drawing, colorSpaceManager } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = { alpha: 1, red: 0.5, green: 0.4, blue: 0.7 };
brush.setColor4f(color4f, colorSpace);
let color = brush.getColor4f();
```

## getHexColor<sup>18+</sup>

getHexColor(): number

Obtains the hexadecimal ARGB format value of the brush color. The difference from [getColor](#getcolor12) is that the return value type is a 32-bit unsigned integer in hexadecimal ARGB format.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
| number | Color, represented as a 32-bit unsigned integer in hexadecimal ARGB format.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let brush = new drawing.Brush();
brush.setColor(color);
let hexColor: number = brush.getHexColor();
console.info('getHexColor: ', hexColor.toString(16));
```

## setAntiAlias

setAntiAlias(aa: boolean) : void

Sets whether to enable anti-aliasing for the brush. After anti-aliasing is enabled, the edges of the shape are displayed more smoothly. If this API is not called, anti-aliasing is disabled by default.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description                                             |
| ------ | ------- | ---- | ------------------------------------------------- |
| aa     | boolean | Yes  | Whether to enable anti-aliasing. The value **true** means to enable anti-aliasing, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setAntiAlias(true);
```

## isAntiAlias<sup>12+</sup>

isAntiAlias(): boolean

Checks whether anti-aliasing is enabled for this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Check result. The value **true** means that anti-aliasing is enabled, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let isAntiAlias = brush.isAntiAlias();
```

## setAlpha

setAlpha(alpha: number) : void

Sets the transparency of the brush. After setAlpha is called, the transparency set by setAlpha takes effect during rendering, overriding the alpha channel value of the Color object in setColor.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| alpha  | number | Yes   | Integer in the range [0, 255] used to represent transparency. Floating-point numbers within the range are rounded down. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setAlpha(128);
```

## getAlpha<sup>12+</sup>

getAlpha(): number

Obtains the alpha value of this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description             |
| ------ | ---------------- |
| number | Return the transparency of the brush, which is an integer in the value range [0, 255]. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let alpha = brush.getAlpha();
```

## setColorFilter

setColorFilter(filter: ColorFilter | null) : void

Sets a color filter for this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                       | Mandatory| Description        |
| ------ | --------------------------- | ---- | ------------ |
| filter | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) \| null | Yes | Color filter used for color adjustment of the drawing content (such as gamma correction, color matrix transformation, etc.). null indicates clearing the color filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
brush.setColorFilter(colorFilter);
```

## setMaskFilter<sup>12+</sup>

setMaskFilter(filter: MaskFilter | null): void

Sets a mask filter for this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                      | Mandatory| Description     |
| ------ | ------------------------- | ---- | --------- |
| filter | [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md) \| null | Yes | Mask filter, used for scenarios such as blurring the edges of drawn graphics. null indicates clearing the mask filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const brush = new drawing.Brush();
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
    brush.setMaskFilter(maskFilter);
  }
}
```

## setShaderEffect<sup>12+</sup>

setShaderEffect(shaderEffect: ShaderEffect | null): void

Sets the shader effect for this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type                      | Mandatory| Description        |
| ------- | ------------------------- | ---- | ------------ |
| shaderEffect  | [ShaderEffect](arkts-apis-graphics-drawing-ShaderEffect.md) \| null | Yes   | Shader effect object used to implement complex drawing effects such as gradient fill and pattern fill. null indicates clearing the shader effect. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100, y: 100}, {x: 300, y: 300}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
brush.setShaderEffect(shaderEffect);
```

## setShadowLayer<sup>12+</sup>

setShadowLayer(shadowLayer: ShadowLayer | null): void

Sets a shadow layer for this brush. The shadow layer effect takes effect only when text is drawn through methods such as [drawTextBlob](arkts-apis-graphics-drawing-Canvas.md#drawtextblob) of Canvas.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type                      | Mandatory| Description     |
| ------- | ------------------------- | ---- | --------- |
| shadowLayer  | [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) \| null | Yes   | Shadow layer object, used to add a shadow effect to the brush. null indicates clearing the shadow layer effect. This shadow layer effect takes effect only when drawing text. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(60);

    let textBlob = drawing.TextBlob.makeFromString('hello', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    let pen = new drawing.Pen();
    pen.setStrokeWidth(2.0);

    let penColor : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    pen.setColor(penColor);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 100);
    canvas.detachPen();

    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
    pen.setShadowLayer(shadowLayer);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 200);
    canvas.detachPen();

    let brush = new drawing.Brush();
    let brushColor : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    brush.setColor(brushColor);
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 300, 100);
    canvas.detachBrush();

    brush.setShadowLayer(shadowLayer);
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 300, 200);
    canvas.detachBrush();
  }
}
```

## setBlendMode

setBlendMode(mode: BlendMode) : void

Sets a blend mode for this brush. If this API is not called, the default blend mode is **SRC_OVER**.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                   | Mandatory| Description            |
| ------ | ----------------------- | ---- | ---------------- |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode) | Yes   | Blend mode of the color, used to control how the source color is blended with the existing destination color during drawing. If this interface is not called to set the blend mode, the system default blend mode is SRC_OVER. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setBlendMode(drawing.BlendMode.SRC);
```

## setImageFilter<sup>12+</sup>

setImageFilter(filter: ImageFilter | null): void

Sets an image filter for this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| filter    | [ImageFilter](arkts-apis-graphics-drawing-ImageFilter.md) \| null | Yes   | Image filter used to apply image processing such as blurring and sharpening to the drawing content. null indicates clearing the image filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. | 

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let brush = new drawing.Brush();
let imageFilter = drawing.ImageFilter.createBlurImageFilter(5, 10, drawing.TileMode.DECAL);
brush.setImageFilter(imageFilter);
brush.setImageFilter(null);
```

## getColorFilter<sup>12+</sup>

getColorFilter(): ColorFilter

Obtains the color filter of this brush.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the color filter of the brush, which is used to adjust the color of the drawn content, such as gamma correction and color matrix transformation. |

**Example**

```ts 
import { drawing } from '@kit.ArkGraphics2D';

let brush = new drawing.Brush();
let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
brush.setColorFilter(colorFilter);
let currentFilter = brush.getColorFilter();   
```

## reset<sup>12+</sup>

reset(): void

Resets this brush to the initial state, clearing the set color, transparency, anti-aliasing, color filter, mask filter, shader effect, shadow layer effect, blend mode, and image filter. The specific values of the initial state are as follows: anti-aliasing is disabled, the blend mode is SRC_OVER, and no color filter, mask filter, shader effect, shadow layer effect, or image filter is set. To use the preceding attributes, call the corresponding set APIs again.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.reset();
```