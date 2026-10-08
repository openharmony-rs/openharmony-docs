# Class (Font)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d66ce495242bdf35b08a89dbf23cdf3929953623 translatedAt=2026-08-24T07:56:22.571Z pushedAt=2026-08-25T06:30:45.568Z -->

The Font class describes the attributes used for font drawing (such as size, typeface, weight, skew, and scale), and supports capabilities such as text measurement, glyph conversion, path outline retrieval, and theme font following.

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

## isSubpixel<sup>12+</sup>

isSubpixel(): boolean

Obtains whether the font uses subpixel rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| boolean | Return Font whether to use subpixel rendering, true indicates use, false indicates not use. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
font.enableSubpixel(true)
console.info("values=" + font.isSubpixel());
```

## isLinearMetrics<sup>12+</sup>

isLinearMetrics(): boolean

Checks whether linear scaling is used for this font.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| boolean | Check result. The value **true** means that linear scaling is used, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
font.enableLinearMetrics(true);
console.info("values=" + font.isLinearMetrics());
```

## getSkewX<sup>12+</sup>

getSkewX(): number

Obtains the skew ratio of the font in the x-axis direction.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| number | Return Font skew ratio in the x-axis direction. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
font.setSkewX(-1);
console.info("values=" + font.getSkewX());
```

## isEmbolden<sup>12+</sup>

isEmbolden(): boolean

Checks whether the bold effect is set for this font.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| boolean  | Check result. The value **true** means that the bold effect is set, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
font.enableEmbolden(true);
console.info("values=" + font.isEmbolden());
```

## getScaleX<sup>12+</sup>

getScaleX(): number

Obtains the horizontal scale ratio of this font.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| number  | Horizontal scale ratio.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
font.setScaleX(2);
console.info("values=" + font.getScaleX());
```

## getHinting<sup>12+</sup>

getHinting(): FontHinting

Obtains the font hinting effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| [FontHinting](arkts-apis-graphics-drawing-e.md#fonthinting12)  | Font hinting effect.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
console.info("values=" + font.getHinting());
```

## getEdging<sup>12+</sup>

getEdging(): FontEdging

