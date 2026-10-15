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

<!--Device-unnamed-declare interface LayoutManager--><!--Device-unnamed-declare interface LayoutManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Objects to Import

Take the Text component as an example. For a complete example, see [Example 10: Obtaining Text Information](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md) of the Text component.

```ts
controller: TextController = new TextController();
let layoutManager: LayoutManager = this.controller.getLayoutManager();
```

<a id="getcharacterpositionatcoordinate1"></a>

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(x: number, y: number): PositionWithAffinity | undefined
```

Obtains the position information of the character closest to the specified coordinate.

> **NOTE:** 
> 
> - After the text content changes, wait until the layout is complete before obtaining the latest position information.
> 
> - The character position returned by this API is the UTF-8 encoding offset.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: number, y: number): PositionWithAffinity | undefined--><!--Device-LayoutManager-getCharacterPositionAtCoordinate(x: number, y: number): PositionWithAffinity | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Y coordinate relative to the component.<br>Unit: px |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) &#124; undefined | Character position information. When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to the component, this API returns undefined. |

<a id="getcharacterpositionatcoordinate2"></a>

## getCharacterPositionAtCoordinate

```TypeScript
getCharacterPositionAtCoordinate(
    x: number, y: number, encoding?: TextEncoding): PositionWithAffinity | undefined
```

Obtains the position information of the character closest to the specified coordinate based on the specified encoding type.

Compared with [getCharacterPositionAtCoordinate](#getcharacterpositionatcoordinate1), this API supports specifying the encoding type (UTF-8 or UTF-16) used for the character position through the encoding parameter.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest position
> information.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LayoutManager-getCharacterPositionAtCoordinate(    x: number, y: number, encoding?: TextEncoding): PositionWithAffinity | undefined--><!--Device-LayoutManager-getCharacterPositionAtCoordinate(    x: number, y: number, encoding?: TextEncoding): PositionWithAffinity | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Vertical coordinate relative to the component.<br>Unit: px |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used by the character position. In UTF-8 encoding, the character position is in bytes; in UTF-16 encoding, the character position is in UTF-16 code units.<br>Default value: TextEncoding.TEXT_ENCODING_UTF8. |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) &#124; undefined | Character position. Returns **undefined** when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component. |

<a id="getcharacterrangeforglyphrange1"></a>

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined
```

Obtains the character range and the actual glyph range based on the specified text glyph range. The character offset of this API is UTF-8 encoding.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest character range
> information.
> Take the text "世界Hello" as an example. The correspondence between the glyph index and the character index under
> UTF-8 encoding is as follows:

| Text | 世 | 界 | H | e | l | l | o |  
|---|---|---|---|---|---|---|---|  
| Glyph Index Range | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |
| Character Index Range (UTF-8) | [0, 3] | [3, 6] | [6, 7] | [7, 8] | [8, 9] | [9, 10] | [10, 11] |

