# LayoutManager

布局管理器对象。 > **说明：** > > 文本内容变更后，需等待布局完成才可获取到最新的布局信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface LayoutManager--><!--Device-unnamed-export declare interface LayoutManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined
```

获取距离指定坐标最近的字符的位置信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined--><!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 相对于组件的横坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |
| y | double | 是 | 相对于组件的纵坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-textcommon-positionwithaffinity-i.md) | 字符的位置信息。当[LayoutManager]{ |

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: double, y: double, encoding?: TextEncoding): PositionWithAffinity | undefined
```

根据指定编码类型，获取距离指定坐标最近的字符位置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: double, y: double, encoding?: TextEncoding): PositionWithAffinity | undefined--><!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: double, y: double, encoding?: TextEncoding): PositionWithAffinity | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 相对于组件的横坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |
| y | double | 是 | 相对于组件的纵坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |
| encoding | [TextEncoding](arkts-arkui-textcommon-textencoding-e.md) | 否 | 字符位置使用的编码类型，默认值为TextEncoding.TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-textcommon-positionwithaffinity-i.md) | 字符的位置信息。当[LayoutManager]{ |

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined
```

根据给定的文本字形范围来获取范围内的字符范围，以及实际的字形范围。例如文本为"世界Hello"，其字形索引范围为[0, 7]，一个汉字占三个字符，所以其对应的字符索引范围为[0, 11]。如果指定的索引范围是[0, 11]，但 字形一共只有7个，所以实际的字形索引范围是[0, 7]。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined--><!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textcommon-textrange-i.md) | 是 | 文本的字形范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textcommon-textrange-i.md)&gt; | 数组中含有两个元素，第一个元素是字符范围，第二个元素是实际的字形范围，当返回的范围是异常值时，范围内元素为-1。当 [LayoutManager]{ |

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

根据指定编码类型和文本字形范围，获取字符范围以及实际的字形范围。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined--><!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textcommon-textrange-i.md) | 是 | 文本的字形范围。 |
| encoding | [TextEncoding](arkts-arkui-textcommon-textencoding-e.md) | 否 | 字符范围使用的编码类型，默认值为TextEncoding.TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textcommon-textrange-i.md)&gt; | 数组中含有两个元素，第一个元素是字符范围，第二个元素是实际的字形范围，当返回的范围是异常值时，范围内元素为-1。当 [LayoutManager]{ |

## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined
```

获取较为接近给定坐标的字形的位置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getGlyphPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined--><!--Device-LayoutManager-getGlyphPositionAtCoordinate(x: double, y: double): PositionWithAffinity | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 相对于组件的横坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |
| y | double | 是 | 相对于组件的纵坐标。&lt;br/&gt;单位：[px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-textcommon-positionwithaffinity-i.md) | 字形位置信息。 |

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined
```

根据给定的文本字符范围来获取范围内的字形范围，以及实际的字符范围。例如文本为"世界Hello"，其中文本"世"的字形索引范围为[0, 1]，一个汉字占三个字符，所以其对应的字符索引范围为[0, 3]。如果指定的字符索引范围是 [0, 1]，但无法解析出三分之一个汉字，所以实际的字符索引范围是[0, 3]。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined--><!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textcommon-textrange-i.md) | 是 | 文本的字符范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textcommon-textrange-i.md)&gt; | 数组中含有两个元素，第一个元素是字形范围，第二个元素是实际的字符范围，当返回的范围是异常值时，范围内元素为-1。当 [LayoutManager]{ |

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

根据指定编码类型和文本字符范围，获取字形范围以及实际的字符范围。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined--><!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textcommon-textrange-i.md) | 是 | 文本的字符范围。 |
| encoding | [TextEncoding](arkts-arkui-textcommon-textencoding-e.md) | 否 | 字符范围使用的编码类型，默认值为TextEncoding.TEXT_ENCODING_UTF8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textcommon-textrange-i.md)&gt; | 数组中含有两个元素，第一个元素是字形范围，第二个元素是实际的字符范围，当返回的范围是异常值时，范围内元素为-1。当 [LayoutManager]{ |

## getLineCount

```TypeScript
getLineCount(): int | undefined
```

获取组件内容的总行数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getLineCount(): int | undefined--><!--Device-LayoutManager-getLineCount(): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 组件内容的总行数。 |

## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: int): LineMetrics | undefined
```

ArkTS-Sta: getLineMetrics(lineNumber: int): LineMetrics | undefined 获取指定行的行信息、文本样式信息、以及字体属性信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getLineMetrics(lineNumber: int): LineMetrics | undefined--><!--Device-LayoutManager-getLineMetrics(lineNumber: int): LineMetrics | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineNumber | int | 是 | 行号，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | 行信息、文本样式信息、以及字体属性信息。&lt;br/&gt;当行号小于0或超出实际行，返回无效值。 |

## getRectsForRange

```TypeScript
getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox> | undefined
```

获取给定的矩形区域宽度以及矩形区域高度的规格下，文本中任意区间范围内的字符或占位符所占的绘制区域信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutManager-getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox> | undefined--><!--Device-LayoutManager-getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [TextRange](arkts-arkui-textcommon-textrange-i.md) | 是 | 需要获取的区域的文本区间。 |
| widthStyle | [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | 是 | 返回的矩形区域的宽度的规格。 |
| heightStyle | [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | 是 | 返回的矩形区域的高度的规格。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextBox](arkts-arkui-textbox-t.md)&gt; | 矩形区域数组。 |

