# Paragraph

```TypeScript
class Paragraph
```

Implements a carrier that stores the text content and style. You can perform operations such as layout and drawing.

Before calling any of the following APIs, you must use [build()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#build) of the [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md) class to create a **Paragraph** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## didExceedMaxLines

```TypeScript
didExceedMaxLines(): boolean
```

Checks whether the number of lines in the paragraph exceeds the maximum.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the number of lines exceeds the maximum, and **false** means the opposite. |

**Examples**

```TypeScript
let didExceed = paragraph.didExceedMaxLines();
```

## forceReuseRasterResult

```TypeScript
forceReuseRasterResult(isForce: boolean): void
```

Sets whether to force reuse of the rasterization result. If this API is not called, the system allows updating the rasterization result by default.

This API is suitable for scenarios where the text content remains unchanged but [paint](#paint) needs to be called multiple times for drawing. By reusing the rasterization result, repeated rasterization calculations can be avoided to improve drawing performance. After this setting is applied, it takes effect the next time [paint](#paint) is called for drawing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isForce | boolean | Yes | Whether to force reuse of the rasterization result. The value **true** means to force reuse of the rasterization result, and **false** means to allow updating the rasterization result. |

**Examples**

```TypeScript
// Index.ets
import { text, drawing } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit'
 
function textFunc(pixelmap: PixelMap) {
  let canvas = new drawing.Canvas(pixelmap);
  let textData = "Hello World";
  let myTextStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  paragraphBuilder.addText(textData);
  let paragraph = paragraphBuilder.build();
  paragraph.layoutSync(200);
  paragraph.forceReuseRasterResult(true);
  paragraph.paint(canvas, 0, 0);
}

@Entry
@Component
struct Index {
  @State pixelmap?: PixelMap = undefined;
  fun: Function = textFunc;
  build() {
    Column() {
      Image(this.pixelmap).width(200).height(200);
      Button("Click").onClick(() => {
        if (this.pixelmap == undefined) {
          const color: ArrayBuffer = new ArrayBuffer(160000);
          let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}
```

## getActualTextRange

```TypeScript
getActualTextRange(lineNumber: number, includeSpaces: boolean): Range
```

Obtains the actually visible text range in the specified line, excluding any overflow ellipsis.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineNumber | number | Yes | Line number of the text range, starting from 0. This API can only be used to obtain the bounds of existing lines. That is, the line number must start from 0, and the maximum line index is the number of text lines – 1. The number of text lines can be obtained via the [getLineCount](#getlinecount) API. |
| includeSpaces | boolean | Yes | Whether spaces are included. The value **true** means that spaces are contained, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| [Range](arkts-arkgraphics2d-text-range-i.md) | Text range obtained. If the line index is invalid, **start** and **end** are both **0**. |

**Examples**

```TypeScript
let rang = paragraph.getActualTextRange(0, true);
```

## getAlphabeticBaseline

```TypeScript
getAlphabeticBaseline(): number
```

Obtains the alphabetic baseline.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Alphabetic baseline, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let alphabeticBaseline = paragraph.getAlphabeticBaseline();
```

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: number, y: number, encoding: drawing.TextEncoding): PositionWithAffinity
```

Obtains the character position information closest to the given coordinates.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate in the text layout area, in physical pixels (px). X offset relative to the top-left corner of the text layout area, with the right direction as positive. Supports floating-point values and accepts negative values, which indicate positions to the left of the text layout area. If the coordinates are beyond the text layout area, the nearest character position is returned. It can be obtained through a touch event or click event. |
| y | number | Yes | Vertical coordinate in the text layout area, in physical pixels (px). Y offset relative to the top-left corner of the text layout area, with the downward direction as positive. Supports floating-point values and accepts negative values, which indicate positions above the text layout area. If the coordinates are beyond the text layout area, the nearest character position is returned. It can be obtained through a touch event or click event. |
| encoding | [drawing.TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | Yes | Text encoding type. Currently, only UTF-8 and UTF-16 encoding types are supported. For UTF-8 encoding, the returned character position indicates the byte offset. For UTF-16 encoding, the returned character position indicates the UTF-16 encoding unit offset. |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkgraphics2d-text-positionwithaffinity-i.md) | Character position. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

**Examples**

```TypeScript
import { drawing, text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("get character position")
        .onClick(() => {
          let encoding: drawing.TextEncoding = drawing.TextEncoding.TEXT_ENCODING_UTF8;
          let textData = "Heน้ำl👨‍👩‍👧lo1️⃣World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle,
            align: text.TextAlign.END,
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          paragraph.layoutSync(200);
          let x = 10;
          let y = 5;
          let position = paragraph.getCharacterPositionAtCoordinate(x, y, encoding);
        })
    }
  }
}
```

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: Range, encoding: drawing.TextEncoding): Array<Range>
```

Obtains the character range corresponding to the specified glyph range.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glyphRange | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Glyph range. |
| encoding | [drawing.TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | Yes | Text encoding type. Currently, only UTF-8 and UTF-16 encoding types are supported. For UTF-8 encoding, the returned character range indicates the byte range. For UTF-16 encoding, the returned character range indicates the UTF-16 encoding unit range. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Range](arkts-arkgraphics2d-text-range-i.md)&gt; | Character range. If the array contains one element, it indicates the character range. If the array contains two elements, the first element indicates the character range, and the second element indicates the actual glyph range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

**Examples**

```TypeScript
import { drawing, text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("get character range")
        .onClick(() => {
          let glyphRange: text.Range = { start: 0, end: 5 };
          let encoding: drawing.TextEncoding = drawing.TextEncoding.TEXT_ENCODING_UTF8;
          let textData = "Heน้ำl👨‍👩‍👧lo1️⃣World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle,
            align: text.TextAlign.END,
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          paragraph.layoutSync(200);
          let ranges = paragraph.getCharacterRangeForGlyphRange(glyphRange, encoding);
        })
    }
  }
}
```

## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity
```

