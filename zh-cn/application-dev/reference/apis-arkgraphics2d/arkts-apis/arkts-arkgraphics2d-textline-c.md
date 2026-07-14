# TextLine

描述段落基础文本行结构的载体。

下列API示例中都需先使用[Paragraph](arkts-arkgraphics2d-paragraphstyle-i.md)类的[getTextLines()](arkts-arkgraphics2d-paragraph-c.md#gettextlines-1)接口或者
[LineTypeset](arkts-arkgraphics2d-linetypeset-c.md)类的[createLine()](arkts-arkgraphics2d-linetypeset-c.md#createline-1)接口获取到TextLine对象实例，再通过此实例调用对
应方法。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## createTruncatedLine

```TypeScript
createTruncatedLine(width: number, ellipsisMode: EllipsisMode, ellipsis: string): TextLine
```

创建一个截断的文本行对象。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 截断后的行宽度，浮点数，单位为物理像素px。 |
| ellipsisMode | EllipsisMode | 是 | 截断的类型，当前仅支持头部截断START和尾部截断END。 |
| ellipsis | string | 是 | 截断的标记字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextLine | 截断的文本行对象。 |

**示例：**

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
          let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}

```

## enumerateCaretOffsets

```TypeScript
enumerateCaretOffsets(callback: CaretOffsetsCallback): void
```

枚举文本行中每个字符的偏移量和索引值。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | CaretOffsetsCallback | 是 | 用户自定义函数。回调方法参数包括文本行中每个字符的偏移量和索引值。 |

**示例：**

```TypeScript
lines[0].enumerateCaretOffsets((offset: number, index: number, leadingEdge: boolean): boolean => {
  console.info('textLine: offset: ' + offset + ', index: ' + index + ', leadingEdge: ' + leadingEdge);
  return index > 50;
});

```

## getAlignmentOffset

```TypeScript
getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number
```

获取文本行根据对齐因子和对齐宽度计算的对齐所需偏移量。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignmentFactor | number | 是 | 对齐因子，即对齐的程度，浮点数。小于等于0.0表示左对齐，大于0.0小于0.5表示偏左对齐，0.5表示居中对齐，大于0.5小于1.0表示偏右对齐，大于等于1.0表示右对齐。 |
| alignmentWidth | number | 是 | 对齐宽度，即文本行的宽度，浮点数，单位为物理像素px。小于文本行的实际宽度时，返回0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 计算得到的对齐所需偏移量，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let alignmentOffset = lines[0].getAlignmentOffset(0.5, 500);

```

## getGlyphCount

```TypeScript
getGlyphCount(): number
```

获取文本行中字形的数量。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该文本行中字形数量，整数。 |

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

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

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

获取文本行的图像边界。文本行图像边界与排版字体、排版字号、字符本身都有关，相当于视觉边界。例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，用户在界面上只能看到"a b"，图像边界即为不包括带行首
和末尾空格的边界。例如字符串为"j"或"E"，视觉边界不同，即与字符本身有关，"j"字符串的视觉边界宽度小于"E"字符串的视觉边界宽度，"j"字符串的视觉边界高度大于"E"字符串的视觉边界高度。

> **说明：**
>
> 示意图展示了字符串为" a b "的图像边界。
>
> ![zh-ch_image_ImageBounds.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_ImageBounds.png)
>
> 示意图展示了字符串为"j"或"E"的图像边界。
>
> !
> [zh-ch_image_ImageBounds_Character.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_ImageBounds_Character.png)

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

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

```TypeScript
getOffsetForStringIndex(index: number): number
```

获取文本行中给定字符串索引处的偏移量。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要获取偏移量的字符串索引，整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 给定字符串索引处的偏移量，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let offset = lines[0].getOffsetForStringIndex(3);

```

## getStringIndexForPosition

```TypeScript
getStringIndexForPosition(point: common2D.Point): number
```

获取给定位置在原始字符串中的字符索引。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 要查找索引的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 给定位置在文本行中对应的字符串索引，整数。 |

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

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Range | 该行文本在整个段落文本中的索引区间。 |

**示例：**

```TypeScript
let textRange = lines[0].getTextRange();

```

## getTrailingSpaceWidth

```TypeScript
getTrailingSpaceWidth(): number
```

获取文本行尾部空白字符的宽度。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文本行尾部空白字符的宽度，浮点数，单位为物理像素px。 |

**示例：**

```TypeScript
let trailingSpaceWidth = lines[0].getTrailingSpaceWidth();

```

## getTypographicBounds

```TypeScript
getTypographicBounds(): TypographicBounds
```

获取文本行的排版边界。文本行排版边界与排版字体、排版字号有关，与字符本身无关。例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。例如字符串为"j"或"E"，排版
边界相同，即与字符本身无关。

> **说明：**
>
> 示意图展示了字符串为" a b "的排版边界。
>
> !
> [zh-ch_image_TypographicBounds.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds.png)
>
> 示意图展示了字符串为"j"或"E"的排版边界。
>
> !
> [zh-ch_image_TypographicBounds_Character.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_TypographicBounds_Character.png)

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TypographicBounds | 文本行的排版边界。 |

**示例：**

```TypeScript
let bounds = lines[0].getTypographicBounds();
console.info('textLine ascent:' + bounds.ascent + ', descent:' + bounds.descent + ', leading:' + bounds.leading + ', width:' + bounds.width);

```

## paint

```TypeScript
paint(canvas: drawing.Canvas, x: number, y: number): void
```

在画布上以坐标点(x, y)为左上角位置绘制该文本行。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | drawing.Canvas | 是 | 绘制的目标canvas。 |
| x | number | 是 | 绘制的左上角位置的横坐标，浮点数，单位为物理像素px。 |
| y | number | 是 | 绘制的左上角位置的纵坐标，浮点数，单位为物理像素px。 |

**示例：**

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
          let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 200, width: 200 } }
          this.pixelmap = image.createPixelMapSync(color, opts);
        }
        this.fun(this.pixelmap);
      })
    }
  }
}

```

