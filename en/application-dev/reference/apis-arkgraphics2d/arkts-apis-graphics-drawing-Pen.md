# Class (Pen)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d66ce495242bdf35b08a89dbf23cdf3929953623 translatedAt=2026-08-24T08:09:54.744Z pushedAt=2026-08-29T08:08:46.358Z -->

Pen object, which describes the outline information of the drawn shape. It supports setting the color, line width, anti-aliasing, transparency, blend mode, join style, line cap style, as well as drawing effects such as color filter, mask filter, path effect, shader effect, and shadow layer.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>12+</sup>

constructor()

A constructor used to create a **Pen** object.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
```

## constructor<sup>12+</sup>

constructor(pen: Pen)

Copies a **Pen** object to create a new one.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type       | Mandatory| Description             |
| ------| ----------- | ---- | ---------------- |
| pen     | [Pen](arkts-apis-graphics-drawing-Pen.md) | Yes  | **Pen** object to copy.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
const penColor: common2D.Color = { alpha: 255, red: 0, green: 255, blue: 0 };
pen.setColor(penColor);
pen.setStrokeWidth(10);
const newPen = new drawing.Pen(pen);
```

## setMiterLimit<sup>12+</sup>

setMiterLimit(miter: number): void

Sets the maximum ratio of the miter length to the line width. When the pen draws a polyline and [JoinStyle](arkts-apis-graphics-drawing-e.md#joinstyle12) is MITER_JOIN, if the ratio of the miter length to the line width is greater than the maximum ratio, the join is drawn with BEVEL_JOIN.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| miter  | number | Yes   | Maximum ratio of the miter length to the line width. A negative value is treated as 4.0 during drawing, and a non-negative value takes effect as the actual value passed in. This parameter is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setMiterLimit(5);
```

## getMiterLimit<sup>12+</sup>

getMiterLimit(): number

Obtains the maximum ratio of the miter length to the line width.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| -------| -------------------- |
| number | Maximum ratio obtained.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let miter = pen.getMiterLimit();
```

## setImageFilter<sup>12+</sup>

setImageFilter(filter: ImageFilter \| null): void

Sets an image filter for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| filter    | [ImageFilter](arkts-apis-graphics-drawing-ImageFilter.md) \| null | Yes  |  Image filter. If **null** is passed in, the image filter effect of the pen will be cleared.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorfilter = drawing.ColorFilter.createSRGBGammaToLinear();
let imgFilter = drawing.ImageFilter.createFromColorFilter(colorfilter);
let pen = new drawing.Pen();
pen.setImageFilter(imgFilter);
pen.setImageFilter(null);
```

## getColorFilter<sup>12+</sup>

getColorFilter(): ColorFilter

Obtains the color filter of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the color filter currently set for the pen, which can be used to query the current color filtering effect of the pen. |

**Example**

```ts 
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLumaColorFilter();
pen.setColorFilter(colorFilter);
let filter = pen.getColorFilter();
```

## setColor

setColor(color: common2D.Color) : void

Sets a color for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) | Yes  | Color in ARGB format. The value of each color channel is an integer ranging from 0 to 255.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
```

## setColor<sup>12+</sup>

setColor(alpha: number, red: number, green: number, blue: number): void

Sets a color for this pen. This API provides better performance than [setColor](#setcolor) and is recommended.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description                                               |
| ------ | ------ | ---- | -------------------------------------------------- |
| alpha  | number | Yes   | Transparency channel value of the color in ARGB format. The value range is [0, 255]. Floating-point numbers within the range are rounded down, and values out of range are truncated to 0 or 255. |
| red    | number | Yes   | Red channel value of the color in ARGB format. The value range is [0, 255]. Floating-point numbers within the range are rounded down, and values out of range are truncated to 0 or 255.   |
| green  | number | Yes   | Green channel value of the color in ARGB format. The value range is [0, 255]. Floating-point numbers within the range are rounded down, and values out of range are truncated to 0 or 255.   |
| blue   | number | Yes   | Blue channel value of the color in ARGB format. The value range is [0, 255]. Floating-point numbers within the range are rounded down, and values out of range are truncated to 0 or 255.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(255, 255, 0, 0);
```

## setColor<sup>18+</sup>

setColor(color: number) : void

Sets a color for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | number | Yes   | Color in hexadecimal ARGB format, in the format 0xAARRGGBB, where AA indicates the transparency channel, RR indicates the red channel, GG indicates the green channel, and BB indicates the blue channel. The value range of each channel is 00-FF, and the overall value range is [0x00000000, 0xFFFFFFFF]. Values out of the valid range are truncated. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(0xffff0000);
```

## setColor4f<sup>20+</sup>

setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager \| null): void

Sets the color and standard color gamut for this pen. The difference from [setColor](#setcolor) is that the color gamut can be set separately.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color4f  | [common2D.Color4f](js-apis-graphics-common2D.md#color4f20) | Yes   | Color in ARGB format, a floating-point number. The value range of each color channel is [0.0, 1.0]. Values out of range are truncated to 0.0 or 1.0. |
| colorSpace  | [colorSpaceManager.ColorSpaceManager](js-apis-colorSpaceManager.md#colorspacemanager) \| null | Yes  | Standard color gamut object. **null** indicates SRGB.|

**Example**

```ts
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = {alpha: 1, red: 0.5, green: 0.4, blue: 0.7};
pen.setColor4f(color4f, colorSpace);
```

## getColor<sup>12+</sup>

getColor(): common2D.Color

Obtains the color of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
| [common2D.Color](js-apis-graphics-common2D.md#color) | Color currently set for the pen. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
let colorGet = pen.getColor();
```

## getColor4f<sup>20+</sup>

getColor4f(): common2D.Color4f

Obtains the color of this pen. The difference from [getColor](#getcolor12) is that the return value type is [common2D.Color4f](js-apis-graphics-common2D.md#color4f20), and the color channel values are floating-point numbers, which is suitable for scenarios that require floating-point types.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
|[common2D.Color4f](js-apis-graphics-common2D.md#color4f20) | Returns the color currently set for the pen, represented as a floating-point number in ARGB format. The value range of each color channel is [0.0, 1.0]. |

**Example**

```ts
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = {alpha: 1, red: 0.5, green: 0.4, blue: 0.7};
pen.setColor4f(color4f, colorSpace);
let color = pen.getColor4f();
```

## getHexColor<sup>18+</sup>

getHexColor(): number

Obtains the color of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type          | Description           |
| -------------- | -------------- |
| number | Color, represented as a 32-bit unsigned integer in hexadecimal ARGB format.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let pen = new drawing.Pen();
pen.setColor(color);
let hexColor: number = pen.getHexColor();
console.info('getHexColor: ', hexColor.toString(16));
```

## setStrokeWidth

setStrokeWidth(width: number) : void

Sets the stroke width for this pen. The value **0** is treated as an unusually thin width. During drawing, the width of 0 is always drawn as 1 pixel wide, regardless of any scaling applied to the canvas. Negative values are also regarded as the value **0** during the drawing process.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| width  | number | Yes | Line width. This parameter is a floating-point number, in physical pixel px. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setStrokeWidth(5);
```

## getWidth<sup>12+</sup>

getWidth(): number

Obtains the stroke width of this pen. The width describes the thickness of the outline of a shape.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description           |
| ------ | -------------- |
| number | Stroke width for the pen, in px.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let width = pen.getWidth();
```

## setAntiAlias

setAntiAlias(aa: boolean) : void

Sets whether to enable anti-aliasing for this pen. When enabled, the edges of the shape are smoother when displayed. If this API is not called, anti-aliasing is disabled by default.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description                                             |
| ------ | ------- | ---- | ------------------------------------------------- |
| aa     | boolean | Yes  | Whether to enable anti-aliasing. **true** to enable, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAntiAlias(true);
```

## isAntiAlias<sup>12+</sup>

isAntiAlias(): boolean

Checks whether anti-aliasing is enabled for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Check result. The value **true** means that anti-aliasing is enabled, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let isAntiAlias = pen.isAntiAlias();
```

## setAlpha

setAlpha(alpha: number) : void

Sets an alpha value for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                                    |
| ------ | ------ | ---- | ---------------------------------------- |
| alpha  | number | Yes  | Transparency. Value range: [0, 255]. Rounded down when a floating-point number is passed in. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAlpha(128);
```

## getAlpha<sup>12+</sup>

getAlpha(): number

Obtains the alpha value of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description             |
| ------ | ---------------- |
| number | Alpha value of the pen. The return value is an integer ranging from 0 to 255.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let alpha = pen.getAlpha();
```

## setColorFilter

setColorFilter(filter: ColorFilter \| null) : void

Sets a color filter for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                       | Mandatory| Description        |
| ------ | --------------------------- | ---- | ------------ |
| filter | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) \| null | Yes  | Defines a color filter. If **null** is passed in, the color filter is cleared.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
pen.setColorFilter(colorFilter);
```

## setMaskFilter<sup>12+</sup>

setMaskFilter(filter: MaskFilter \| null): void

Adds a mask filter for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                      | Mandatory| Description     |
| ------ | ------------------------- | ---- | --------- |
| filter | [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md) \| null | Yes  | Mask filter. If **null** is passed in, the mask filter is cleared.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
    pen.setMaskFilter(maskFilter);
  }
}
```

## setPathEffect<sup>12+</sup>

setPathEffect(effect: PathEffect \| null): void

Sets the path effect for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type                      | Mandatory| Description        |
| ------- | ------------------------- | ---- | ------------ |
| effect  | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) \| null | Yes   | Path effect object used to set the path drawing style such as dashed lines and joins. null indicates that the path effect is cleared. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let pathEffect = drawing.PathEffect.createDashPathEffect([30, 10], 0);
    pen.setPathEffect(pathEffect);
  }
}
```

## setShaderEffect<sup>12+</sup>

setShaderEffect(shaderEffect: ShaderEffect \| null): void

Sets the shader effect for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type                      | Mandatory| Description        |
| ------- | ------------------------- | ---- | ------------ |
| shaderEffect  | [ShaderEffect](arkts-apis-graphics-drawing-ShaderEffect.md) \| null | Yes   | Shader effect object. null indicates clearing the shader effect. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100, y: 100}, {x: 300, y: 300}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
pen.setShaderEffect(shaderEffect);
```