Its glyph index range is [0, 7]. Since a Chinese character occupies 3 bytes, its corresponding character index range is [0, 11]. If the specified glyph index range is [0, 11], but there are only 7 glyphs in total, the actual glyph index range is [0, 7].

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined--><!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange): Array<TextRange> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Glyph range of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | The array contains two elements: the first element is the character range, and the second element is the actual glyph range. <br>When the returned range is an abnormal value, the elements in the range are -1. <br>When the [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component, this API returns undefined. |

<a id="getcharacterrangeforglyphrange2"></a>

## getCharacterRangeForGlyphRange

```TypeScript
getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

Obtains the character range and the actual glyph range based on the specified encoding type and text glyph range.

Compared with [getCharacterRangeForGlyphRange](#getcharacterrangeforglyphrange1), this API supports specifying the encoding type (UTF-8 or UTF-16) used for the character range through the **encoding** parameter.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest character range
> information.
> Take the text "世界Hello" as an example. The correspondence between the glyph index and the character index under
> different encoding types is as follows:

| Text | 世 | 界 | H | e | l | l | o |  
|---|---|---|---|---|---|---|---|  
| Glyph Index Range | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |
| Character Index Range (UTF-8) | [0, 3] | [3, 6] | [6, 7] | [7, 8] | [8, 9] | [9, 10] | [10, 11] |
| Character Index Range (UTF-16) | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |

Under UTF-8 encoding, its glyph index range is [0, 7]. Since a Chinese character occupies 3 bytes, the corresponding character index range is [0, 11]. If the specified glyph index range exceeds the actual number of glyphs (for example, [0, 11]), since there are only 7 glyphs in total, the returned actual glyph index range is [0, 7].

Under UTF-16 encoding, the character index is measured in UTF-16 code units. A BMP character (such as "世") occupies 1 code unit (2 bytes), and a supplementary plane character (such as an emoji) occupies 2 code units (a 4-byte surrogate pair). Its glyph index range is [0, 7], and the corresponding character index range is [0, 7]. If the specified glyph index range exceeds the actual number of glyphs (for example, [0, 10]), since there are only 7 glyphs in total, the returned actual glyph index range is [0, 7].

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined--><!--Device-LayoutManager-getCharacterRangeForGlyphRange(glyphRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glyphRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Glyph range of the text. |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used for the character range. With UTF-8 encoding, the character index is in bytes; with UTF-16 encoding, the character index is in UTF-16 code units.<br>Default value: TextEncoding.TEXT_ENCODING_UTF8 |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | The array contains two elements. The first element is the character range, and the second element is the actual glyph range. <br>When the returned range is an abnormal value, the elements in the range are -1. <br>When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component, this interface returns undefined. |

## getGlyphPositionAtCoordinate

```TypeScript
getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity
```

Obtains the position information of the character close to the given coordinate.

> **NOTE:** 
> 
> - This API actually obtains the UTF-16 character offset, rather than the glyph offset.
> 
> - After the text content changes, wait until the layout is complete before obtaining the latest position information.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LayoutManager-getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity--><!--Device-LayoutManager-getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Horizontal coordinate relative to the component.<br>Unit: px |
| y | number | Yes | Vertical coordinate relative to the component.<br>Unit: px |

**Return value:**

| Type | Description |
| --- | --- |
| [PositionWithAffinity](arkts-arkui-positionwithaffinity-i.md) | Character position information. When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component, an invalid value is returned. |

<a id="getglyphrangeforcharacterrange1"></a>

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined
```

Obtains the glyph range and the actual character range based on the specified text character range. The character offset of this API is in UTF-8 encoding.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest glyph range
> information.
> Take the text "世界Hello" as an example. The correspondence between the glyph index and the character index under
> UTF-8 encoding is as follows:

| Text | 世 | 界 | H | e | l | l | o |  
|---|---|---|---|---|---|---|---|  
| Glyph Index Range | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |
| Character Index Range (UTF-8) | [0, 3] | [3, 6] | [6, 7] | [7, 8] | [8, 9] | [9, 10] | [10, 11] |

The glyph index range of the character "世" is [0, 1]. Since a Chinese character occupies 3 bytes, its corresponding character index range is [0, 3]. If the specified character index range is [0, 1], it is impossible to parse one- third of a Chinese character, so the actual character index range is [0, 3].

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined--><!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange): Array<TextRange> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Character range of the text. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | The array contains two elements: the first element is the glyph range, and the second element is the actual character range. <br>When the returned range is an abnormal value, the elements in the range are -1. <br>When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component, this API returns undefined. |

<a id="getglyphrangeforcharacterrange2"></a>

## getGlyphRangeForCharacterRange

```TypeScript
getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined
```

Obtains the glyph range and the actual character range based on the specified encoding type and text character range.

