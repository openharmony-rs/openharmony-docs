# Paragraph

保存文本内容及样式的载体，支持排版与绘制操作。

下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md)类的[build()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#build-1)接口获取到Paragraph对象实例，再通过此实例调用对应方法。

**起始版本：** 12

<!--Device-text-class Paragraph--><!--Device-text-class Paragraph-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

<a id="didexceedmaxlines"></a>
## didExceedMaxLines

```TypeScript
didExceedMaxLines(): boolean
```

返回段落是否超过最大行数。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-didExceedMaxLines(): boolean--><!--Device-Paragraph-didExceedMaxLines(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示段落超出了最大行限制，false则表示没有超出最大行限制。 |

**示例：**

```TypeScript
let didExceed = paragraph.didExceedMaxLines();

```

<a id="forcereuserasterresult"></a>
## forceReuseRasterResult

```TypeScript
forceReuseRasterResult(isForce: boolean): void
```

是否强制复用栅格化结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-forceReuseRasterResult(isForce: boolean): void--><!--Device-Paragraph-forceReuseRasterResult(isForce: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForce | boolean | 是 | 是否强制复用栅格化结果。True表示强制复用光栅化结果。False表示允许更新光栅化结果。默认值为false。 |

**示例：**

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

<a id="getactualtextrange"></a>
## getActualTextRange

```TypeScript
getActualTextRange(lineNumber: number, includeSpaces: boolean): Range
```

获取指定行的实际可见文本范围，不包括溢出的省略号。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getActualTextRange(lineNumber: int, includeSpaces: boolean): Range--><!--Device-Paragraph-getActualTextRange(lineNumber: int, includeSpaces: boolean): Range-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineNumber | number | 是 | 要获取文本范围的行索引，行索引从0开始。该接口只能获取已有行的边界，即输入行索引从0开始。最大行索引为文本行数量-1，文本行数量可通过[getLineCount](arkts-arkgraphics2d-text-paragraph-c.md#getlinecount-1)接口获取。 |
| includeSpaces | boolean | 是 | 表示是否应包含空白字符。true表示包含空白字符，false表示不包含空白字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 返回对应行数的实际文本范围。如果行索引非法，返回的start和end均为0。 |

**示例：**

```TypeScript
let rang = paragraph.getActualTextRange(0, true);

```

<a id="getalphabeticbaseline"></a>
## getAlphabeticBaseline

```TypeScript
getAlphabeticBaseline(): number
```

获取拉丁字母基线位置。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getAlphabeticBaseline(): double--><!--Device-Paragraph-getAlphabeticBaseline(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 拉丁字母下的基线位置，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let alphabeticBaseline = paragraph.getAlphabeticBaseline();

```

<a id="getcharacterpositionatcoordinate"></a>
## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: number, y: number, encoding: drawing.TextEncoding): PositionWithAffinity
```

获取与给定坐标最接近的字符位置信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getCharacterPositionAtCoordinate(x: double, y: double, encoding: drawing.TextEncoding): PositionWithAffinity--><!--Device-Paragraph-getCharacterPositionAtCoordinate(x: double, y: double, encoding: drawing.TextEncoding): PositionWithAffinity-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 文本排版区域内的水平坐标，单位为物理像素（px）。相对于文本排版区域左上角的x偏移量，向右为正方向。支持浮点数，可取负值（表示在文本区域左侧）。坐标超出文本区域范围时，将返回最近的字符位置。可通过触摸事件或点击事件获取。 |
| y | number | 是 | 文本排版区域内的垂直坐标，单位为物理像素（px）。相对于文本排版区域左上角的y偏移量，向下为正方向。支持浮点数，可取负值（表示在文本区域上方）。坐标超出文本区域范围时，将返回最近的字符位置。可通过触摸事件或点击事件获取。 |
| encoding | drawing.TextEncoding | 是 | 文本编码类型。目前仅支持UTF-8和UTF-16编码类型。对于UTF-8编码，返回的字符位置表示字节偏移量。对于UTF-16编码，返回的字符位置表示UTF-16编码单元偏移量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PositionWithAffinity](../../apis-arkui/arkts-apis/arkts-arkui-positionwithaffinity-i.md) | 字符位置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

**示例：**

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

<a id="getcharacterrangeforglyphrange"></a>
## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: Range, encoding: drawing.TextEncoding): Array<Range>
```

获取指定字形范围对应的字符范围。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getCharacterRangeForGlyphRange(glyphRange: Range, encoding: drawing.TextEncoding): Array<Range>--><!--Device-Paragraph-getCharacterRangeForGlyphRange(glyphRange: Range, encoding: drawing.TextEncoding): Array<Range>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphRange | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 字形范围。 |
| encoding | drawing.TextEncoding | 是 | 文本编码类型。目前仅支持UTF-8和UTF-16编码类型。对于UTF-8编码，返回的字符范围表示字节范围。对于UTF-16编码，返回的字符范围表示UTF-16编码单元范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Range&gt; | 字符范围。如果数组包含一个元素，它表示字符范围。如果包含两个元素，第一个是字符范围，第二个是实际的字形范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

**示例：**

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

<a id="getglyphpositionatcoordinate"></a>
## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity
```

获取与给定坐标最接近的字形位置信息。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getGlyphPositionAtCoordinate(x: double, y: double): PositionWithAffinity--><!--Device-Paragraph-getGlyphPositionAtCoordinate(x: double, y: double): PositionWithAffinity-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 横坐标，浮点数，单位为物理像素px。 |
| y | number | 是 | 纵坐标，浮点数，单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PositionWithAffinity](../../apis-arkui/arkts-apis/arkts-arkui-positionwithaffinity-i.md) | 字形位置信息。 |

**示例：**

```TypeScript
let positionWithAffinity = paragraph.getGlyphPositionAtCoordinate(0, 0);

```

<a id="getglyphrangeforcharacterrange"></a>
## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(characterRange: Range, encoding: drawing.TextEncoding): Array<Range>
```

获取指定字符范围对应的字形范围。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getGlyphRangeForCharacterRange(characterRange: Range, encoding: drawing.TextEncoding): Array<Range>--><!--Device-Paragraph-getGlyphRangeForCharacterRange(characterRange: Range, encoding: drawing.TextEncoding): Array<Range>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characterRange | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 字符范围。 |
| encoding | drawing.TextEncoding | 是 | 文本编码类型。目前仅支持UTF-8和UTF-16编码类型。对于UTF-8编码，返回的实际字符范围表示字节范围。对于UTF-16编码，返回的实际字符范围表示UTF-16编码单元范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Range&gt; | 字形范围。数组包含两个元素，第一个是字形范围，第二个是实际的字符范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

**示例：**

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

<a id="getheight"></a>
## getHeight

```TypeScript
getHeight(): number
```

获取文本总高度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getHeight(): double--><!--Device-Paragraph-getHeight(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 总高度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let height = paragraph.getHeight();

```

<a id="getideographicbaseline"></a>
## getIdeographicBaseline

```TypeScript
getIdeographicBaseline(): number
```

获取表意字（如CJK（中文，日文，韩文））下的基线位置。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getIdeographicBaseline(): double--><!--Device-Paragraph-getIdeographicBaseline(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取表意字下的基线位置，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let ideographicBaseline = paragraph.getIdeographicBaseline();

```

<a id="getlinecount"></a>
## getLineCount

```TypeScript
getLineCount(): number
```

返回文本行数。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLineCount(): int--><!--Device-Paragraph-getLineCount(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文本行数量，整数。 |

**示例：**

```TypeScript
let lineCount = paragraph.getLineCount();

```

<a id="getlineheight"></a>
## getLineHeight

```TypeScript
getLineHeight(line: number): number
```

返回指定行的行高。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLineHeight(line: int): double--><!--Device-Paragraph-getLineHeight(line: int): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| line | number | 是 | 文本行索引，整数，范围为0~getLineCount()-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 行高，单位为物理像素px。 |

**示例：**

```TypeScript
let lineHeight = paragraph.getLineHeight(0);

```

<a id="getlinemetrics"></a>
## getLineMetrics

```TypeScript
getLineMetrics(): Array<LineMetrics>
```

获取文本行的行度量数组。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLineMetrics(): Array<LineMetrics>--><!--Device-Paragraph-getLineMetrics(): Array<LineMetrics>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LineMetrics&gt; | 文本行的行度量数组。 |

**示例：**

```TypeScript
let arrLineMetric =  paragraph.getLineMetrics();

```

<a id="getlinemetrics-1"></a>
## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: number): LineMetrics | undefined
```

获取特定行号的行度量信息。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLineMetrics(lineNumber: int): LineMetrics | undefined--><!--Device-Paragraph-getLineMetrics(lineNumber: int): LineMetrics | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineNumber | number | 是 | 要查询度量信息的行的编号，行号从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LineMetrics](../../apis-arkui/arkts-apis/arkts-arkui-linemetrics-t.md) | **LineMetrics** object containing the measurement information if the specified line number is valid and the measurement information exists. If the line number is invalid or the measurement information cannot be obtained, **undefined** is returned. |

**示例：**

```TypeScript
let lineMetrics =  paragraph.getLineMetrics(0);

```

<a id="getlinewidth"></a>
## getLineWidth

```TypeScript
getLineWidth(line: number): number
```

返回指定行的行宽。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLineWidth(line: int): double--><!--Device-Paragraph-getLineWidth(line: int): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| line | number | 是 | 文本行索引，整数，范围为0~getLineCount()-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 行宽，单位为物理像素px。 |

**示例：**

```TypeScript
let lineWidth = paragraph.getLineWidth(0);

```

<a id="getlongestline"></a>
## getLongestLine

```TypeScript
getLongestLine(): number
```

获取文本最长行宽。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLongestLine(): double--><!--Device-Paragraph-getLongestLine(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最长一行的宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let longestLine = paragraph.getLongestLine();

```

<a id="getlongestlinewithindent"></a>
## getLongestLineWithIndent

```TypeScript
getLongestLineWithIndent(): number
```

获取文本最长一行的宽度（包含缩进），建议向上取整。文本内容为空时返回0。

**起始版本：** 13

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getLongestLineWithIndent(): double--><!--Device-Paragraph-getLongestLineWithIndent(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最长一行的宽度（该宽度包含当前行缩进的宽度），浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let longestLineWithIndent = paragraph.getLongestLineWithIndent();

```

<a id="getmaxintrinsicwidth"></a>
## getMaxIntrinsicWidth

```TypeScript
getMaxIntrinsicWidth(): number
```

获取段落最大固有宽度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getMaxIntrinsicWidth(): double--><!--Device-Paragraph-getMaxIntrinsicWidth(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该段落所占水平空间的最大固有宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let maxIntrinsicWidth = paragraph.getMaxIntrinsicWidth();

```

<a id="getmaxwidth"></a>
## getMaxWidth

```TypeScript
getMaxWidth(): number
```

获取文本最大行宽。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getMaxWidth(): double--><!--Device-Paragraph-getMaxWidth(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 最大的行宽，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let maxWidth = paragraph.getMaxWidth();

```

<a id="getminintrinsicwidth"></a>
## getMinIntrinsicWidth

```TypeScript
getMinIntrinsicWidth(): number
```

获取段落最小固有宽度。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getMinIntrinsicWidth(): double--><!--Device-Paragraph-getMinIntrinsicWidth(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该段落所占水平空间的最小固有宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let minIntrinsicWidth = paragraph.getMinIntrinsicWidth();

```

<a id="getparagraphstyle"></a>
## getParagraphStyle

```TypeScript
getParagraphStyle(): ParagraphStyle
```

获取段落的样式配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getParagraphStyle(): ParagraphStyle--><!--Device-Paragraph-getParagraphStyle(): ParagraphStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md) | 段落的样式配置。 |

**示例：**

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

<a id="getprocessstate"></a>
## getProcessState

```TypeScript
getProcessState(): TextProcessState
```

获取段落的文本处理状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getProcessState(): TextProcessState--><!--Device-Paragraph-getProcessState(): TextProcessState-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextProcessState](arkts-arkgraphics2d-text-textprocessstate-e.md) | 段落的文本处理状态。 |

**示例：**

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

<a id="getrectsforplaceholders"></a>
## getRectsForPlaceholders

```TypeScript
getRectsForPlaceholders(): Array<TextBox>
```

获取文本中所有占位符所占的矩形区域。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getRectsForPlaceholders(): Array<TextBox>--><!--Device-Paragraph-getRectsForPlaceholders(): Array<TextBox>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextBox&gt; | 矩形区域数组。 |

**示例：**

```TypeScript
let placeholderRects = paragraph.getRectsForPlaceholders();

```

<a id="getrectsforrange"></a>
## getRectsForRange

```TypeScript
getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>
```

获取给定的矩形区域宽度以及矩形区域高度的规格下，文本中该区间范围内的字符所占的矩形区域。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>--><!--Device-Paragraph-getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 需要获取的区域的文本区间。 |
| widthStyle | [RectWidthStyle](arkts-arkgraphics2d-text-rectwidthstyle-e.md) | 是 | 返回的矩形区域的宽度的规格。 |
| heightStyle | [RectHeightStyle](arkts-arkgraphics2d-text-rectheightstyle-e.md) | 是 | 返回的矩形区域的高度的规格。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextBox&gt; | 矩形区域数组。 |

**示例：**

```TypeScript
let range: text.Range = { start: 0, end: 1};
let rects = paragraph.getRectsForRange(range, text.RectWidthStyle.TIGHT, text.RectHeightStyle.TIGHT);

```

<a id="gettextdisplaystate"></a>
## getTextDisplayState

```TypeScript
getTextDisplayState(): TextDisplayState
```

获取段落的文本显示状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getTextDisplayState(): TextDisplayState--><!--Device-Paragraph-getTextDisplayState(): TextDisplayState-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextDisplayState](arkts-arkgraphics2d-text-textdisplaystate-e.md) | 段落的文本显示状态。 |

**示例：**

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

<a id="gettextlines"></a>
## getTextLines

```TypeScript
getTextLines(): Array<TextLine>
```

返回所有的文本行。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getTextLines(): Array<TextLine>--><!--Device-Paragraph-getTextLines(): Array<TextLine>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextLine&gt; | 文本行载体数组。 |

**示例：**

```TypeScript
let lines = paragraph.getTextLines();

```

<a id="getvisibletextranges"></a>
## getVisibleTextRanges

```TypeScript
getVisibleTextRanges(): Array<Range>
```

获取段落中在屏幕上可见的文本范围。不包含因最大行数（[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)的maxLines属性）截断或省略号模式（[EllipsisMode](arkts-arkgraphics2d-text-ellipsismode-e.md)）替换而未显示的文本。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getVisibleTextRanges(): Array<Range>--><!--Device-Paragraph-getVisibleTextRanges(): Array<Range>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Range&gt; | 段落可见文本范围数组，范围为UTF-16编码单元索引。 |

**示例：**

```TypeScript
let visibleRanges = paragraph.getVisibleTextRanges();

```

<a id="getwordboundary"></a>
## getWordBoundary

```TypeScript
getWordBoundary(offset: number): Range
```

返回给定offset的字形所在单词的索引区间。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-getWordBoundary(offset: int): Range--><!--Device-Paragraph-getWordBoundary(offset: int): Range-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 字形的偏移量，整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 单词的索引区间。 |

**示例：**

```TypeScript
let wordRange = paragraph.getWordBoundary(0);

```

<a id="layout"></a>
## layout

```TypeScript
layout(width: number): Promise<void>
```

进行排版并计算所有字形位置，使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-layout(width: double): Promise<void>--><!--Device-Paragraph-layout(width: double): Promise<void>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 单行的最大宽度，浮点数，单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
// 添加文本字符串
paragraphBuilder.addText("test");
// 生成排版对象
let paragraph = paragraphBuilder.build();

function textFunc(pixelmap: PixelMap) {
  // 通过图片对象构造画布
  let canvas = new drawing.Canvas(pixelmap);
  // 进行绘制文本字符串
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
            // 构造图片对象
            this.pixelmap = image.createPixelMapSync(color, opts);
          }
          // 进行绘制文字
          this.fun(this.pixelmap);
        })
    }
  }
}

```

<a id="layoutsync"></a>
## layoutSync

```TypeScript
layoutSync(width: number): void
```

进行排版并计算所有字形位置。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-layoutSync(width: double): void--><!--Device-Paragraph-layoutSync(width: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 单行的最大宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
paragraph.layoutSync(100);

```

<a id="layoutwithconstraints"></a>
## layoutWithConstraints

```TypeScript
layoutWithConstraints(size: TextRectSize): TextLayoutResult
```

使用给定的高度和宽度进行排版并计算所有字形的位置。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-layoutWithConstraints(size: TextRectSize): TextLayoutResult--><!--Device-Paragraph-layoutWithConstraints(size: TextRectSize): TextLayoutResult-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [TextRectSize](arkts-arkgraphics2d-text-textrectsize-i.md) | 是 | 约束的高度和宽度，单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextLayoutResult](arkts-arkgraphics2d-text-textlayoutresult-i.md) | 布局后的实际尺寸和排版后容下的字符范围。 |

**示例：**

```TypeScript
let size: text.TextRectSize = { width: 200, height: 100 };
let result = paragraph.layoutWithConstraints(size); // 功能增强的 layoutSync
console.info('Width: ' + result.correctRect.width + ', Height: ' + result.correctRect.height);
for (let i = 0; i < result.fitStrRange.length; ++i) {
  console.info('fitRange: [' + result.fitStrRange[i].start + ', ' + result.fitStrRange[i].end + ']');
}

```

<a id="paint"></a>
## paint

```TypeScript
paint(canvas: drawing.Canvas, x: number, y: number): void
```

在画布上以 (x, y) 为左上角绘制文本。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-paint(canvas: drawing.Canvas, x: double, y: double): void--><!--Device-Paragraph-paint(canvas: drawing.Canvas, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | drawing.Canvas | 是 | 绘制的目标画布。 |
| x | number | 是 | 绘制的左上角位置的横坐标，浮点数，单位为物理像素px。 |
| y | number | 是 | 绘制的左上角位置的纵坐标，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
const color: ArrayBuffer = new ArrayBuffer(160000);
let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
let canvas = new drawing.Canvas(pixelMap);
paragraph.paint(canvas, 0, 0);

```

<a id="paintonpath"></a>
## paintOnPath

```TypeScript
paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void
```

在画布上沿路径绘制文本。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: double, vOffset: double): void--><!--Device-Paragraph-paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: double, vOffset: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | drawing.Canvas | 是 | 绘制的目标画布。 |
| path | drawing.Path | 是 | 确认文字位置的路径。 |
| hOffset | number | 是 | 沿路径方向偏置，从路径起点向前为正，向后为负，单位为物理像素px。 |
| vOffset | number | 是 | 沿路径垂直方向偏置，沿路径方向左侧为负，右侧为正，单位为物理像素px。 |

**示例：**

```TypeScript
const color: ArrayBuffer = new ArrayBuffer(160000);
let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
let canvas = new drawing.Canvas(pixelMap);
let path = new drawing.Path();
path.arcTo(20, 20, 180, 180, 180, 90);
paragraph.paintOnPath(canvas, path, 0, 0);

```

<a id="updatecolor"></a>
## updateColor

```TypeScript
updateColor(color: common2D.Color): void
```

更新整个文本段落的颜色。如果当前装饰线未设置颜色，使用该接口也会同时更新装饰线的颜色。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-updateColor(color: common2D.Color): void--><!--Device-Paragraph-updateColor(color: common2D.Color): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | 更新后的字体色。 |

**示例：**

```TypeScript
paragraph.updateColor({ alpha: 255, red: 255, green: 0, blue: 0 });

```

<a id="updatedecoration"></a>
## updateDecoration

```TypeScript
updateDecoration(decoration: Decoration): void
```

更新整个文本段落的装饰线。

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Paragraph-updateDecoration(decoration: Decoration): void--><!--Device-Paragraph-updateDecoration(decoration: Decoration): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decoration | [Decoration](arkts-arkgraphics2d-text-decoration-i.md) | 是 | 更新后的装饰线。 |

**示例：**

```TypeScript
paragraph.updateDecoration({
  textDecoration: text.TextDecorationType.OVERLINE,
  color: { alpha: 255, red: 255, green: 0, blue: 0 },
  decorationStyle: text.TextDecorationStyle.WAVY,
  decorationThicknessScale: 2.0,
});

```