## setShadowLayer<sup>12+</sup>

setShadowLayer(shadowLayer: ShadowLayer \| null): void

Sets a shadow layer for this pen. The shadow layer effect takes effect only when text is drawn.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type                      | Mandatory| Description     |
| ------- | ------------------------- | ---- | --------- |
| shadowLayer  | [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) \| null | Yes  | Implements a shadow layer. If **null** is passed in, the shadow layer is cleared.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(60);
    let textBlob = drawing.TextBlob.makeFromString("hello", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    let pen = new drawing.Pen();
    pen.setStrokeWidth(2.0);
    let pen_color : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    pen.setColor(pen_color);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 100);
    canvas.detachPen();
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
    pen.setShadowLayer(shadowLayer);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 200);
    canvas.detachPen();
  }
}
```

## setBlendMode

setBlendMode(mode: BlendMode) : void

Sets a blend mode for this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                   | Mandatory| Description            |
| ------ | ----------------------- | ---- | ---------------- |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode) | Yes  | Blend mode.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setBlendMode(drawing.BlendMode.SRC);
```

## setJoinStyle<sup>12+</sup>

setJoinStyle(style: JoinStyle): void

Sets the join style for this pen. If this API is not called, the default join style is **MITER_JOIN**.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                    | Mandatory| Description            |
| ------ | ----------------------- | ---- | --------------- |
| style  | [JoinStyle](arkts-apis-graphics-drawing-e.md#joinstyle12) | Yes  | Join style.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
  }
}
```

## getJoinStyle<sup>12+</sup>

getJoinStyle(): JoinStyle

Obtains the join style of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type         | Description                   |
| ------------- | ---------------------- |
| [JoinStyle](arkts-apis-graphics-drawing-e.md#joinstyle12) | Returns the style of the polyline join.         |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
    pen.getJoinStyle();
  }
}
```

