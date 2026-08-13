# TextBlob

TextBlob是由一个或多个具有相同字型的字符组成的字块。支持通过文本、字符串、RunBuffer等多种方式创建字形集合，适用于需要批量渲染文本或获取文字边界框的场景。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-class TextBlob--><!--Device-drawing-class TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## bounds

```TypeScript
bounds(): common2D.Rect
```

获取文字边界框的矩形区域。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-TextBlob-bounds(): common2D.Rect--><!--Device-TextBlob-bounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | 文字边界框的矩形区域。 |

## bounds

```TypeScript
bounds(): common2D.Rect | undefined
```

获取文字边界框的矩形区域。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextBlob-bounds(): common2D.Rect | undefined--><!--Device-TextBlob-bounds(): common2D.Rect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | 文字边界框的矩形区域。创建失败时返回undefined。 |

## makeFromPosText

```TypeScript
static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob
```

使用文本创建TextBlob对象，其中每个字形的坐标由points中对应的坐标信息决定。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob--><!--Device-TextBlob-static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| len | number | 是 | 字形个数，由[countText](arkts-arkgraphics2d-drawing-font-c.md#countText)获取，该参数为整数。 |
| points | common2D.Point[] | 是 | 点数组，用于指定每个字形的坐标，长度必须为len。 |
| font | Font | 是 | 字型对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | 由文本和坐标信息创建的TextBlob对象，用于后续绘制字形。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromPosText

```TypeScript
static makeFromPosText(text: string, len: int, points: common2D.Point[], font: Font): TextBlob | undefined
```

使用文本创建TextBlob对象，其中每个字形的坐标由points中对应的坐标信息决定。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromPosText(text: string, len: int, points: common2D.Point[], font: Font): TextBlob | undefined--><!--Device-TextBlob-static makeFromPosText(text: string, len: int, points: common2D.Point[], font: Font): TextBlob | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| len | int | 是 | 字形个数，由[countText](arkts-arkgraphics2d-drawing-font-c.md#countText)获取，该参数为整数。 |
| points | common2D.Point[] | 是 | 点数组，用于指定每个字形的坐标，长度必须为len。 |
| font | Font | 是 | 字型对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | 由文本和坐标信息创建的TextBlob对象，用于后续绘制字形。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromRunBuffer

```TypeScript
static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob
```

基于RunBuffer信息创建TextBlob对象。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob--><!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | Array&lt;[TextBlobRunBuffer](arkts-arkgraphics2d-drawing-textblobrunbuffer-i.md)&gt; | 是 | TextBlobRunBuffer数组，每个元素包含字形ID及位置坐标信息。 |
| font | Font | 是 | 字型对象。 |
| bounds | common2D.Rect | 否 | 文字边界框的矩形区域；如果不设置，则不预设边界框。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | 基于RunBuffer创建的TextBlob对象，用于后续绘制字形。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromRunBuffer

```TypeScript
static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob | undefined
```

基于RunBuffer信息创建TextBlob对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob | undefined--><!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | Array&lt;[TextBlobRunBuffer](arkts-arkgraphics2d-drawing-textblobrunbuffer-i.md)&gt; | 是 | TTextBlobRunBuffer数组，每个元素包含字形ID及位置坐标信息。 |
| font | Font | 是 | 字型对象。 |
| bounds | common2D.Rect | 否 | 文字边界框的矩形区域；如果不设置，则不预设边界框。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | 基于RunBuffer创建的TextBlob对象，用于后续绘制字形。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromString

```TypeScript
static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob
```

根据指定的编码类型和字型，使用string类型的值创建TextBlob对象。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob--><!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| font | Font | 是 | 字型对象。 |
| encoding | TextEncoding | 否 | 编码类型，默认值为TEXT_ENCODING_UTF8。当前只有TEXT_ENCODING_UTF8生效，其余编码类型也会被视为 TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob对象，用于后续绘制字形。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## makeFromString

```TypeScript
static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob | undefined
```

根据指定的编码类型和字型，使用string类型的值创建TextBlob对象

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob | undefined--><!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| font | Font | 是 | 字型对象。 |
| encoding | TextEncoding | 否 | 编码类型，默认值为TEXT_ENCODING_UTF8。当前只有TEXT_ENCODING_UTF8生效，其余编码类型也会被视为 TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob对象，用于后续绘制字形。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |

## uniqueID

```TypeScript
uniqueID(): long
```

获取该TextBlob对象的唯一非零标识符。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TextBlob-uniqueID(): long--><!--Device-TextBlob-uniqueID(): long-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回TextBlob对象的唯一的非零标识符。 |

