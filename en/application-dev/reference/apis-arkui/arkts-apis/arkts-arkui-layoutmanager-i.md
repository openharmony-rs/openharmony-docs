# LayoutManager

```TypeScript
declare interface LayoutManager
```

Implements a layout manager object.

> **NOTE:** 
> 
> After the text content is changed, you must wait for the layout to be completed before you can obtain the most up-
> to-date layout information.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: number, y: number): PositionWithAffinity | undefined
```

Obtains the position of the character nearest to the specified coordinate.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Y coordinate relative to the component.<br>Unit: px |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) &#124; undefined | Character position. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

<a id="getcharacterpositionatcoordinate-1"></a>

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(
    x: number, y: number, encoding?: TextEncoding): PositionWithAffinity | undefined
```

Obtains the position of the character nearest to the specified coordinate based on the specified encoding type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Y coordinate relative to the component.<br>Unit: px |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used for the character position. The default value is **TextEncoding.TEXT_ENCODING_UTF8**. |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) &#124; undefined | Character position. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined
```

Obtains the character range and the actual glyph range based on the specified glyph range. If a text contains two Chinese characters and five letters, the glyph index range of the text is [0, 7]. A Chinese character occupies three characters, so the corresponding character index range is [0, 11]. If the specified index range is [0, 11], but there are only seven glyphs, the actual glyph index range is [0, 7].

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Glyph range of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | Contains two elements: the first is the character range, and the second is the actual glyph range. When the returned range is invalid, the element in the range is **-1**. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

<a id="getcharacterrangeforglyphrange-1"></a>

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

Obtains the character range and the actual glyph range based on the specified glyph range and encoding type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Glyph range of the text. |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used for the character range. The default value is **TextEncoding.TEXT_ENCODING_UTF8**. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | Contains two elements: the first is the character range, and the second is the actual glyph range. When the returned range is invalid, the element in the range is **-1**. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity
```

Obtains the position of a glyph close to a given coordinate.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Y coordinate relative to the component.<br>Unit: px |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) | Glyph position. |

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined
```

Obtains the glyph range and the actual character range based on the specified character range. If the first glyph is a Chinese character, the glyph index range of the character is [0, 1]. A Chinese character occupies three characters, so the corresponding character index range is [0, 3]. If the specified character index range is [0, 1], one third of a Chinese character cannot be parsed, so the actual character index range is [0, 3].

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Character range of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | Contains two elements: the first is the glyph range, and the second is the actual character range. When the returned range is invalid, the element in the range is **-1**. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

<a id="getglyphrangeforcharacterrange-1"></a>

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

Obtains the glyph range and the actual character range based on the specified character range and encoding type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Character range of the text. |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used for the character range. The default value is **TextEncoding.TEXT_ENCODING_UTF8**. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | Contains two elements: the first is the glyph range, and the second is the actual character range. When the returned range is invalid, the element in the range is **-1**. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

## getLineCount

```TypeScript
getLineCount(): number
```

Obtains the total number of lines in the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of lines in the component. |

## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: number): LineMetrics
```

Obtains the information about the specified line, including line metrics, text style information, and font properties.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineNumber | number | Yes | Line number, which is zero-based. |

**Return value:**

| Type | Description |
| --- | --- |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | Information about the specified line, including line metrics, text style information, and font properties.<br>Returns an invalid value if the line number is less than 0 or exceeds the actual number of lines. |

## getRectsForRange

```TypeScript
getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>
```

Obtains the drawing area information of the characters or placeholders within any range of the text, based on the specified rectangle width and height styles.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](arkts-arkui-textrange-i.md) | Yes | Text range for which the drawing area is to be obtained. |
| widthStyle | [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | Yes | Width style of the rectangle. |
| heightStyle | [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | Yes | Height style of the rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBox](arkts-arkui-textbox-t.md)&gt; | Array of drawing rectangles. |