Obtains the font edging effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| [FontEdging](arkts-apis-graphics-drawing-e.md#fontedging12)  | Font edging effect.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
console.info("values=" + font.getEdging());
```

## enableSubpixel

enableSubpixel(isSubpixel: boolean): void

Enables subpixel font rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type   | Mandatory| Description                                                        |
| ---------- | ------- | ---- | ------------------------------------------------------------ |
| isSubpixel | boolean | Yes  | Whether to enable subpixel font rendering. **true** to enable, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.enableSubpixel(true);
```

## enableEmbolden

enableEmbolden(isEmbolden: boolean): void

Enables emboldened fonts.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type   | Mandatory| Description                                                 |
| ---------- | ------- | ---- | ----------------------------------------------------- |
| isEmbolden | boolean | Yes  | Whether to enable emboldened fonts. **true** to enable, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.enableEmbolden(true);
```

## enableLinearMetrics

enableLinearMetrics(isLinearMetrics: boolean): void

Enables linear font scaling.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name         | Type   | Mandatory| Description                                                       |
| --------------- | ------- | ---- | ----------------------------------------------------------- |
| isLinearMetrics | boolean | Yes  | Whether to enable linear font scaling. **true** to enable, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.enableLinearMetrics(true);
```

## setSize

setSize(textSize: number): void

Sets the font size.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type  | Mandatory| Description            |
| -------- | ------ | ---- | ---------------- |
| textSize | number | Yes | Font size. This parameter is a floating-point number. If it is a negative number, it is set to 0. If it is 0, the drawn text is not displayed. The unit is physical pixel px. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.setSize(5);
```

## getSize

getSize(): number

Obtains the font size.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| number | Returns the font size, a floating-point number. The unit is physical pixel px. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.setSize(5);
let fontSize = font.getSize();
```

## setTypeface

setTypeface(typeface: Typeface): void

Sets the typeface style (including attributes such as font name, weight, and italic) for the font.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                 | Mandatory| Description  |
| -------- | --------------------- | ---- | ------ |
| typeface | [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Yes  | Typeface style (including attributes such as font name, weight, and italic).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
```

## getTypeface

getTypeface(): Typeface

Obtains the typeface.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                 | Description  |
| --------------------- | ------ |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Font.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
let typeface = font.getTypeface();
```

## getMetrics

getMetrics(): FontMetrics

Obtains the font metrics of the typeface.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description             |
| --------------------------- | ----------------- |
| [FontMetrics](arkts-apis-graphics-drawing-i.md#fontmetrics) | The metrics attribute object associated with the font. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
let metrics = font.getMetrics();
```

## measureText

measureText(text: string, encoding: TextEncoding): number

Measures the text width.

> **NOTE**
>
> This API is used to measure the text width of the original string. To measure the text width after typesetting, call [measure.measureText](../apis-arkui/arkts-apis-uicontext-measureutils.md#measuretext12).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| text     | string                        | Yes   | Text content to be measured, which will be parsed according to the encoding format specified by encoding. |
| encoding | [TextEncoding](arkts-apis-graphics-drawing-e.md#textencoding) | Yes   | Encoding format of the text. |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| number | Text width, in units of physical pixel px. The value is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.measureText("drawing", drawing.TextEncoding.TEXT_ENCODING_UTF8);
```

## measureSingleCharacter<sup>12+</sup>

measureSingleCharacter(text: string): number

Measures the width of a single character. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type               | Mandatory| Description       |
| ------ | ------------------- | ---- | ----------- |
| text   | string | Yes  | Single character to measure. The length of the string must be **1**. |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| number | Character width, a floating-point number. The unit is physical pixel px. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const font = new drawing.Font();
    font.setSize(20);
    let width = font.measureSingleCharacter("H");
  }
}
```

## measureSingleCharacterWithFeatures<sup>20+</sup>

measureSingleCharacterWithFeatures(text: string, features: Array\<FontFeature\>): number

Measures the width of a single character with font features. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type               | Mandatory| Description       |
| ------ | ------------------- | ---- | ----------- |
| text | string | Yes| Pointer to the single character to measure. The length of the string must be **1**.|
| features | Array\<[FontFeature](arkts-apis-graphics-drawing-i.md#fontfeature20)\> | Yes | Array of font feature objects. When this parameter is an empty array, the preset font features in the TTF (TrueType Font) file are used. |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| number | Character width, in units of physical pixel px. The value is a floating-point number. |

**Error codes**

For details about the following error code, see [Drawing and Display Error Codes](../apis-arkgraphics2d/errorcode-drawing.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 25900001 | Parameter error. Possible causes: Incorrect parameter range. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const font = new drawing.Font();
    font.setSize(20);
    let fontFeatures : Array<drawing.FontFeature> = [];
    fontFeatures.push({name: 'calt', value: 0});
    let width = font.measureSingleCharacterWithFeatures("H", fontFeatures);
  }
}
```

## setScaleX<sup>12+</sup>

setScaleX(scaleX: number): void

Sets the scale ratio of the font in the x-axis direction.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| scaleX     | number                      | Yes   | Scale ratio of the font on the x-axis. This parameter is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

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
    canvas.attachPen(pen);
    let font = new drawing.Font();
    font.setSize(100);
    font.setScaleX(2);
    const textBlob = drawing.TextBlob.makeFromString("hello", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 200, 200);
  }
}
```

## setSkewX<sup>12+</sup>

setSkewX(skewX: number): void

Sets the skew ratio of the font in the x-axis direction.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| skewX     | number                      | Yes   | Skew ratio of the font in the x-axis direction. A positive value indicates a leftward skew, and a negative value indicates a rightward skew. This parameter is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

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
    canvas.attachPen(pen);
    let font = new drawing.Font();
    font.setSize(100);
    font.setSkewX(1);
    const textBlob = drawing.TextBlob.makeFromString("hello", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 200, 200);
  }
}
```

## setEdging<sup>12+</sup>

setEdging(edging: FontEdging): void

