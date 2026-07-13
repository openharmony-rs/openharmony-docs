# LayoutManager

布局管理器对象。

> **说明：**
>
> 文本内容变更后，需等待布局完成才可获取到最新的布局信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: number, y: number): PositionWithAffinity | undefined
```

获取距离指定坐标最近的字符的位置信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 相对于组件的横坐标。<br/>单位：[px](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |
| y | number | 是 | 相对于组件的纵坐标。<br/>单位：[px](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PositionWithAffinity | Character position. Returns **undefined** when[LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined
```

根据给定的文本字形范围来获取范围内的字符范围，以及实际的字形范围。例如文本为"世界Hello"，其字形索引范围为[0, 7]，一个汉字占三个字符，所以其对应的字符索引范围为[0, 11]。如果指定的索引范围是[0, 11]，但字形
一共只有7个，所以实际的字形索引范围是[0, 7]。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphRange | TextRange | 是 | 文本的字形范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextRange&gt; | Contains two elements: the first is the character range, and the secondis the actual glyph range. When the returned range is invalid, the element in the range is **-1**. Returns**undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity
```

获取较为接近给定坐标的字形的位置信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 相对于组件的横坐标。<br/>单位：[px](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |
| y | number | 是 | 相对于组件的纵坐标。<br/>单位：[px](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PositionWithAffinity | 字形位置信息。 |

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined
```

根据给定的文本字符范围来获取范围内的字形范围，以及实际的字符范围。例如文本为"世界Hello"，其中文本"世"的字形索引范围为[0, 1]，一个汉字占三个字符，所以其对应的字符索引范围为[0, 3]。如果指定的字符索引范围是
[0, 1]，但无法解析出三分之一个汉字，所以实际的字符索引范围是[0, 3]。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| charRange | TextRange | 是 | 文本的字符范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextRange&gt; | Contains two elements: the first is the glyph range, and the second isthe actual character range. When the returned range is invalid, the element in the range is **-1**. Returns**undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getLineCount

```TypeScript
getLineCount(): number
```

获取组件内容的总行数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 组件内容的总行数。 |

## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: number): LineMetrics
```

获取指定行的行信息、文本样式信息、以及字体属性信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lineNumber | number | 是 | 行号，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LineMetrics | 行信息、文本样式信息、以及字体属性信息。<br/>当行号小于0或超出实际行，返回无效值。 |

## getRectsForRange

```TypeScript
getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>
```

获取给定的矩形区域宽度以及矩形区域高度的规格下，文本中任意区间范围内的字符或占位符所占的绘制区域信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | TextRange | 是 | 需要获取的区域的文本区间。 |
| widthStyle | RectWidthStyle | 是 | 返回的矩形区域的宽度的规格。 |
| heightStyle | RectHeightStyle | 是 | 返回的矩形区域的高度的规格。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextBox&gt; | 矩形区域数组。 |