Obtains the position of a glyph closest to the given coordinates.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate, which is a floating-point value in physical pixels (px). |
| y | number | Yes | Vertical coordinate, which is a floating-point value in physical pixels (px). |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkgraphics2d-text-positionwithaffinity-i.md) | Position of the glyph. |

**Examples**

```TypeScript
let positionWithAffinity = paragraph.getGlyphPositionAtCoordinate(0, 0);
```

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(characterRange: Range, encoding: drawing.TextEncoding): Array<Range>
```

Obtains the glyph range corresponding to the specified character range.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| characterRange | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Character range. |
| encoding | [drawing.TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | Yes | Text encoding type. Currently, only UTF-8 and UTF-16 encoding types are supported. For UTF-8 encoding, the returned actual character range indicates the byte range. For UTF-16 encoding, the returned actual character range indicates the UTF-16 encoding unit range. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Range](arkts-arkgraphics2d-text-range-i.md)&gt; | Glyph range. The array contains two elements. The first element indicates the glyph range, and the second element indicates the actual character range. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

**Examples**

```TypeScript
import { drawing, text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("get glyph range")
        .onClick(() => {
          let characterRange: text.Range = { start: 0, end: 5 };
          let encoding: drawing.TextEncoding = drawing.TextEncoding.TEXT_ENCODING_UTF8;
          let textData = "Heน้ำl👨‍👩‍👧lo1️⃣World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle,
            align: text.TextAlign.END,
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          paragraph.layoutSync(200);
          let ranges = paragraph.getGlyphRangeForCharacterRange(characterRange, encoding);
        })
    }
  }
}
```

## getHeight

```TypeScript
getHeight(): number
```

Obtains the total height of the text.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Total height, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let height = paragraph.getHeight();
```

## getIdeographicBaseline

```TypeScript
getIdeographicBaseline(): number
```

Obtains the ideographic baseline.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Baseline position under ideographic characters, a floating point number in physical pixels (px). |

**Examples**