## setCapStyle<sup>12+</sup>

setCapStyle(style: CapStyle): void

Sets the cap style for this pen. If this API is not called, the default cap style is **FLAT_CAP**.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                    | Mandatory| Description                  |
| ------ | ----------------------- | ---- | --------------------- |
| style  | [CapStyle](arkts-apis-graphics-drawing-e.md#capstyle12)   | Yes  | Cap style.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
  }
}
```

## getCapStyle<sup>12+</sup>

getCapStyle(): CapStyle

Obtains the cap style of this pen.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type        | Description               |
| ------------ | ------------------ |
| [CapStyle](arkts-apis-graphics-drawing-e.md#capstyle12)     | Returns the line cap style of the pen. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
    pen.getCapStyle();
  }
}
```

## setDither

setDither(dither: boolean) : void

Sets whether to enable the dithering effect for this pen. Dithering makes colors more realistic.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description                                                     |
| ------ | ------- | ---- | --------------------------------------------------------- |
| dither | boolean | Yes  | Whether to enable dithering. **true** to enable, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setDither(true);
```

## getFillPath<sup>12+</sup>

getFillPath(src: Path, dst: Path): boolean

Obtains the source path outline drawn using this pen and represents it using a destination path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| src | [Path](arkts-apis-graphics-drawing-Path.md) | Yes | Source path object whose outline is to be extracted. |
| dst     | [Path](arkts-apis-graphics-drawing-Path.md)                | Yes | Destination path object used to store the outline result calculated from the src path based on the pen properties. |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Check result. The value **true** means that the source path outline is obtained, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let pathSrc: drawing.Path = new drawing.Path();
let pathDst: drawing.Path = new drawing.Path();
pathSrc.moveTo(0, 0);
pathSrc.lineTo(700, 700);
let value = pen.getFillPath(pathSrc, pathDst);
```

## reset<sup>12+</sup>

reset(): void

Resets this pen to the initial state.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.reset();
```