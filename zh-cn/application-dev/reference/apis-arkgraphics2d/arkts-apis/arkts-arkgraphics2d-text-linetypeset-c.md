# LineTypeset

保存文本内容及样式的载体，可用于计算单行排版信息。 下列API示例中都需先使用[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md#ParagraphBuilder)类的 [buildLineTypeset()](arkts-arkgraphics2d-text-paragraphbuilder-c.md#buildLineTypeset)接口获取到LineTypeset对象实例，再通过此实例调用对应方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-text-class LineTypeset--><!--Device-text-class LineTypeset-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## createLine

```TypeScript
createLine(startIndex: int, count: int): TextLine
```

根据指定的排版区间生成文本行对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineTypeset-createLine(startIndex: int, count: int): TextLine--><!--Device-LineTypeset-createLine(startIndex: int, count: int): TextLine-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startIndex | int | 是 | 开始计算排版的起始位置，整数，取值范围为[0, 文本字符总数)。 |
| count | int | 是 | 从指定起始位置开始进行排版的字符个数，取值为 [0,文本字符总数)的整数，startIndex和count之和不能大于文本字符总数。当count为0时，表示排版区间为[startIndex, 文本的最后一个字符位置]。 可以先使用[getLineBreak](#getLineBreak)获取合理的排版字符总数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextLine](arkts-arkgraphics2d-text-textline-c.md) | 根据文本区间字符生成的TextLine对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
let startIndex = 0;
let width = 100.0;
let count = lineTypeset.getLineBreak(startIndex, width);
let line : text.TextLine = lineTypeset.createLine(startIndex, count);
```

## getLineBreak

```TypeScript
getLineBreak(startIndex: int, width: double): int
```

计算在限定宽度下，从指定位置开始可以排版的字符数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineTypeset-getLineBreak(startIndex: int, width: double): int--><!--Device-LineTypeset-getLineBreak(startIndex: int, width: double): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startIndex | int | 是 | 开始计算排版的起始位置（包括起始位置）。取值范围需要为[0,文本字符总数）的整数，当参数超出范围时抛出异常。 |
| width | double | 是 | 可用于排版的宽度，大于0的浮点数，单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回在限定排版宽度下，从指定位置开始可排版的字符总数，取值为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
let startIndex = 0;
let width = 100.0;
let count = lineTypeset.getLineBreak(startIndex, width);
```

