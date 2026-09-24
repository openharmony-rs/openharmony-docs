# TextBlob

```TypeScript
class TextBlob
```

Defines a block consisting of one or more characters with the same font.

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

## bounds

```TypeScript
bounds(): common2D.Rect
```

Obtains the rectangular bounding box of the text blob.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Rectangular bounding box. |

**Examples**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const font = new drawing.Font();
font.setSize(20);
const textBlob = drawing.TextBlob.makeFromString("drawing", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
let bounds = textBlob.bounds();
```

## makeFromPosText

```TypeScript
static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob
```

Creates a **TextBlob** object from the text. The coordinates of each font in the **TextBlob** object are determined by the coordinate information in the **points** array.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Content to be used for drawing the text blob. |
| len | number | Yes | Number of glyphs, which is an integer obtained from [countText](arkts-arkgraphics2d-drawing-font-c.md#counttext). |
| points | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)[] | Yes | Array of points, which are used to specify the coordinates of each font. The array length must be the same as the value of **len**. |
| font | [Font](arkts-arkgraphics2d-drawing-font-c.md) | Yes | **Font** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | **TextBlob** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing, common2D } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let text : string = 'makeFromPosText';
    let font : drawing.Font = new drawing.Font();
    font.setSize(100);
    let length = font.countText(text);
    let points : common2D.Point[] = [];
    for (let i = 0; i !== length; ++i) {
      points.push({ x: i * 35, y: i * 35 });
    }
    let textblob : drawing.TextBlob = drawing.TextBlob.makeFromPosText(text, points.length, points, font);
    canvas.drawTextBlob(textblob, 100, 100);
  }
}
```

## makeFromPosTextWithFallback

```TypeScript
static makeFromPosTextWithFallback(
      text: string, len: number, points: common2D.Point[], font: Font): Array<TextBlob>
```

Creates a sequence of TextBlob objects from text with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. If no fallback typeface is found, the typeface of the current font is still used. One text blob is created per run of consecutive codepoints that share the same typeface. The coordinates of each font in the TextBlob object are determined by the coordinate information in the points array.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Content to be used for drawing the text blob. |
| len | number | Yes | Number of glyphs, which is an integer obtained from [countText](arkts-arkgraphics2d-drawing-font-c.md#counttext). |
| points | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)[] | Yes | Array of points, which are used to specify the coordinates of each font. The array length must be the same as the value of len. |
| font | [Font](arkts-arkgraphics2d-drawing-font-c.md) | Yes | Font object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md)&gt; | An array of TextBlob objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

## makeFromRunBuffer

```TypeScript
static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob
```

Creates a **TextBlob** object based on the **RunBuffer** information.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pos | Array&lt;[TextBlobRunBuffer](arkts-arkgraphics2d-drawing-textblobrunbuffer-i.md)&gt; | Yes | **TextBlobRunBuffer** array. |
| font | [Font](arkts-arkgraphics2d-drawing-font-c.md) | Yes | **Font** object. |
| bounds | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | No | Bounding box. If this parameter is not set, there is no bounding box. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | **TextBlob** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const font = new drawing.Font();
    font.setSize(20);
    let runBuffer : Array<drawing.TextBlobRunBuffer> = [
      { glyph: 65, positionX: 0, positionY: 0 },
      { glyph: 227, positionX: 14.9, positionY: 0 },
      { glyph: 283, positionX: 25.84, positionY: 0 },
      { glyph: 283, positionX: 30.62, positionY: 0 },
      { glyph: 299, positionX: 35.4, positionY: 0 }
    ];
    const textBlob = drawing.TextBlob.makeFromRunBuffer(runBuffer, font, null);
    const brush = new drawing.Brush();
    brush.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 20, 20);
    canvas.detachBrush();
  }
}
```

## makeFromString

```TypeScript
static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob
```

Converts a value of the string type into a **TextBlob** object.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Content to be used for drawing the text blob. |
| font | [Font](arkts-arkgraphics2d-drawing-font-c.md) | Yes | **Font** object. |
| encoding | [TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | No | Encoding type. The default value is **TEXT_ENCODING_UTF8**. Currently, only **TEXT_ENCODING_UTF8** takes effect, and other encoding types are treated as **TEXT_ENCODING_UTF8**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | **TextBlob** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const brush = new drawing.Brush();
    brush.setColor({ alpha: 255, red: 255, green: 0, blue: 0 });
    const font = new drawing.Font();
    font.setSize(20);
    const textBlob = drawing.TextBlob.makeFromString("drawing", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 20, 20);
    canvas.detachBrush();
  }
}
```

## makeFromStringWithFallback

```TypeScript
static makeFromStringWithFallback(text: string, font: Font): Array<TextBlob>
```

Creates a sequence of TextBlob objects from a string with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. If no fallback typeface is found, the typeface of the current font is still used. One text blob is created per run of consecutive codepoints that share the same typeface.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Content to be used for drawing the text blob. |
| font | [Font](arkts-arkgraphics2d-drawing-font-c.md) | Yes | Font object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md)&gt; | An array of TextBlob objects. |

## uniqueID

```TypeScript
uniqueID(): number
```

Obtains the unique, non-zero identifier of this **TextBlob** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique, non-zero identifier of this **TextBlob** object. |

**Examples**

```TypeScript
import { drawing } from "@kit.ArkGraphics2D";

let text : string = 'TextBlobUniqueId';
let font : drawing.Font = new drawing.Font();
font.setSize(100);
let textBlob = drawing.TextBlob.makeFromString(text, font, 0);
let id = textBlob.uniqueID();
console.info('uniqueID---------------' + id);
```