Sets a font edging effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| edging | [FontEdging](arkts-apis-graphics-drawing-e.md#fontedging12) | Yes  | Font edging effect.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.setEdging(drawing.FontEdging.SUBPIXEL_ANTI_ALIAS);
```

## setHinting<sup>12+</sup>

setHinting(hinting: FontHinting): void

Sets a font hinting effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| hinting | [FontHinting](arkts-apis-graphics-drawing-e.md#fonthinting12) | Yes  | Font hinting effect.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
font.setHinting(drawing.FontHinting.FULL);
```

## countText<sup>12+</sup>

countText(text: string): number

Obtains the number of glyphs represented by text.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| text     | string                        | Yes   | Text content to be counted. |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| number | Number of glyphs represented by the text. The value is an integer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font = new drawing.Font();
let resultNumber: number = font.countText('ABCDE');
console.info("count text number: " + resultNumber);
```

## setBaselineSnap<sup>12+</sup>

setBaselineSnap(isBaselineSnap: boolean): void

Sets whether to request that baselines be snapped to pixels when the current canvas matrix is axis aligned.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name         | Type   | Mandatory| Description                                      |
| --------------- | ------- | ---- | ---------------------------------------- |
| isBaselineSnap | boolean | Yes | Indicates whether the font baseline is aligned with pixels. The value true indicates alignment, and false indicates no alignment. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setBaselineSnap(true);
console.info("drawing font isBaselineSnap: " + font.isBaselineSnap());
```

## isBaselineSnap<sup>12+</sup>

isBaselineSnap(): boolean

Checks whether baselines are requested to be snapped to pixels when the current canvas matrix is axis aligned.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| boolean | Returns whether the font baseline is aligned with pixels. true indicates aligned, false indicates not aligned. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
font.setBaselineSnap(true);
console.info("drawing font isBaselineSnap: " + font.isBaselineSnap());
```

## setEmbeddedBitmaps<sup>12+</sup>

setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void

Sets whether to use the embedded bitmap glyphs in the font file for rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type  | Mandatory| Description            |
| -------- | ------ | ---- | ---------------- |
| isEmbeddedBitmaps | boolean | Yes | Whether to use the embedded bitmap glyphs in the font file for rendering. The value true indicates to use the embedded bitmap glyphs, and false indicates not to convert them into bitmaps for processing. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
font.setEmbeddedBitmaps(false);
console.info("draw isEmbeddedBitmaps: " + font.isEmbeddedBitmaps());
```

## isEmbeddedBitmaps<sup>12+</sup>

isEmbeddedBitmaps(): boolean

Gets the result of whether the font uses embedded bitmaps for rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| boolean | Return Font whether embedded bitmap rendering is used. true indicates use of embedded bitmap glyphs, and false indicates not converting to bitmap processing. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
font.setEmbeddedBitmaps(true);
console.info("draw isEmbeddedBitmaps: " + font.isEmbeddedBitmaps());
```

## setForceAutoHinting<sup>12+</sup>

setForceAutoHinting(isForceAutoHinting: boolean): void

Sets whether to automatically adjust the font outline to optimize rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type  | Mandatory| Description            |
| -------- | ------ | ---- | ---------------- |
| isForceAutoHinting | boolean | Yes | Whether to automatically adjust the font outline to optimize rendering. The value true means to automatically adjust, and false means not to automatically adjust. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
font.setForceAutoHinting(false);
console.info("drawing isForceAutoHinting:  " + font.isForceAutoHinting());
```

## isForceAutoHinting<sup>12+</sup>

isForceAutoHinting(): boolean

Gets the result of whether the font automatically adjusts the outline to optimize rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| boolean | Return the result of whether the font automatically adjusts the outline to optimize rendering effect. true indicates automatic adjustment, and false indicates no automatic adjustment. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setTypeface(new drawing.Typeface());
font.setForceAutoHinting(false);
console.info("drawing isForceAutoHinting:  " + font.isForceAutoHinting());
```

## getWidths<sup>12+</sup>

getWidths(glyphs: Array\<number>): Array\<number>

Obtains the width of each glyph in an array.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                 | Mandatory| Description  |
| -------- | --------------------- | ---- | ------ |
| glyphs | Array\<number> | Yes  | Glyph array, which can be generated by [textToGlyphs](#texttoglyphs12).|

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| Array\<number> | Array of glyph widths, as floating-point numbers. The unit is physical pixel px. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
let text: string = 'hello world';
let glyphs: number[] = font.textToGlyphs(text);
let fontWidths: Array<number> = font.getWidths(glyphs);
for (let index = 0; index < fontWidths.length; index++) {
  console.info("get fontWidths[", index, "]:", fontWidths[index]);
}
```

## textToGlyphs<sup>12+</sup>

textToGlyphs(text: string, glyphCount?: number): Array\<number>

Converts text into glyph indexes.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                         | Mandatory| Description      |
| -------- | ----------------------------- | ---- | ---------- |
| text | string | Yes | Text string to be converted to glyph indices. |
| glyphCount | number | No | Number of characters represented by the text. This parameter is an integer. When passed in, it must be equal to the value obtained by [countText](#counttext12). If not passed in, it defaults to the number of characters represented by text. |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| Array\<number> | Array that holds the glyph indexes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
let text : string = 'hello world';
let glyphs : number[] = font.textToGlyphs(text);
console.info("drawing text toglyphs OnTestFunction num =  " + glyphs.length );
```

## getBounds<sup>18+</sup>

getBounds(glyphs: Array\<number>): Array\<common2D.Rect>

Obtains the rectangular bounding box of each glyph in an array.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                 | Mandatory| Description  |
| -------- | --------------------- | ---- | ------ |
| glyphs | Array\<number> | Yes  | Glyph array, which can be generated by [textToGlyphs](#texttoglyphs12).|

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| Array\<[common2D.Rect](js-apis-graphics-common2D.md#rect)> | Array that holds the rectangular bounding boxes.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let font: drawing.Font = new drawing.Font();
let text: string = 'hello world';
let glyphs: number[] = font.textToGlyphs(text);
let fontBounds: Array<common2D.Rect> = font.getBounds(glyphs);
for (let index = 0; index < fontBounds.length; index++) {
  console.info("get fontWidths[", index, "] left:", fontBounds[index].left, " top:", fontBounds[index].top,
    " right:", fontBounds[index].right, " bottom:", fontBounds[index].bottom);
}
```

## getTextPath<sup>18+</sup>

getTextPath(text: string, byteLength: number, x: number, y: number): Path

Obtains the path outline of the text.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name   | Type                                              | Mandatory| Description                   |
| ------   | ------------------------------------------------   | ---- | ---------------------- |
|   text   |    string                                          | Yes   | Text string encoded in UTF-8 format.|
|byteLength|    number                                          | Yes   | Byte length of the text path to be obtained. The text path is obtained based on the minimum value between the passed byte length and the actual byte size of the text.|
|    x     |    number                                          | Yes   | X coordinate of the text in the drawing area, with the origin as the start position. The unit is physical pixel px.|
|    y     |    number                                          | Yes   | Y coordinate of the text in the drawing area, with the origin as the start position. The unit is physical pixel px.|

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| [Path](arkts-apis-graphics-drawing-Path.md) | Outline path of the text.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
import { buffer } from '@kit.ArkTS';
import { RenderNode } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(50);
    let myString: string = "Hello";
    let length: number = buffer.from(myString).length;
    let path = font.getTextPath(myString, length, 0, 100);
    canvas.drawPath(path);
  }
}
```

## getTextPathWithFallback

getTextPathWithFallback(text: string, byteLength: number, x: number, y: number): Path

Obtains the outline path of text, with font fallback support.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                 | Mandatory| Description  |
| ------ | --------------------- | ---- | ------ |
|   text   |    string                                          | Yes  | Text string encoded in UTF-8 format.|
|byteLength|    number                                          | Yes  | Byte length of the text path to obtain. The text path is obtained based on the minimum value between the passed byte length and the actual text byte size.|
|    x     |    number                                          | Yes  | X coordinate of the text in the drawing area, with the origin as the start position. The unit is physical pixel px.|
|    y     |    number                                          | Yes  | Y coordinate of the text in the drawing area, with the origin as the start position. The unit is physical pixel px.|

**Return value**

| Type  | Description            |
| ------ | ---------------- |
| [Path](arkts-apis-graphics-drawing-Path.md) | Outline path of the obtained text. Returns undefined if the path object fails to be created. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
import { buffer } from '@kit.ArkTS';
import { RenderNode, DrawContext } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(50);
    let myString: string = "Hello";
    let length = buffer.from(myString).length;
    let path = font.getTextPathWithFallback(myString, length, 0, 100);
    if (path == undefined) {
      return;
    }
    canvas.drawPath(path);
  }
}
```

