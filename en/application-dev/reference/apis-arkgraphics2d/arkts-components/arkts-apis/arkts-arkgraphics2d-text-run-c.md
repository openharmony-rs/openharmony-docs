# Run

```TypeScript
class Run
```

Represents a text typesetting unit, which is a continuous text segment with the same style attributes. Run is obtained through the [getGlyphRuns()](arkts-arkgraphics2d-text-textline-c.md#getglyphruns) API of the [TextLine](arkts-arkgraphics2d-text-textline-c.md) class.

Before calling any of the following APIs, you must use [getGlyphRuns()](arkts-arkgraphics2d-text-textline-c.md#getglyphruns) of the [TextLine](arkts-arkgraphics2d-text-textline-c.md) class to create a **Run** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## getAdvances

```TypeScript
getAdvances(range: Range): Array<common2D.Point>
```

Obtains the glyph width array of each glyph within the specified range of the run.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Range of the glyph position to be obtained. **range.start** indicates the start position of the range, and **range.end** indicates the range length. If the length is **0**, the range starts from **range.start** and ends at the end of the run. If **range.end** or **range.start** is set to a negative value, **null**, or **undefined**, **undefined** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Returns the glyph width array of each glyph in the run unit relative to the horizontal direction. In [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md), the x value represents the glyph width of each glyph relative to the horizontal direction, in physical pixels (px). The y value is a reserved field and returns **0** by default. |

**Examples**

```TypeScript
let advancesRange = runs[0].getAdvances({start:1, end:2}); // Obtain the widths of glyphs in the range starting from position 1, with a length of 2.
advancesRange = runs[0].getAdvances({start:-1, end:2}); // -1 is an invalid value, and undefined is returned.
advancesRange = runs[0].getAdvances({start:0, end:-10}); // -10 is an invalid value, and undefined is returned.
let advancesNull = runs[0].getAdvances(null); // null is an invalid value, and undefined is returned.
```

## getFont

```TypeScript
getFont(): drawing.Font
```

Obtains the **Font** object of this run.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [drawing.Font](arkts-arkgraphics2d-drawing-font-c.md) | **Font** object of this run. |

**Examples**

```TypeScript
let font = runs[0].getFont();
```

## getGlyphCount

```TypeScript
getGlyphCount(): number
```

Obtains the number of glyphs in this run.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of glyphs. The value is an integer. |

**Examples**

```TypeScript
let glyphs = runs[0].getGlyphCount();
```

## getGlyphs

```TypeScript
getGlyphs(): Array<number>
```

Obtains the index of each glyph in this run.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array holding the index of each glyph in the run. |

**Examples**

```TypeScript
let glyph = runs[0].getGlyphs();
```

<a id="getglyphs-1"></a>

## getGlyphs

```TypeScript
getGlyphs(range: Range): Array<number>
```

Obtains the index of each glyph in the specified range of this run.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Range of glyph indices to obtain. **range.start** indicates the starting position of the range, and **range.end** indicates the length of the range. When **range.end** is **0**, glyphs are fetched from **range.start** to the end of the rendered block. If **range.end** or **range.start** is set to a negative value, **null**, or **undefined**, **undefined** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array holding the index of each glyph in the run. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let glyphs = runs[0].getGlyphs(); // Obtain the index of all glyphs of the run.
  let glyphsRange = runs[0].getGlyphs({start:1, end:2}); // Obtain the glyph indices within the range starting at position 1 with a length of 2 from the rendered block.
  glyphsRange = runs[0].getGlyphs({start:-1, end:2}); // -1 is an invalid value, and undefined is returned.
  glyphsRange = runs[0].getGlyphs({start:0, end:-10}); // -10 is an invalid value, and undefined is returned.
  let glyphsNull = runs[0].getGlyphs(null); // null is an invalid value, and undefined is returned.
  let glyphsUndefined = runs[0].getGlyphs(undefined); // undefined is an invalid value, and undefined is returned.
}

@Entry
@Component
struct Index {
  fun: Function = textFunc;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}
```

## getImageBounds

```TypeScript
getImageBounds(): common2D.Rect
```

Obtains the image boundaries of the typographic unit. Equivalent to visual boundaries, these boundaries are associated with the typographic font, font size, and characters. For example, for the string " a b " (which has a space before "a" and a space after "b"), only "a b" is visible to users, and therefore the image boundaries do not include these spaces at the beginning and end of the line.

> **NOTE:** 
> 
> The figure shows the image boundaries for the string " a b ".
> 
> ![ImageBounds.png](../../../reference/apis-arkgraphics2d/figures/ImageBounds.png)
> 
> The figure shows the image boundaries for the string "j" or "E".
> 
> ![ImageBounds-Character.png](../../../reference/apis-arkgraphics2d/figures/ImageBounds-Character.png)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Image boundary of the layout unit, in physical pixels (px). |

**Examples**

```TypeScript
let bounds = runs[0].getImageBounds();
```

## getOffsets

```TypeScript
getOffsets(): Array<common2D.Point>
```

Obtains the offset of each glyph in this run relative to its index.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Array holding the offset of each glyph in the run relative to its index. |

**Examples**

```TypeScript
let offsets = runs[0].getOffsets();
```

## getPositions

```TypeScript
getPositions(): Array<common2D.Point>
```

Obtains the position of each glyph relative to the respective line in this run.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Array holding the position of each glyph relative to the respective line in the run. |

**Examples**

```TypeScript
let positions = runs[0].getPositions();
```

<a id="getpositions-1"></a>

## getPositions

```TypeScript
getPositions(range: Range): Array<common2D.Point>
```

Obtains the position array of each glyph relative to the respective line within the specified range of this run.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-arkgraphics2d-text-range-i.md) | Yes | Range of the glyphs, where **range.start** indicates the start position of the range, and **range.end** indicates the length of the range. If the length is **0**, the range is from **range.start** to the end of the run. If **range.end** or **range.start** is set to a negative value, **null**, or **undefined**, **undefined** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Array holding the position of each glyph relative to the respective line in the run. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let positions = runs[0].getPositions(); // Obtain the positions of all glyphs in the run.
  let positionsRange = runs[0].getPositions({start:1, end:2}); // Obtain the positions of glyphs in the range starting from position 1, with a length of 2.
  positionsRange = runs[0].getPositions({start:-1, end:2}); // -1 is an invalid value, and undefined is returned.
  positionsRange = runs[0].getPositions({start:0, end:-10}); // -10 is an invalid value, and undefined is returned.
  let positionsNull = runs[0].getPositions(null); // null is an invalid value, and undefined is returned.
  let positionsUndefined = runs[0].getPositions(undefined); // undefined is an invalid value, and undefined is returned.
}

@Entry
@Component
struct Index {
  fun: Function = textFunc;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}
```

## getStringIndices

```TypeScript
getStringIndices(range?: Range): Array<number>
```

Obtains an array of character indices for glyphs within a specified range of this run, where the indices are offsets relative to the entire paragraph.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [Range](arkts-arkgraphics2d-text-range-i.md) | No | Range of character indices to be obtained. **range.start** indicates the starting position of the range, and **range.end** indicates the range length. If the length is 0, characters are retrieved from **range.start** to the end of the rendered block. If **range.end** or **range.start** is set to a negative value, **null**, or **undefined**, **undefined** is returned. If this parameter is not passed, the entire run is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array of character indices. |

**Examples**

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let indices = runs[0].getStringIndices(); // Obtain the indices of all characters in the run.
  let indicesRange = runs[0].getStringIndices({start:1, end:2}); // Obtain the indices of characters in the range starting from position 1, with a length of 2.
  indicesRange = runs[0].getStringIndices({start:-1, end:2}); // -1 is an invalid value, and undefined is returned.
  indicesRange = runs[0].getStringIndices({start:0, end:-10}); // -10 is an invalid value, and undefined is returned.
  let indicesNull = runs[0].getStringIndices(null); // null is an invalid value, and undefined is returned.
  let indicesUndefined = runs[0].getStringIndices(undefined); // undefined is an invalid value, and undefined is returned.
}