Compared with [getGlyphRangeForCharacterRange](#getglyphrangeforcharacterrange1), this interface supports specifying the encoding type (UTF-8 or UTF-16) used for the character range through the encoding parameter.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest glyph range
> information.
> Take the text "世界Hello" as an example. The correspondence between the glyph index and the character index under
> different encoding types is as follows:

| Text | 世 | 界 | H | e | l | l | o |  
|---|---|---|---|---|---|---|---|  
| Glyph Index Range | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |
| Character Index Range (UTF-8) | [0, 3] | [3, 6] | [6, 7] | [7, 8] | [8, 9] | [9, 10] | [10, 11] |
| Character Index Range (UTF-16) | [0, 1] | [1, 2] | [2, 3] | [3, 4] | [4, 5] | [5, 6] | [6, 7] |

Under UTF-8 encoding, a Chinese character occupies 3 bytes. The glyph index range of "世" is [0, 1], and its corresponding character index range is [0, 3]. If the specified character index range is [0, 1], it is impossible to parse one-third of a Chinese character, so the actual character index range is [0, 3].

Under UTF-16 encoding, the character index is measured in UTF-16 code units. A BMP character (such as "世") occupies 1 code unit (2 bytes), and a supplementary plane character (such as an emoji) occupies 2 code units (a 4-byte surrogate pair). The glyph index range of "世" is [0, 1], and its corresponding character index range is [0, 1].

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined--><!--Device-LayoutManager-getGlyphRangeForCharacterRange(charRange: TextRange, encoding?: TextEncoding): Array<TextRange> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| charRange | [TextRange](arkts-arkui-textrange-i.md) | Yes | Character range of the text. |
| encoding | [TextEncoding](arkts-arkui-textencoding-e.md) | No | Encoding type used by the character range. In UTF-8 encoding, the character index is in bytes; in UTF-16 encoding, the character index is in UTF-16 code units.<br>Default value: TextEncoding.TEXT_ENCODING_UTF8 |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextRange](arkts-arkui-textrange-i.md)&gt; &#124; undefined | The array contains two elements. The first element is the glyph range, and the second element is the actual character range. <br>When the returned range is an abnormal value, the elements in the range are -1. <br>When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to the component, this interface will return undefined. |

## getLineCount

```TypeScript
getLineCount(): number
```

Obtains the total number of lines in the component.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest total number of
> lines.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LayoutManager-getLineCount(): number--><!--Device-LayoutManager-getLineCount(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of lines of the component content. Returns 0 when [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to the component. |

## getLineMetrics

```TypeScript
getLineMetrics(lineNumber: number): LineMetrics
```

Obtains the information about the specified line, including line metrics, text style information, and font properties.

> **NOTE:** 
> 
> After the text content changes, wait until the layout is complete before obtaining the latest line information.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LayoutManager-getLineMetrics(lineNumber: number): LineMetrics--><!--Device-LayoutManager-getLineMetrics(lineNumber: number): LineMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineNumber | number | Yes | Line number, ranging from 0 to the actual number of lines minus 1, starting from 0. If the line number is less than 0 or exceeds the actual number of lines, an invalid value is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [LineMetrics](arkts-arkui-linemetrics-t.md) | Line information, text style information, and font attribute information. <br>When the line number is less than 0 or exceeds the actual number of lines, an invalid value is returned. When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to the component, an invalid value is returned. |

## getRectsForRange

```TypeScript
getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>
```

Obtains the drawing area information of the characters or placeholders within any range of the text, based on the specified rectangle width and height styles.

> **NOTE:** 
> 
> - After the text content changes, wait until the layout is complete before obtaining the latest drawing area information.
> 
> - The [TextRange](arkts-arkui-textrange-i.md) of the **range** parameter is a UTF-16 character offset.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-LayoutManager-getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>--><!--Device-LayoutManager-getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array<TextBox>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](arkts-arkui-textrange-i.md) | Yes | Text range for which the drawing area is to be obtained. |
| widthStyle | [RectWidthStyle](arkts-arkui-rectwidthstyle-t.md) | Yes | Width specification of the returned rectangular area, used to control how the width of the returned rectangle is calculated. Different specification values affect the width boundary of the rectangle. |
| heightStyle | [RectHeightStyle](arkts-arkui-rectheightstyle-t.md) | Yes | Height specification of the returned rectangular area, used to control how the height of the returned rectangle is calculated. Different specification values affect the height boundary of the rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[TextBox](arkts-arkui-textbox-t.md)&gt; | Array of rectangular areas. When [LayoutManager](arkts-arkui-layoutmanager-i.md) is not bound to a component, an empty array is returned. |
