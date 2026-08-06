# Run

文本排版单元。 下列API示例中都需先使用[TextLine]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类的[getGlyphRuns()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口获取Run对象实例，再通过此实例调 用对应方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-text-class Run--><!--Device-text-class Run-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## getAdvances

```TypeScript
getAdvances(range: Range): Array<common2D.Point>
```

获取该排版单元指定范围内每个字形的字形宽度数组。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getAdvances(range: Range): Array<common2D.Point>--><!--Device-Run-getAdvances(range: Range): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要获取的字形位置范围。range.start表示范围开始的位置，range.end表示范围的长度。如果长度是0表示从range.start开始获取到渲染块结束。当range.end、range.start为负数，或者传入null、undefined时，该方法将返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | Returns the glyph width array of each glyph in the run unit relative to the |

**示例：**

ArkTS-Dyn示例：

```TypeScript
let advancesRange = runs[0].getAdvances({start:1, end:2}); // 获取渲染块从起始位置1开始, 长度为2范围内的字形宽度
advancesRange = runs[0].getAdvances({start:-1, end:2}); // -1是非法参数，将返回undefined
advancesRange = runs[0].getAdvances({start:0, end:-10}); // -10是非法参数，将返回undefined
let advancesNull = runs[0].getAdvances(null); // null是非法参数，将返回undefined
```

ArkTS-Sta示例：

```TypeScript
let advancesRange = runs[0].getAdvances({start:1, end:2}); // 获取渲染块从起始位置1开始, 长度为2范围内的字形宽度
advancesRange = runs[0].getAdvances({start:-1, end:2}); // -1是非法参数，将返回undefined
advancesRange = runs[0].getAdvances({start:0, end:-10}); // -10是非法参数，将返回undefined
```

## getAdvances

```TypeScript
getAdvances(range: Range): Array<common2D.Point> | undefined
```

获取指定范围内的字形宽度数组

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Run-getAdvances(range: Range): Array<common2D.Point> | undefined--><!--Device-Run-getAdvances(range: Range): Array<common2D.Point> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | range获取当前run的字形范围，其中start表示起始位置，end表示范围长度，如果长度为0，则获取从start到末尾的字形 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | Array holding the advance width and height of each glyph. |

## getFont

```TypeScript
getFont(): drawing.Font
```

获取排版单元的字体属性对象。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getFont(): drawing.Font--><!--Device-Run-getFont(): drawing.Font-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| drawing.Font | **Font** object of this run. |

**示例：**

```TypeScript
let font = runs[0].getFont();
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

获取该排版单元中字形的数量。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getGlyphCount(): int--><!--Device-Run-getGlyphCount(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 该排版单元中字形数量，整数。 |

**示例：**

```TypeScript
let glyphs = runs[0].getGlyphCount();
```

## getGlyphs

ArkTS-Dyn:
```TypeScript
getGlyphs(): Array<number>
```

ArkTS-Sta:
```TypeScript
getGlyphs(): Array<int>
```

获取该排版单元中每个字符的字形序号。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getGlyphs(): Array<int>--><!--Device-Run-getGlyphs(): Array<int>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | 该排版单元中每个字符对应的字形序号。 |

**示例：**

```TypeScript
let glyph = runs[0].getGlyphs();
```

## getGlyphs

```TypeScript
getGlyphs(range: Range): Array<int>
```

获取该排版单元指定范围内每个字符的字形序号。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getGlyphs(range: Range): Array<int>--><!--Device-Run-getGlyphs(range: Range): Array<int>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要获取的字形序号范围，range.start表示范围开始的位置，range.end表示范围的长度，当range.end为0时表示从range.start开始获取到渲染块结束。当range.end、range.start为负数，或者传入null、undefined时，该方法将返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 该排版单元中每个字符对应的字形序号。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let glyphs = runs[0].getGlyphs(); // 获取渲染块全部字形序号
  let glyphsRange = runs[0].getGlyphs({start:1, end:2}); // 获取渲染块从起始位置1开始，长度为2范围内的字形序号
  glyphsRange = runs[0].getGlyphs({start:-1, end:2}); // -1是非法参数，将返回undefined
  glyphsRange = runs[0].getGlyphs({start:0, end:-10}); // -10是非法参数，将返回undefined
  let glyphsNull = runs[0].getGlyphs(null); // null是非法参数，将返回undefined
  let glyphsUndefined = runs[0].getGlyphs(undefined); // undefined是非法参数，将返回undefined
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"

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
  let lines = paragraph.getTextLines();
  let runs = lines[0].getGlyphRuns();
  let glyphs = runs[0].getGlyphs({ start: 0, end: 0 }); // 获取渲染块全部字形序号
  let glyphsRange = runs[0].getGlyphs({ start: 1, end: 2 }); // 获取渲染块从起始位置1开始, 长度为2范围内的字形序号
  glyphsRange = runs[0].getGlyphs({ start: -1, end: 2 }); // -1是非法参数，将返回undefined
  glyphsRange = runs[0].getGlyphs({ start: 0, end: -10 }); // -10是非法参数，将返回undefined
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;

  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## getGlyphs

```TypeScript
getGlyphs(range: Range): Array<int> | undefined
```

获取范围内每个字符的字形标识符

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Run-getGlyphs(range: Range): Array<int> | undefined--><!--Device-Run-getGlyphs(range: Range): Array<int> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | range获取当前run的字形范围，其中start表示起始位置，end表示范围长度，如果长度为0，则获取从start到末尾的字形 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | Glyph identifier or undefined. |

## getImageBounds

```TypeScript
getImageBounds(): common2D.Rect
```

获取该排版单元的图像边界，图像边界与排版字体、排版字号、字符本身都有关，相当于视觉边界，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，用户在界面上只能看到"a b"，图像边界即为不包括带行首和 末尾空格的边界。 > **说明：** > > 示意图展示了字符串为" a b "的图像边界。 > > !\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > > 示意图展示了字符串为"j"或"E"的图像边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getImageBounds(): common2D.Rect--><!--Device-Run-getImageBounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Image boundary of the layout unit, in physical pixels (px). |

**示例：**

```TypeScript
let bounds = runs[0].getImageBounds();
```

## getOffsets

```TypeScript
getOffsets(): Array<common2D.Point>
```

获取该排版单元中每个字形的索引偏移量。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getOffsets(): Array<common2D.Point>--><!--Device-Run-getOffsets(): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | Array holding the offset of each glyph in the run relative to its index. |

**示例：**

```TypeScript
let offsets = runs[0].getOffsets();
```

## getPositions

```TypeScript
getPositions(): Array<common2D.Point>
```

获取该排版单元中每个字形相对于每行的字形位置。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getPositions(): Array<common2D.Point>--><!--Device-Run-getPositions(): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | Array holding the position of each glyph relative to the respective line in |

**示例：**

```TypeScript
let positions = runs[0].getPositions();
```

## getPositions

```TypeScript
getPositions(range: Range): Array<common2D.Point>
```

获取该排版单元指定范围内每个字形相对于每行的字形位置数组。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getPositions(range: Range): Array<common2D.Point>--><!--Device-Run-getPositions(range: Range): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要获取的字形位置范围，range.start表示范围开始的位置，range.end表示范围的长度，如果长度是0表示从范围range.start开始获取到渲染块结束。当range.end、range.start为负数，或者传入null、undefined时，该方法将返回undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | Array holding the position of each glyph relative to the respective line in |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let positions = runs[0].getPositions(); // 获取渲染块全部字形位置
  let positionsRange = runs[0].getPositions({start:1, end:2}); // 获取渲染块从起始位置1开始, 长度为2范围内的字形位置
  positionsRange = runs[0].getPositions({start:-1, end:2}); // -1是非法参数，将返回undefined
  positionsRange = runs[0].getPositions({start:0, end:-10}); // -10是非法参数，将返回undefined
  let positionsNull = runs[0].getPositions(null); // null是非法参数，将返回undefined
  let positionsUndefined = runs[0].getPositions(undefined); // undefined是非法参数，将返回undefined
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D";

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
  let lines = paragraph.getTextLines();
  let runs = lines[0].getGlyphRuns();
  let positions = runs[0].getPositions({ start: 0, end: 0 }); // 获取渲染块全部字形位置
  let positionsRange = runs[0].getPositions({ start: 1, end: 2 }); // 获取渲染块从起始位置1开始, 长度为2范围内的字形位置
  positionsRange = runs[0].getPositions({ start: -1, end: 2 }); // -1是非法参数，将返回undefined
  positionsRange = runs[0].getPositions({ start: 0, end: -10 }); // -10是非法参数，将返回undefined
}


@Entry
@Component
struct Index {
  fun: () => void = textFunc;

  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## getPositions

```TypeScript
getPositions(range: Range): Array<common2D.Point> | undefined
```

获取指定范围内字体位置信息

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Run-getPositions(range: Range): Array<common2D.Point> | undefined--><!--Device-Run-getPositions(range: Range): Array<common2D.Point> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | range获取当前run的字形范围，其中start表示起始位置，end表示范围长度，如果长度为0，则获取从start到末尾的字形 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | The position of the font in the layout or undefined. |

## getStringIndices

```TypeScript
getStringIndices(range?: Range): Array<int>
```

获取排版单元指定范围内字形的字符索引，该索引是相对于整个段落的偏移。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getStringIndices(range?: Range): Array<int>--><!--Device-Run-getStringIndices(range?: Range): Array<int>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要获取的字符索引范围，range.start表示范围开始的位置，range.end表示范围的长度，如果长度是0表示从范围range.start开始获取到渲染块结束。当range.end、range.start为负数，或者传入null、undefined时，该方法将返回undefined。不传该参数时，默认获取整个渲染块。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 返回每个字符的索引。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { text } from '@kit.ArkGraphics2D'

function textFunc() {
  let indices = runs[0].getStringIndices(); // 获取渲染块全部字符索引
  let indicesRange = runs[0].getStringIndices({start:1, end:2}); // 获取渲染块从起始位置1开始, 长度为2范围内的字符索引
  indicesRange = runs[0].getStringIndices({start:-1, end:2}); // -1是非法参数，将返回undefined
  indicesRange = runs[0].getStringIndices({start:0, end:-10}); // -10是非法参数，将返回undefined
  let indicesNull = runs[0].getStringIndices(null); // null是非法参数，将返回undefined
  let indicesUndefined = runs[0].getStringIndices(undefined); // undefined是非法参数，将返回undefined
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

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { text } from "@kit.ArkGraphics2D";

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
  let lines = paragraph.getTextLines();
  let runs = lines[0].getGlyphRuns();
  let indices = runs[0].getStringIndices({start:0, end:0}); // 获取渲染块全部字符索引
  let indicesRange = runs[0].getStringIndices({start:1, end:2}); // 获取渲染块从起始位置1开始, 长度为2范围内的字符索引
  indicesRange = runs[0].getStringIndices({start:-1, end:2}); // -1是非法参数，将返回undefined
  indicesRange = runs[0].getStringIndices({start:0, end:-10}); // -10是非法参数，将返回undefined
  let indicesUndefined = runs[0].getStringIndices(undefined); // undefined是非法参数，将返回undefined
}

@Entry
@Component
struct Index {
  fun: () => void = textFunc;
  build() {
    Column() {
      Button("Click").onClick((e: ClickEvent) => {
        this.fun();
      })
    }
  }
}
```

## getStringIndices

```TypeScript
getStringIndices(range?: Range): Array<int> | undefined
```

获取run对象中字形索引的范围，索引为相对于段落起始的偏移

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Run-getStringIndices(range?: Range): Array<int> | undefined--><!--Device-Run-getStringIndices(range?: Range): Array<int> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | range获取当前run的字形范围，其中start表示起始位置，end表示范围长度，如果长度为0，则获取从start到末尾的字形 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | The glyph indices or undefined. |

## getStringRange

```TypeScript
getStringRange(): Range
```

获取排版单元生成字形的字符范围。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getStringRange(): Range--><!--Device-Run-getStringRange(): Range-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 排版单元生成字形的字符范围，Range类型中的start表示字符范围的开始位置，该位置是相对于整个段落的索引，Range类型中的end表示字符范围的长度。 |

**示例：**

```TypeScript
let runStringRange = runs[0].getStringRange();
let location = runStringRange.start;
let length = runStringRange.end;
```

## getTextDirection

```TypeScript
getTextDirection(): TextDirection
```

获取该排版单元的文本方向。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getTextDirection(): TextDirection--><!--Device-Run-getTextDirection(): TextDirection-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回该排版单元的文本方向。 |

**示例：**

```TypeScript
let textDirection = runs[0].getTextDirection();
```

## getTextStyle

```TypeScript
getTextStyle(): TextStyle
```

获取当前绘制单元的样式属性信息

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getTextStyle(): TextStyle--><!--Device-Run-getTextStyle(): TextStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 当前绘制单元的样式属性对象 |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
// Index.ets
import { Entry, Component, Column, Button, ClickEvent} from '@ohos.arkui.component'
import { text } from "@kit.ArkGraphics2D"
import { common2D } from '@kit.ArkGraphics2D'

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
      let textColor = runStyle?.color;
      if (textColor != undefined) {
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
```

## getTypographicBounds

```TypeScript
getTypographicBounds(): TypographicBounds
```

获取该排版单元的排版边界，排版边界与排版字体、排版字号有关，与字符本身无关，例如字符串为" a b "，'a'字符前面有1个空格，'b'字符后面有1个空格，排版边界就包括行首和末尾空格的边界。 > **说明：** > > 示意图展示了字符串为" a b "的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > > 示意图展示了字符串为"j"或"E"的排版边界。 > > ! > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-getTypographicBounds(): TypographicBounds--><!--Device-Run-getTypographicBounds(): TypographicBounds-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 该排版单元的排版边界。 |

**示例：**

```TypeScript
let typographicBounds = runs[0].getTypographicBounds();
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

在画布上以(x, y)为左上角位置绘制排版单元。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Run-paint(canvas: drawing.Canvas, x: double, y: double): void--><!--Device-Run-paint(canvas: drawing.Canvas, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | drawing.Canvas | 是 | 绘制的目标 canvas。 |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 绘制的左上角位置的横坐标，浮点数，单位为物理像素px。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 绘制的左上角位置的纵坐标，浮点数，单位为物理像素px。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { drawing } from '@kit.ArkGraphics2D'
import { text } from '@kit.ArkGraphics2D'
import { common2D } from '@kit.ArkGraphics2D'
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
    let runs = lines[0].getGlyphRuns();
    runs[0].paint(canvas, 0, 0);
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