@Entry
@Component
struct Index {
  fun: Function = textFunc;
  build() {
    Column() {
      Button().onClick(() => {
        this.fun();
      })
    }
  }
}
```

## getStringRange

```TypeScript
getStringRange(): Range
```

Obtains the range of glyphs generated by this run.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [Range](arkts-arkgraphics2d-text-range-i.md) | Range of the glyphs, where **start** indicates the start position of the range, which is the index relative to the entire paragraph, and **end** indicates the length of the range. |

**Examples**

```TypeScript
let runStringRange = runs[0].getStringRange();
let location = runStringRange.start;
let length = runStringRange.end;
```

## getTextDirection

```TypeScript
getTextDirection(): TextDirection
```

Obtains the text direction of the run.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [TextDirection](arkts-arkgraphics2d-text-textdirection-e.md) | Obtains the text direction of the run. |

**Examples**

```TypeScript
let textDirection = runs[0].getTextDirection();
```

## getTextStyle

```TypeScript
getTextStyle(): TextStyle
```

Obtains the text style of this typesetting unit.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) | Text style of this typesetting unit. <br>**Note:** <br>1. The `textStyle.color`, `textStyle.textShadows.color`, `textStyle.backgroundRect.color`, and `textStyle.decoration.color` attributes: return a 32-bit unsigned integer color value. Example: The return value `4278190080` corresponds to the solid black hexadecimal color value `0xFF000000`, which is equivalent to the [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) object parameters: alpha=255, red=0, green=0, blue=0. The example provides a numberToRGBA conversion method for reference. <br>2. `textStyle.ellipsis` and `textStyle.ellipsisMode` are paragraph attributes and cannot be obtained through this API. Use [getParagraphStyle()](arkts-arkgraphics2d-text-paragraph-c.md#getparagraphstyle) instead. |

**Examples**

```TypeScript
// Index.ets
import { text } from "@kit.ArkGraphics2D"
import { common2D } from '@kit.ArkGraphics2D'
import { JSON } from "@kit.ArkTS";