```TypeScript
let ideographicBaseline = paragraph.getIdeographicBaseline();
```

## getLineCount

```TypeScript
getLineCount(): number
```

Obtains the number of text lines.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of text lines. The value is an integer. |

**Examples**

```TypeScript
let lineCount = paragraph.getLineCount();
```

## getLineHeight

```TypeScript
getLineHeight(line: number): number
```

Obtains the height of a given line.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| line | number | Yes | Index of the text line, which is an integer ranging from 0 to [getLineCount](#getlinecount)-1. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Line height, in physical pixels (px). |

**Examples**

```TypeScript
let lineHeight = paragraph.getLineHeight(0);
```

## getLineMetrics

```TypeScript
getLineMetrics(): Array<LineMetrics>
```

Obtains an array of line measurement information.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[LineMetrics](arkts-arkgraphics2d-text-linemetrics-i.md)&gt; | Array of line measurement information. |

**Examples**

```TypeScript
let arrLineMetric =  paragraph.getLineMetrics();
```

<a id="getlinemetrics-1"></a>

## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: number): LineMetrics | undefined
```

Obtains the line measurement information of a line.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineNumber | number | Yes | Number of the line for which metric information is to be queried. Line numbers start from 0, and the maximum line index is the number of text lines minus 1. The number of text lines can be obtained through the [getLineCount](#getlinecount) API. |

**Return value:**

| Type | Description |
| --- | --- |
| [LineMetrics](arkts-arkgraphics2d-text-linemetrics-i.md) &#124; undefined | **LineMetrics** object containing the measurement information if the specified line number is valid and the measurement information exists. If the line number is invalid or the measurement information cannot be obtained, **undefined** is returned. |

**Examples**

```TypeScript
let lineMetrics =  paragraph.getLineMetrics(0);
```

## getLineWidth

```TypeScript
getLineWidth(line: number): number
```

Obtains the width of a given line.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| line | number | Yes | Text line index, which is an integer ranging from 0 to [getLineCount](#getlinecount)-1. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Line width, in physical pixels (px). |

**Examples**

```TypeScript
let lineWidth = paragraph.getLineWidth(0);
```

## getLongestLine

```TypeScript
getLongestLine(): number
```

Obtains the longest line in the text.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Longest line, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let longestLine = paragraph.getLongestLine();
```

## getLongestLineWithIndent

```TypeScript
getLongestLineWithIndent(): number
```

Obtains the width of the longest line, including its indentation, in the text. You are advised to round up the return value. If the text content is empty, **0** is returned.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Width of the longest line, including its indentation. The value is a floating point number, in px. |

**Examples**

```TypeScript
let longestLineWithIndent = paragraph.getLongestLineWithIndent();
```

## getMaxIntrinsicWidth

```TypeScript
getMaxIntrinsicWidth(): number
```

Obtains the maximum intrinsic width of the paragraph.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum intrinsic width, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let maxIntrinsicWidth = paragraph.getMaxIntrinsicWidth();
```

## getMaxWidth

```TypeScript
getMaxWidth(): number
```

Obtains the maximum width of the line in the text.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum line width, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let maxWidth = paragraph.getMaxWidth();
```

## getMinIntrinsicWidth

```TypeScript
getMinIntrinsicWidth(): number
```

Obtains the minimum intrinsic width of the paragraph.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum intrinsic width, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
let minIntrinsicWidth = paragraph.getMinIntrinsicWidth();
```

## getParagraphStyle

```TypeScript
getParagraphStyle(): ParagraphStyle
```

Obtains the style configuration of a paragraph.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md) | Style configuration of the paragraph. <br>The `textStyle.color`, `textStyle.textShadows.color`, `textStyle.backgroundRect.color`, and `textStyle.decoration.color` properties return a 32-bit unsigned integer color value. Example: The return value `4278190080` corresponds to the pure black hexadecimal color value `0xFF000000`, which is equivalent to the [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) object parameters: alpha=255, red=0, green =0, blue=0. The example provides the numberToRGBA conversion method as a reference. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'
import { common2D } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("Click")
        .onClick(() => {
          let textData = "Hello World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          paragraph.layoutSync(200);
          let paragraphStyle = paragraph.getParagraphStyle();
          if (paragraphStyle.textStyle != undefined) {
            console.info("Print fontSize: " + paragraphStyle.textStyle?.fontSize);
            if (paragraphStyle.textStyle?.color != undefined && typeof paragraphStyle.textStyle?.color == 'number') {
              let textColor: common2D.Color = numberToRGBA(paragraphStyle.textStyle?.color);
              console.info(`Print text color ARGB: ${textColor.alpha}, ${textColor.red}, ${textColor.green}, ${textColor.blue}`);
            }
          }
        })
    }
  }
}

function numberToRGBA(colorNum: number): common2D.Color {
  const a = (colorNum >>> 24) & 0xFF;
  const r = (colorNum >>> 16) & 0xFF;
  const g = (colorNum >>> 8) & 0xFF;
  const b = colorNum & 0xFF;
  return { alpha: a, red: r, green: g, blue: b };
}
```

## getProcessState

```TypeScript
getProcessState(): TextProcessState
```

Obtains the text processing status of a paragraph.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [TextProcessState](arkts-arkgraphics2d-text-textprocessstate-e.md) | Text processing status of a paragraph. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("Click")
        .onClick(() => {
          let textData = "Hello World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          let processState = paragraph.getProcessState(); // Now it is INIT
          console.info("Print state: " + processState);
          paragraph.layoutSync(200);
          processState = paragraph.getProcessState(); // Now it is FORMATTED
          console.info("Print state: " + processState);
        })
    }
  }
}
```

## getRectsForPlaceholders

```TypeScript
getRectsForPlaceholders(): Array<TextBox>
```

Obtains the rectangles occupied by all placeholders in the text.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBox](arkts-arkgraphics2d-text-textbox-i.md)&gt; | Array holding the rectangles obtained. |

**Examples**

```TypeScript
let placeholderRects = paragraph.getRectsForPlaceholders();
```

## getRectsForRange

```TypeScript
getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>
```

Obtains the rectangles occupied by the characters in the range of the text under the given rectangle width and height.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Range of the text. |
| widthStyle | [RectWidthStyle](arkts-arkgraphics2d-text-rectwidthstyle-e.md) | Yes | Width of the rectangle. |
| heightStyle | [RectHeightStyle](arkts-arkgraphics2d-text-rectheightstyle-e.md) | Yes | Height of the rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBox](arkts-arkgraphics2d-text-textbox-i.md)&gt; | Array holding the rectangles obtained. |

**Examples**

```TypeScript
let range: text.Range = { start: 0, end: 1};
let rects = paragraph.getRectsForRange(range, text.RectWidthStyle.TIGHT, text.RectHeightStyle.TIGHT);
```

## getTextDisplayState

```TypeScript
getTextDisplayState(): TextDisplayState
```

Obtains the text display status of a paragraph.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [TextDisplayState](arkts-arkgraphics2d-text-textdisplaystate-e.md) | Text display status of a paragraph. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("Click")
        .onClick(() => {
          let textData = "Hello World";
          let myTextStyle: text.TextStyle = {
            color: { alpha: 255, red: 255, green: 0, blue: 0 },
            fontSize: 33,
          };
          let myParagraphStyle: text.ParagraphStyle = {
            textStyle: myTextStyle
          };
          let fontCollection = new text.FontCollection();
          let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
          paragraphBuilder.addText(textData);
          let paragraph = paragraphBuilder.build();
          let displayState = paragraph.getTextDisplayState(); // Now it is UNKNOWN
          console.info("Print state: " + displayState);
          paragraph.layoutSync(200);
          displayState = paragraph.getTextDisplayState(); // Now it is CLIP
          console.info("Print state: " + displayState);
        })
    }
  }
}
```

