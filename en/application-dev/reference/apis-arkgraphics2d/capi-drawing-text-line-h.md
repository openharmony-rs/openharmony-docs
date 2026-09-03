# drawing_text_line.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=26f1a11070a0259938fa2e9b40098b1fb904b6e8 translatedAt=2026-07-25T02:03:49.732Z pushedAt=2026-07-25T09:53:18.955Z -->

## Overview

This file declares the capabilities for obtaining the character position in a text line, obtaining the run information, and truncating text by line.

**File to include**: <native_drawing/drawing_text_line.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_Array* OH_Drawing_TypographyGetTextLines(OH_Drawing_Typography* typography)](#oh_drawing_typographygettextlines) | - | Obtains the array of text lines in a typography object. This array contains one or more text line objects. Release this pointer by calling [OH_Drawing_DestroyTextLines](capi-drawing-text-line-h.md#oh_drawing_destroytextlines) when this object is no longer needed.|
| [void OH_Drawing_DestroyTextLines(OH_Drawing_Array* lines)](#oh_drawing_destroytextlines) | - | Releases the memory occupied by a text line array.|
| [void OH_Drawing_DestroyTextLine(OH_Drawing_TextLine* line)](#oh_drawing_destroytextline) | - | Releases the memory of a single text line object. Only the memory of a text line object that is independently allocated can be released. The memory of a text line object obtained from a line array through [OH_Drawing_GetTextLineByIndex](capi-drawing-text-line-h.md#oh_drawing_gettextlinebyindex) cannot be released. |
| [OH_Drawing_TextLine* OH_Drawing_GetTextLineByIndex(OH_Drawing_Array* lines, size_t index)](#oh_drawing_gettextlinebyindex) | - | Obtains the text line object with the specified index in a text line array.|
| [double OH_Drawing_TextLineGetGlyphCount(OH_Drawing_TextLine* line)](#oh_drawing_textlinegetglyphcount) | - | Obtains the number of glyphs in a text line object.|
| [void OH_Drawing_TextLineGetTextRange(OH_Drawing_TextLine* line, size_t* start, size_t* end)](#oh_drawing_textlinegettextrange) | - | Obtains the range of the text in a text line object in the entire paragraph.|
| [OH_Drawing_Array* OH_Drawing_TextLineGetGlyphRuns(OH_Drawing_TextLine* line)](#oh_drawing_textlinegetglyphruns) | - | Obtains the array of text rendering units [OH_Drawing_Run](capi-drawing-oh-drawing-run.md) in the text line object. |
| [void OH_Drawing_DestroyRuns(OH_Drawing_Array* runs)](#oh_drawing_destroyruns) | - | Releases the memory occupied by a glyph run array.|
| [OH_Drawing_Run* OH_Drawing_GetRunByIndex(OH_Drawing_Array* runs, size_t index)](#oh_drawing_getrunbyindex) | - | Obtains the glyph run object with the specified index in a glyph run array.|
| [void OH_Drawing_TextLinePaint(OH_Drawing_TextLine* line, OH_Drawing_Canvas* canvas, double x, double y)](#oh_drawing_textlinepaint) | - | Paints a text line on the canvas with the coordinate point (x, y) as the upper left corner.|
| [OH_Drawing_TextLine* OH_Drawing_TextLineCreateTruncatedLine(OH_Drawing_TextLine* line, double width, int mode, const char* ellipsis)](#oh_drawing_textlinecreatetruncatedline) | - | Creates a truncated text line object. Based on the passed width, truncation mode, and truncation mark string, truncates the original text line, inserts the specified mark string at the truncation position, and generates and returns a new independent text line object. The original text is not affected. |
| [double OH_Drawing_TextLineGetTypographicBounds(OH_Drawing_TextLine* line, double* ascent, double* descent, double* leading)](#oh_drawing_textlinegettypographicbounds) | - | Obtains the typographic bounds of the text line object. The typographic bounds of a text line are related to the typographic font and typographic font size, and are independent of the characters themselves.<br>For example, for the string " a b ", there is one space before the 'a' character and one space after the 'b' character. The typographic bounds include the boundaries of the leading and trailing spaces. For example, for the string "j" or "E", the typographic bounds are the same, i.e., independent of the characters themselves.<br>The text height can be calculated using height = ascent + descent + leading. |
| [OH_Drawing_Rect* OH_Drawing_TextLineGetImageBounds(OH_Drawing_TextLine* line)](#oh_drawing_textlinegetimagebounds) | - | Obtains the image bounds of the text line object. The image bounds of a text line are related to the typographic font, typographic font size, and the characters themselves, and are equivalent to the visual bounds.<br>For example, for the string " a b ", there is one space before the 'a' character and one space after the 'b' character. The user can only see "a b" on the UI, so the image bounds are the bounds excluding the leading and trailing spaces.<br>For example, for the string "j" or "E", the visual bounds are different, i.e., related to the characters themselves. The visual bound width of the string "j" is smaller than that of the string "E", and the visual bound height of the string "j" is greater than that of the string "E". |
| [double OH_Drawing_TextLineGetTrailingSpaceWidth(OH_Drawing_TextLine* line)](#oh_drawing_textlinegettrailingspacewidth) | - | Obtains the width of the spaces at the end of a text line object.|
| [int32_t OH_Drawing_TextLineGetStringIndexForPosition(OH_Drawing_TextLine* line, OH_Drawing_Point* point)](#oh_drawing_textlinegetstringindexforposition) | - | Obtains the string index at the specified position in the text line object. |
| [double OH_Drawing_TextLineGetOffsetForStringIndex(OH_Drawing_TextLine* line, int32_t index)](#oh_drawing_textlinegetoffsetforstringindex) | - | Obtains the offset of a character with the specified index in a text line object.|
| [typedef bool (\*Drawing_CaretOffsetsCallback)(double offset, int32_t index, bool leadingEdge)](#drawing_caretoffsetscallback) | Drawing_CaretOffsetsCallback | Defines a custom callback used to receive the offset and index of each character in a text line object as its parameters.|
| [void OH_Drawing_TextLineEnumerateCaretOffsets(OH_Drawing_TextLine* line, Drawing_CaretOffsetsCallback callback)](#oh_drawing_textlineenumeratecaretoffsets) | - | Enumerates the offset and index of each character in a text line object and passes them to a custom callback function. You can use the offset and index array for other operations.|
| [double OH_Drawing_TextLineGetAlignmentOffset(OH_Drawing_TextLine* line, double alignmentFactor, double alignmentWidth)](#oh_drawing_textlinegetalignmentoffset) | - | Obtains the offset of a text line object after alignment based on the alignment factor and alignment width.|

## Function Description

### OH_Drawing_TypographyGetTextLines()

```c
OH_Drawing_Array* OH_Drawing_TypographyGetTextLines(OH_Drawing_Typography* typography)
```

**Description**

Obtains the array of text lines in a typography object. This array contains one or more text line objects. Release this pointer by calling [OH_Drawing_DestroyTextLines](capi-drawing-text-line-h.md#oh_drawing_destroytextlines) when this object is no longer needed.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Typography](capi-drawing-oh-drawing-typography.md)* typography | Pointer to the [OH_Drawing_Typography](capi-drawing-oh-drawing-typography.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* | Pointer to the text line array [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). Returns NULL when typography is NULL. |

### OH_Drawing_DestroyTextLines()

```c
void OH_Drawing_DestroyTextLines(OH_Drawing_Array* lines)
```

**Description**

Releases the memory occupied by a text line array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* lines | Pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|

### OH_Drawing_DestroyTextLine()

```c
void OH_Drawing_DestroyTextLine(OH_Drawing_TextLine* line)
```

**Description**

Releases the memory of a single text line object. Only the memory of a text line object that is independently allocated can be released. The memory of a text line object obtained from a line array through [OH_Drawing_GetTextLineByIndex](capi-drawing-text-line-h.md#oh_drawing_gettextlinebyindex) cannot be released.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|

### OH_Drawing_GetTextLineByIndex()

```c
OH_Drawing_TextLine* OH_Drawing_GetTextLineByIndex(OH_Drawing_Array* lines, size_t index)
```

**Description**

Obtains the text line object with the specified index in a text line array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* lines | Pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| size_t index | Index of the text line array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) text line object at the specified index. Returns NULL if lines is NULL or the index is out of bounds. |

### OH_Drawing_TextLineGetGlyphCount()

```c
double OH_Drawing_TextLineGetGlyphCount(OH_Drawing_TextLine* line)
```

**Description**

Obtains the number of glyphs in a text line object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| double | Returns the number of glyphs in the text line object.|

### OH_Drawing_TextLineGetTextRange()

```c
void OH_Drawing_TextLineGetTextRange(OH_Drawing_TextLine* line, size_t* start, size_t* end)
```

**Description**

Obtains the range of the text in a text line object in the entire paragraph.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| size_t* start | Pointer to the start of the range.|
| size_t* end | Pointer to the end of the range.|

### OH_Drawing_TextLineGetGlyphRuns()

```c
OH_Drawing_Array* OH_Drawing_TextLineGetGlyphRuns(OH_Drawing_TextLine* line)
```

**Description**

Obtains the array of text rendering units [OH_Drawing_Run](capi-drawing-oh-drawing-run.md) in the text line object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* | Pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) array of text rendering units [OH_Drawing_Run](capi-drawing-oh-drawing-run.md). When the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) is no longer needed, please use the [OH_Drawing_DestroyRuns](capi-drawing-text-line-h.md#oh_drawing_destroyruns) API to release the pointer of the object. |

### OH_Drawing_DestroyRuns()

```c
void OH_Drawing_DestroyRuns(OH_Drawing_Array* runs)
```

**Description**

Releases the memory occupied by a glyph run array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* runs | Pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) array, which holds multiple [OH_Drawing_Run](capi-drawing-oh-drawing-run.md) objects.|

### OH_Drawing_GetRunByIndex()

```c
OH_Drawing_Run* OH_Drawing_GetRunByIndex(OH_Drawing_Array* runs, size_t index)
```

**Description**

Obtains the glyph run object with the specified index in a glyph run array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* runs | Pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) array, which holds multiple [OH_Drawing_Run](capi-drawing-oh-drawing-run.md) objects.|
| size_t index | Index of the glyph run array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Run](capi-drawing-oh-drawing-run.md)* | Pointer to the text rendering unit object [OH_Drawing_Run](capi-drawing-oh-drawing-run.md) at the specified index. NULL is returned if runs is NULL or the index is out of bounds. |

### OH_Drawing_TextLinePaint()

```c
void OH_Drawing_TextLinePaint(OH_Drawing_TextLine* line, OH_Drawing_Canvas* canvas, double x, double y)
```

**Description**

Paints a text line on the canvas with the coordinate point (x, y) as the upper left corner.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the target canvas for drawing, which is an [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md). |
| double x | Horizontal coordinate of the upper left corner, in px.|
| double y | Vertical coordinate of the upper left corner, in px.|

### OH_Drawing_TextLineCreateTruncatedLine()

```c
OH_Drawing_TextLine* OH_Drawing_TextLineCreateTruncatedLine(OH_Drawing_TextLine* line, double width, int mode, const char* ellipsis)
```

**Description**

Creates a truncated text line object. Truncates the original text line based on the specified width, truncation type, and truncation mark string, inserts the specified mark string at the truncation position, and generates and returns a new independent text line object. The original text is not affected.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| double width | Width of the truncated line, in physical pixels (px). |
| int mode | Truncation type. The value is an enumerated value of [OH_Drawing_EllipsisModal](capi-drawing-text-typography-h.md#oh_drawing_ellipsismodal). Currently, only **ELLIPSIS_MODAL_HEAD** and **ELLIPSIS_MODAL_TAIL** are supported.|
| const char* ellipsis | Pointer to the string used to mark a truncation.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* | Pointer to the truncated text line object [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md). NULL is returned when line or ellipsis is NULL. Please use [OH_Drawing_DestroyTextLine](capi-drawing-text-line-h.md#oh_drawing_destroytextline) to release the object's memory when it is no longer needed. |

### OH_Drawing_TextLineGetTypographicBounds()

```c
double OH_Drawing_TextLineGetTypographicBounds(OH_Drawing_TextLine* line, double* ascent, double* descent, double* leading)
```

**Description**

Obtains the typographic bounds of the text line object. The typographic bounds of a text line are related to the typographic font and typographic font size, and are independent of the characters themselves.<br>For example, for the string " a b ", where there is one space before the 'a' character and one space after the 'b' character, the typographic bounds include the bounds of the leading and trailing spaces. For example, for the string "j" or "E", the typographic bounds are the same, i.e., independent of the characters themselves.<br>The text height can be calculated using height = ascent + descent + leading.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the text line object [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md). |
| double* ascent | Pointer to the ascent height of the text line object. The unit is physical pixel. |
| double* descent | Pointer to the descent height of the text line object. The unit is physical pixel. |
| double* leading | Pointer to the leading of the text line object. The unit is physical pixel. |

**Returns**

| Type| Description|
| -- | -- |
| double | Total width of the typographic bounds, in physical pixels. |

### OH_Drawing_TextLineGetImageBounds()

```c
OH_Drawing_Rect* OH_Drawing_TextLineGetImageBounds(OH_Drawing_TextLine* line)
```

**Description**

Obtains the image bounds of the text line object. The image bounds of a text line are related to the typographic font, typographic font size, and the characters themselves, and are equivalent to the visual bounds.<br>For example, for the string " a b ", where there is one space before the 'a' character and one space after the 'b' character, the user can only see "a b" on the UI, and the image bounds are the bounds excluding the leading and trailing spaces.<br>For example, for the string "j" or "E", the visual bounds are different, i.e., related to the characters themselves. The visual bounds width of the string "j" is smaller than that of the string "E", and the visual bounds height of the string "j" is greater than that of the string "E".

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* | Pointer to the image bounds [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) of the text line object. Returns NULL when the passed-in line is NULL. When the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) is no longer needed, please use the [OH_Drawing_RectDestroy](capi-drawing-rect-h.md#oh_drawing_rectdestroy) API to release the pointer of the object. |

### OH_Drawing_TextLineGetTrailingSpaceWidth()

```c
double OH_Drawing_TextLineGetTrailingSpaceWidth(OH_Drawing_TextLine* line)
```

**Description**

Obtains the width of the spaces at the end of a text line object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| double | Width of the trailing whitespace characters of the text line object, in physical pixels (px). |

### OH_Drawing_TextLineGetStringIndexForPosition()

```c
int32_t OH_Drawing_TextLineGetStringIndexForPosition(OH_Drawing_TextLine* line, OH_Drawing_Point* point)
```

**Description**

Obtains the string index at the specified position in the text line object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to the position [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) where the index is to be found. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns the index of the character. For example, for the string "abc", the index of "a" is 0, the index of "b" is 1, and the index of "c" is 2. If the specified position is at "a", then **0** is returned.|

### OH_Drawing_TextLineGetOffsetForStringIndex()

```c
double OH_Drawing_TextLineGetOffsetForStringIndex(OH_Drawing_TextLine* line, int32_t index)
```

**Description**

Obtains the offset of a character with the specified index in a text line object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| int32_t index | Index of the character.|

**Returns**

| Type| Description|
| -- | -- |
| double | Offset at the specified string index, in physical pixels (px). |

### Drawing_CaretOffsetsCallback()

```c
typedef bool (*Drawing_CaretOffsetsCallback)(double offset, int32_t index, bool leadingEdge)
```

**Description**

Defines a custom callback used to receive the offset and index of each character in a text line object as its parameters.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| double offset | Offset of each character in the text line object, in physical pixels (px). |
|  int32_t index | Index of each character in the text line object.|
| bool leadingEdge | Whether the cursor is at the leading edge of the character. The value **true** indicates the cursor is at the leading edge, and the offset does not include the character width; **false** indicates the cursor is at the trailing edge, and the offset includes the character width. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether to stop calling the callback. **true** means to stop; **false** otherwise.|

### OH_Drawing_TextLineEnumerateCaretOffsets()

```c
void OH_Drawing_TextLineEnumerateCaretOffsets(OH_Drawing_TextLine* line, Drawing_CaretOffsetsCallback callback)
```

**Description**

Enumerates the offset and index of each character in a text line object and passes them to a custom callback function. You can use the offset and index array for other operations.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| [Drawing_CaretOffsetsCallback](#drawing_caretoffsetscallback) callback | User-defined function [Drawing_CaretOffsetsCallback](capi-drawing-text-line-h.md#drawing_caretoffsetscallback).|

### OH_Drawing_TextLineGetAlignmentOffset()

```c
double OH_Drawing_TextLineGetAlignmentOffset(OH_Drawing_TextLine* line, double alignmentFactor, double alignmentWidth)
```

**Description**

Obtains the offset of a text line object after alignment based on the alignment factor and alignment width.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md)* line | Pointer to the [OH_Drawing_TextLine](capi-drawing-oh-drawing-textline.md) object.|
| double alignmentFactor | Alignment factor. A value less than or equal to 0.0 indicates left alignment, greater than 0.0 and less than 0.5 indicates left-biased alignment, 0.5 indicates center alignment, greater than 0.5 and less than 1.0 indicates right-biased alignment, and greater than or equal to 1.0 indicates right alignment. |
| double alignmentWidth | Alignment width, i.e., the offset of the bottom-right corner of the text line object relative to the starting position after final offset, in physical pixels (px). If the specified alignment width is less than the actual width of the text line object, 0 is returned. |

**Returns**

| Type| Description|
| -- | -- |
| double | Calculated offset required for alignment. The unit is physical pixel (px). |