function textFunc() {
  let textStyle: text.TextStyle = {
    color: { alpha: 255, red: 255, green: 0, blue: 0 },
    fontSize: 33,
  };
  let paragraphStyle: text.ParagraphStyle = {
    textStyle: textStyle,
    align: text.TextAlign.END,
  };
  let fontCollection = new text.FontCollection();
  let paragraphBuilder = new text.ParagraphBuilder(paragraphStyle, fontCollection);
  paragraphBuilder.addText("Hello World");
  let paragraph = paragraphBuilder.build();
  paragraph.layoutSync(50);
  let lines = paragraph.getTextLines();
  for (let i = 0; i < lines.length; i++) {
    const line = lines[i];
    let runs = line.getGlyphRuns();
    for (let j = 0; j < runs.length; j++) {
      const run = runs[j];
      const runStyle = run.getTextStyle();
      console.info(`print line [${i}] run [${j}] textStyle: ${JSON.stringify(runStyle)}`);
      if (runStyle?.color != undefined && typeof runStyle?.color == 'number') {
        let textColor: common2D.Color = numberToRGBA(runStyle?.color);
        console.info(`Print text color ARGB: ${textColor.alpha}, ${textColor.red}, ${textColor.green}, ${textColor.blue}`);
      }
    }
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        textFunc();
      })
    }
  }
}

function numberToRGBA(colorNum: number): common2D.Color {
  const alpha = (colorNum >>> 24) & 0xFF;
  const red = (colorNum >>> 16) & 0xFF;
  const green = (colorNum >>> 8) & 0xFF;
  const blue = colorNum & 0xFF;
  return { alpha: alpha, red: red, green: green, blue: blue };
}
```

## getTypographicBounds

```TypeScript
getTypographicBounds(): TypographicBounds
```

Obtains the typographic boundaries of the typographic unit. These boundaries are associated with the typographic font and font size, but not with the characters. For example, for the string " a b " (which has a space before "a" and a space after "b"), the typographic boundaries include the spaces at the beginning and end of the line.

> **NOTE:** 
> 
> The figure shows the typesetting boundaries for the string " a b ".
> 
> ![TypographicBounds.png](../../../reference/apis-arkgraphics2d/figures/TypographicBounds.png)
> 
> The figure shows the typesetting boundaries for the string "j" or "E".
> 
> !
> [TypographicBounds-Character.png](../../../reference/apis-arkgraphics2d/figures/TypographicBounds-Character.png)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [TypographicBounds](arkts-arkgraphics2d-text-typographicbounds-i.md) | Typographic boundaries of the run. |

**Examples**

```TypeScript
let typographicBounds = runs[0].getTypographicBounds();
```

## paint

```TypeScript
paint(canvas: drawing.Canvas, x: number, y: number): void
```

Paints this run on the canvas with the coordinate point (x, y) as the upper left corner.

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
import { drawing } from '@kit.ArkGraphics2D'
import { text } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit'

function textFunc(pixelmap: PixelMap) {
  let canvas = new drawing.Canvas(pixelmap);
  runs[0].paint(canvas, 0, 0);
}

@Entry
@Component
struct Index {
  @State pixelmap?: PixelMap = undefined;
  fun: Function = textFunc;
  build() {
    Column() {
      Image(this.pixelmap).width(200).height(200);
      Button().onClick(() => {
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