## getTextLines

```TypeScript
getTextLines(): Array<TextLine>
```

Obtains all the text lines.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextLine](arkts-arkgraphics2d-text-textline-c.md)&gt; | Array of text lines. |

**Examples**

```TypeScript
let lines = paragraph.getTextLines();
```

## getVisibleTextRanges

```TypeScript
getVisibleTextRanges(): Array<Range>
```

Obtains the range of text that is visible on the screen in a paragraph. Excludes text that is not displayed due to truncation by the maximum line count (the maxLines attribute of [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)) or replacement in ellipsis mode ([EllipsisMode](arkts-arkgraphics2d-text-ellipsismode-e.md)).

**NOTE:** 

The returned range depends on the specific truncation of the paragraph (for example, whether the maximum number of lines or ellipsis is set):

| Scenario| Description|  
|---|---|  
| Text is not truncated.| The range includes all typeset text.|
| Only maxLines truncation is set (no ellipsis).| the text from the first line to the end of the maxLines line.|
| EllipsisMode.END| The range is the text before the ellipsis.|
| EllipsisMode.START| The value is the text after the ellipsis.|
| [EllipsisMode.MIDDLE](arkts-arkgraphics2d-text-ellipsismode-e.md) | the text range before and after the ellipsis is returned.|
| [EllipsisMode.MULTILINE_START](arkts-arkgraphics2d-text-ellipsismode-e.md) | the text range before and after the ellipsis is returned.|
| [EllipsisMode.MULTILINE_MIDDLE](arkts-arkgraphics2d-text-ellipsismode-e.md) | the text range before and after the ellipsis is returned.|

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Range](arkts-arkgraphics2d-text-range-i.md)&gt; | Array of the visible text range of a paragraph. The range is the index of the UTF-16 encoding unit. |

