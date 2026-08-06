# TextLine

描述段落基础文本行结构的载体。 下列API示例中都需先使用[Paragraph]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类的[getTextLines()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口或者 [LineTypeset]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_类的[createLine()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口获取到TextLine对象实例，再通过此实例调用对 应方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-text-class TextLine--><!--Device-text-class TextLine-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## createTruncatedLine

```TypeScript
createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine
```

创建一个截断的文本行对象。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine--><!--Device-TextLine-createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | double | 是 | 截断后的行宽度，浮点数，单位为物理像素px。 |
| ellipsisMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 截断的类型，当前仅支持头部截断START和尾部截断END。 |
| ellipsis | string | 是 | 截断的标记字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 截断的文本行对象。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { drawing, text } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit'

function textFunc(pixelmap: PixelMap) {
  let canvas = new drawing.Canvas(pixelmap);
  let truncatedTextLine = lines[0].createTruncatedLine(100, text.EllipsisMode.START, "...");
  truncatedTextLine.paint(canvas, 0, 100);
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
          let opts: image.InitializationOptions =
            { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, Image, ClickEvent} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { drawing, text, common2D } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit';

function textFunc(pixelmap?: image.PixelMap) {
  if (pixelmap) {
    let canvas = new drawing.Canvas(pixelmap);
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
    let lines = paragraph.getTextLines();
    let truncatedTextLine = lines[0].createTruncatedLine(100, text.EllipsisMode.START, "...");
    if (truncatedTextLine != undefined) {
      truncatedTextLine.paint(canvas, 0, 100);
    }
  }
}

@Entry
@Component
struct Index {
  @State pixelmap?: image.PixelMap = undefined;
  fun: (pixelmap?: image.PixelMap) => void = textFunc;
  build() {
    Column() {
      Image(this.pixelmap).width(200).height(200);
      Button("Click").onClick((e: ClickEvent) => {
        if (this.pixelmap == undefined) {
          const color: ArrayBuffer = new ArrayBuffer(160000);
          let opts: image.InitializationOptions =
            { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}
```

## createTruncatedLine

```TypeScript
createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine | undefined
```

创建一个截断的文本行对象

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextLine-createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine | undefined--><!--Device-TextLine-createTruncatedLine(width: double, ellipsisMode: EllipsisMode, ellipsis: string): TextLine | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | double | 是 | 截断后的行宽度 |
| ellipsisMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 省略的类型，当前不支持中部省略 |
| ellipsis | string | 是 | 用于省略的文字 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Truncated text line object. |

## enumerateCaretOffsets

```TypeScript
enumerateCaretOffsets(callback: CaretOffsetsCallback): void
```

枚举文本行中每个字符的偏移量和索引值。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-enumerateCaretOffsets(callback: CaretOffsetsCallback): void--><!--Device-TextLine-enumerateCaretOffsets(callback: CaretOffsetsCallback): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用户自定义函数。回调方法参数包括文本行中每个字符的偏移量和索引值。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
lines[0].enumerateCaretOffsets((offset: number, index: number, leadingEdge: boolean): boolean => {
  console.info('textLine: offset: ' + offset + ', index: ' + index + ', leadingEdge: ' + leadingEdge);
  return index > 50;
});
```

ArkTS-Sta示例：

```TypeScript
lines[0].enumerateCaretOffsets((offset: double, index: int, leadingEdge: boolean): boolean => {
  console.info('textLine: offset: ' + offset + ', index: ' + index + ', leadingEdge: ' + leadingEdge);
  return index > 50;
});
```

## getAlignmentOffset

ArkTS-Dyn:
```TypeScript
getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number
```

ArkTS-Sta:
```TypeScript
getAlignmentOffset(alignmentFactor: double, alignmentWidth: double): double
```

获取文本行根据对齐因子和对齐宽度计算的对齐所需偏移量。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getAlignmentOffset(alignmentFactor: double, alignmentWidth: double): double--><!--Device-TextLine-getAlignmentOffset(alignmentFactor: double, alignmentWidth: double): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignmentFactor | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 对齐因子，即对齐的程度，浮点数。小于等于0.0表示左对齐，大于0.0小于0.5表示偏左对齐，0.5表示居中对齐，大于0.5小于1.0表示偏右对齐，大于等于1.0表示右对齐。 |
| alignmentWidth | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 对齐宽度，即文本行的宽度，浮点数，单位为物理像素px。小于文本行的实际宽度时，返回0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 计算得到的对齐所需偏移量，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let alignmentOffset = lines[0].getAlignmentOffset(0.5, 500);
```

## getGlyphCount

ArkTS-Dyn:
```TypeScript
getGlyphCount(): number
```

ArkTS-Sta:
```TypeScript
getGlyphCount(): int
```

获取文本行中字形的数量。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getGlyphCount(): int--><!--Device-TextLine-getGlyphCount(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 该文本行中字形数量，整数。 |

**示例：**

```TypeScript
let glyphCount = lines[0].getGlyphCount();
```

## getGlyphRuns

```TypeScript
getGlyphRuns(): Array<Run>
```

获取文本行的排版单元数组。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getGlyphRuns(): Array<Run>--><!--Device-TextLine-getGlyphRuns(): Array<Run>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Run&gt; | 该文本行中的文本排版单元数组。 |

**示例：**

```TypeScript
let runs = lines[0].getGlyphRuns();
```

## getImageBounds

```TypeScript
getImageBounds(): common2D.Rect
```

获取文本行的图像边界。文本行图像边界与排版字体、排版字号、字符本身都有关，相当于视觉边界。例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，用户在界面上只能看到"a b"，图像边界即为不包括带行首 和末尾空格的边界。例如字符串为"j"或"E"，视觉边界不同，即与字符本身有关，"j"字符串的视觉边界宽度小于"E"字符串的视觉边界宽度，"j"字符串的视觉边界高度大于"E"字符串的视觉边界高度。 > **说明：** > > 示意图展示了字符串为" a b "的图像边界。 > > !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > > 示意图展示了字符串为"j"或"E"的图像边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getImageBounds(): common2D.Rect--><!--Device-TextLine-getImageBounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Image boundary of a text line, in physical pixels (px). |

**示例：**

```TypeScript
let imageBounds = lines[0].getImageBounds();
```

## getOffsetForStringIndex

ArkTS-Dyn:
```TypeScript
getOffsetForStringIndex(index: number): number
```

ArkTS-Sta:
```TypeScript
getOffsetForStringIndex(index: int): double
```

获取文本行中给定字符串索引处的偏移量。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getOffsetForStringIndex(index: int): double--><!--Device-TextLine-getOffsetForStringIndex(index: int): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 要获取偏移量的字符串索引，整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 给定字符串索引处的偏移量，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let offset = lines[0].getOffsetForStringIndex(3);
```

## getStringIndexForPosition

ArkTS-Dyn:
```TypeScript
getStringIndexForPosition(point: common2D.Point): number
```

ArkTS-Sta:
```TypeScript
getStringIndexForPosition(point: common2D.Point): int
```

获取给定位置在原始字符串中的字符索引。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getStringIndexForPosition(point: common2D.Point): int--><!--Device-TextLine-getStringIndexForPosition(point: common2D.Point): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 要查找索引的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 给定位置在文本行中对应的字符串索引，整数。 |

**示例：**

```TypeScript
let point : common2D.Point = { x: 15.0, y: 2.0 };
let index = lines[0].getStringIndexForPosition(point);
```

## getTextRange

```TypeScript
getTextRange(): Range
```

获取该行文本在整个段落文本中的索引区间。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getTextRange(): Range--><!--Device-TextLine-getTextRange(): Range-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 该行文本在整个段落文本中的索引区间。 |

**示例：**

```TypeScript
let textRange = lines[0].getTextRange();
```

## getTrailingSpaceWidth

ArkTS-Dyn:
```TypeScript
getTrailingSpaceWidth(): number
```

ArkTS-Sta:
```TypeScript
getTrailingSpaceWidth(): double
```

获取文本行尾部空白字符的宽度。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getTrailingSpaceWidth(): double--><!--Device-TextLine-getTrailingSpaceWidth(): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 文本行尾部空白字符的宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let trailingSpaceWidth = lines[0].getTrailingSpaceWidth();
```

## getTypographicBounds

```TypeScript
getTypographicBounds(): TypographicBounds
```

获取文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关。例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版 边界相同，即与字符本身无关。 > **说明：** > > 示意图展示了字符串为" a b "的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > > 示意图展示了字符串为"j"或"E"的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-getTypographicBounds(): TypographicBounds--><!--Device-TextLine-getTypographicBounds(): TypographicBounds-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 文本行的排版边界。 |

**示例：**

```TypeScript
let bounds = lines[0].getTypographicBounds();
console.info('textLine ascent:' + bounds.ascent + ', descent:' + bounds.descent + ', leading:' + bounds.leading + ', width:' + bounds.width);
```

## paint

ArkTS-Dyn:
```TypeScript
paint(canvas: drawing.Canvas, x: number, y: number): void
```

ArkTS-Sta:
```TypeScript
paint(canvas: drawing.Canvas, x: double, y: double): void
```

在画布上以坐标点(x, y)为左上角位置绘制该文本行。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextLine-paint(canvas: drawing.Canvas, x: double, y: double): void--><!--Device-TextLine-paint(canvas: drawing.Canvas, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | drawing.Canvas | 是 | 绘制的目标canvas。 |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 绘制的左上角位置的横坐标，浮点数，单位为物理像素px。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 绘制的左上角位置的纵坐标，浮点数，单位为物理像素px。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { drawing } from '@kit.ArkGraphics2D'
import { image } from '@kit.ImageKit'

function textFunc(pixelmap: PixelMap) {
  let canvas = new drawing.Canvas(pixelmap);
  lines[0].paint(canvas, 0, 0);
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
          let opts: image.InitializationOptions =
            { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, Image, ClickEvent} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { drawing } from '@kit.ArkGraphics2D'
import { text } from "@kit.ArkGraphics2D"
import { image } from '@kit.ImageKit';

function textFunc(pixelmap?: image.PixelMap) {
  if (pixelmap) {
    let canvas = new drawing.Canvas(pixelmap);
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
    let lines = paragraph.getTextLines();
    lines[0].paint(canvas, 0, 0);
  }
}

@Entry
@Component
struct Index {
  @State pixelmap?: image.PixelMap = undefined;
  fun: (pixelmap?: image.PixelMap) => void = textFunc;
  build() {
    Column() {
      Image(this.pixelmap).width(200).height(200);
      Button("Click").onClick((e: ClickEvent) => {
        if (this.pixelmap == undefined) {
          const color: ArrayBuffer = new ArrayBuffer(160000);
          let opts: image.InitializationOptions =
            { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}
```

