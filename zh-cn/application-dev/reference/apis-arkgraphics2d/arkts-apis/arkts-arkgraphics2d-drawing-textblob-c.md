# TextBlob

由一个或多个具有相同字体的字符组成的字块。

> **说明：**  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

<!--Device-drawing-class TextBlob--><!--Device-drawing-class TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## bounds

```TypeScript
bounds(): common2D.Rect
```

获取文字边界框的矩形区域。

**起始版本：** 11

<!--Device-TextBlob-bounds(): common2D.Rect--><!--Device-TextBlob-bounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Rectangular bounding box. |

## makeFromPosText

```TypeScript
static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob
```

使用文本创建TextBlob对象，TextBlob对象中每个字形的坐标由points中对应的坐标信息决定。

**起始版本：** 12

<!--Device-TextBlob-static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob--><!--Device-TextBlob-static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| len | number | 是 | 字形个数，由[countText](arkts-arkgraphics2d-drawing-font-c.md#counttext-1)获取，该参数为整数。 |
| points | common2D.Point[] | 是 | 点数组，用于指定每个字形的坐标，长度必须为len。 |
| font | [Font](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 字型对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## makeFromRunBuffer

```TypeScript
static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob
```

基于RunBuffer信息创建TextBlob对象。

**起始版本：** 11

<!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob--><!--Device-TextBlob-static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<TextBlobRunBuffer> | 是 | TextBlobRunBuffer数组。 |
| font | [Font](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 字型对象。 |
| bounds | common2D.Rect | 否 | 可选，如果不设置，则无边界框。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## makeFromString

```TypeScript
static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob
```

将string类型的值转化成TextBlob对象。

**起始版本：** 11

<!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob--><!--Device-TextBlob-static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 绘制字形的文本内容。 |
| font | [Font](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 字型对象。 |
| encoding | [TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | 否 | 编码类型，默认值为TEXT_ENCODING_UTF8。当前只有TEXT_ENCODING_UTF8生效，其余编码类型也会被视为TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | TextBlob对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## uniqueID

```TypeScript
uniqueID(): number
```

获取该TextBlob对象的唯一的非零标识符。

**起始版本：** 12

<!--Device-TextBlob-uniqueID(): long--><!--Device-TextBlob-uniqueID(): long-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回TextBlob对象的唯一的非零标识符。 |