**Examples**

```TypeScript
let visibleRanges = paragraph.getVisibleTextRanges();
```

## getWordBoundary

```TypeScript
getWordBoundary(offset: number): Range
```

Obtains the range of the word where the glyph with a given offset is located.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset of the glyph. The value is an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [Range](arkts-arkgraphics2d-text-range-i.md) | Range of the word. |

**Examples**

```TypeScript
let wordRange = paragraph.getWordBoundary(0);
```

## layout

```TypeScript
layout(width: number): Promise<void>
```

Performs layout and calculates the positions of all glyphs. This API uses a promise to return the result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Maximum width of a single line, in units of px. The value is a floating point number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { drawing, text } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit'

let textStyle: text.TextStyle = {
  color: {
    alpha: 255,
    red: 255,
    green: 0,
    blue: 0
  },
  fontSize: 30,
};
let paragraphStyle: text.ParagraphStyle = {
  textStyle: textStyle,
};
let fontCollection: text.FontCollection = new text.FontCollection();
let paragraphBuilder = new text.ParagraphBuilder(paragraphStyle, fontCollection);
// Add a text string.
paragraphBuilder.addText("test");
// Create a paragraph object.
let paragraph = paragraphBuilder.build();

function textFunc(pixelmap: PixelMap) {
  // Construct a canvas using an image object.
  let canvas = new drawing.Canvas(pixelmap);
  // Draw a text string.
  paragraph.paint(canvas, 100, 10);
}

@Entry
@Component
struct Index {
  @State pixelmap?: PixelMap = undefined;
  fun: Function = textFunc;

async prepareLayoutPromise() {
    try {
      await paragraph.layout(200);
      console.info('Succeeded in doing layout');
    } catch (error) {
      let e: Error = error as Error;
      console.error(`Failed to do layout, error: ${JSON.stringify(e)} message: ${e.message}`);
    }
  }

  aboutToAppear() {
    this.prepareLayoutPromise();
  }