## createPathForGlyph<sup>18+</sup>

createPathForGlyph(index: number): Path

Obtains the outline path of a glyph.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                 | Mandatory| Description  |
| -------- | --------------------- | ---- | ------ |
| index | number | Yes | Glyph index, which can be generated by [textToGlyphs](#texttoglyphs12). |

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| [Path](arkts-apis-graphics-drawing-Path.md) | Outline path of the glyph.|

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(50);
    let text: string = 'Hello';
    let glyphs: number[] = font.textToGlyphs(text);
    for (let index = 0; index < glyphs.length; index++) {
      let path: drawing.Path = font.createPathForGlyph(glyphs[index]);
      canvas.drawPath(path);
    }
  }
}
```

## setThemeFontFollowed<sup>15+</sup>

setThemeFontFollowed(followed: boolean): void

Sets whether to follow the theme font. When **followed** is set to **true**, the theme font is used if it is enabled by the system and no typeface is set.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type  | Mandatory| Description            |
| -------- | ------ | ---- | ---------------- |
| followed | boolean | Yes  | Whether to follow the theme font. The value **true** means to follow the theme font, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setThemeFontFollowed(true);
console.info("font is theme font followed: " + font.isThemeFontFollowed());
```

## isThemeFontFollowed()<sup>15+</sup>

isThemeFontFollowed(): boolean

Checks whether the font follows the theme font. By default, the font follows the theme font.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description            |
| ------ | ---------------- |
| boolean | Check result. The value **true** means that the theme font is followed, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let font : drawing.Font = new drawing.Font();
font.setThemeFontFollowed(true);
console.info("font is theme font followed: " + font.isThemeFontFollowed());
```