  build() {
    Column() {
      Image(this.pixelmap).width(200).height(200);
      Button("layout")
        .width(100)
        .height(50)
        .onClick(() => {
          const color: ArrayBuffer = new ArrayBuffer(160000);
          let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
          if (this.pixelmap == undefined) {
            // Construct an image object.
            this.pixelmap = image.createPixelMapSync(color, opts);
          }
          // Draw the text.
          this.fun(this.pixelmap);
        })
    }
  }
}
```

## layoutSync

```TypeScript
layoutSync(width: number): void
```

Performs layout and calculates the positions of all glyphs.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Maximum width of a single line, in units of px. The value is a floating point number. |

**Examples**

```TypeScript
paragraph.layoutSync(100);
```

## layoutWithConstraints

```TypeScript
layoutWithConstraints(size: TextRectSize): TextLayoutResult
```

Performs layout with the given height and width and calculates the positions of all glyphs.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [TextRectSize](arkts-arkgraphics2d-text-textrectsize-i.md) | Yes | Constrained height and width, in physical pixels (px). |

**Return value:**

| Type | Description |
| --- | --- |
| [TextLayoutResult](arkts-arkgraphics2d-text-textlayoutresult-i.md) | Actual size after layout and character range after typesetting. |

**Examples**

```TypeScript
let size: text.TextRectSize = { width: 200, height: 100 };
let result = paragraph.layoutWithConstraints(size); // Enhanced layoutSync
console.info('Width: ' + result.correctRect.width + ', Height: ' + result.correctRect.height);
for (let i = 0; i < result.fitStrRange.length; ++i) {
  console.info('fitRange: [' + result.fitStrRange[i].start + ', ' + result.fitStrRange[i].end + ']');
}
```

## paint

```TypeScript
paint(canvas: drawing.Canvas, x: number, y: number): void
```

Draws text on the canvas with (x, y) as the upper-left corner. You must call [layout()](#layout) for typesetting before calling this API; otherwise, the text content cannot be displayed correctly.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| canvas | [drawing.Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | Yes | Target canvas. |
| x | number | Yes | Horizontal coordinate of the upper left corner, which is a floating-point value, in physical pixels (px). |
| y | number | Yes | Vertical coordinate of the upper left corner, which is a floating-point value, in physical pixels (px). |

**Examples**

```TypeScript
const color: ArrayBuffer = new ArrayBuffer(160000);
let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
let canvas = new drawing.Canvas(pixelMap);
paragraph.paint(canvas, 0, 0);
```

## paintOnPath

```TypeScript
paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void
```

Draws text along a path on the canvas. You must call [layout()](#layout) for typesetting before calling this API; otherwise, the text content cannot be displayed correctly.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| canvas | [drawing.Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | Yes | Target canvas. |
| path | [drawing.Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | Path along which the text is drawn. |
| hOffset | number | Yes | Offset along the path direction. Positive values extend forward from the path start point, and negative values extend backward. Unit: physical pixels (px). |
| vOffset | number | Yes | Offset along the vertical direction of the path. Positive values extend to the right along the path, and negative values extend to the left. Unit: physical pixels (px). |

**Examples**

```TypeScript
const color: ArrayBuffer = new ArrayBuffer(160000);
let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
let canvas = new drawing.Canvas(pixelMap);
let path = new drawing.Path();
path.arcTo(20, 20, 180, 180, 180, 90);
paragraph.paintOnPath(canvas, path, 0, 0);
```

## updateColor

```TypeScript
updateColor(color: common2D.Color): void
```

Updates the color of the entire text span. This API call also updates the decoration color if it hasn't been set yet.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | Updated font color. |

**Examples**

```TypeScript
paragraph.updateColor({ alpha: 255, red: 255, green: 0, blue: 0 });
```

## updateDecoration

```TypeScript
updateDecoration(decoration: Decoration): void
```

Updates the decoration line of the entire text span.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decoration | [Decoration](arkts-arkgraphics2d-text-decoration-i.md) | Yes | Updated decoration line. |

**Examples**

```TypeScript
paragraph.updateDecoration({
  textDecoration: text.TextDecorationType.OVERLINE,
  color: { alpha: 255, red: 255, green: 0, blue: 0 },
  decorationStyle: text.TextDecorationStyle.WAVY,
  decorationThicknessScale: 2.0,
});
```
