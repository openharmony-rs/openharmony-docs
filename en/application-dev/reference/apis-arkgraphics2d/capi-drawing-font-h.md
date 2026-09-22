# drawing_font.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=f94c9354683cc515ee158bb93e3f5497b6ae62ad translatedAt=2026-08-24T08:32:54.046Z pushedAt=2026-08-31T07:25:52.785Z -->

## Overview

Defines the font-related functions.<br>This module adopts a single-thread model policy, and the caller is responsible for managing thread safety and context state switching.

**File to include**: <native_drawing/drawing_font.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md) | OH_Drawing_Font_Metrics | Describes the measurement information about a font.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_FontHinting](#oh_drawing_fonthinting) | OH_Drawing_FontHinting | Defines an enum for the font hinting types.|
| [OH_Drawing_FontEdging](#oh_drawing_fontedging) | OH_Drawing_FontEdging | Defines an enum for the font edging types.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ErrorCode OH_Drawing_FontGetSpacing(const OH_Drawing_Font* font, float* spacing)](#oh_drawing_fontgetspacing) | Obtains the recommended line spacing for a font.|
| [OH_Drawing_ErrorCode OH_Drawing_FontGetPos(const OH_Drawing_Font* font, const uint16_t* glyphs, int count,const OH_Drawing_Point* origin, OH_Drawing_Point2D* points)](#oh_drawing_fontgetpos) | Obtains the relative position of each glyph from the specified origin.|
| [OH_Drawing_ErrorCode OH_Drawing_FontGetWidthsBounds(const OH_Drawing_Font* font, const uint16_t* glyphs, int count,const OH_Drawing_Brush* brush, const OH_Drawing_Pen* pen, float* widths, OH_Drawing_Array* bounds)](#oh_drawing_fontgetwidthsbounds) | Obtains the width and bounding box of each glyph in a glyph array.|
| [OH_Drawing_ErrorCode OH_Drawing_FontMeasureTextWithBrushOrPen(const OH_Drawing_Font* font, const void* text,size_t byteLength, OH_Drawing_TextEncoding encoding, const OH_Drawing_Brush* brush, const OH_Drawing_Pen* pen,OH_Drawing_Rect* bounds, float* textWidth)](#oh_drawing_fontmeasuretextwithbrushorpen) | Obtains the width and bounding box of the text with a brush or pen.|
| [OH_Drawing_Font* OH_Drawing_FontCreate(void)](#oh_drawing_fontcreate) | Creates an **OH_Drawing_Font** object.|
| [void OH_Drawing_FontSetBaselineSnap(OH_Drawing_Font* font, bool baselineSnap)](#oh_drawing_fontsetbaselinesnap) | Sets whether to request that baselines be snapped to pixels when the current canvas matrix is axis aligned.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_FontIsBaselineSnap(const OH_Drawing_Font* font)](#oh_drawing_fontisbaselinesnap) | Checks whether baselines are requested to be snapped to pixels when the current canvas matrix is axis aligned.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetSubpixel(OH_Drawing_Font* font, bool isSubpixel)](#oh_drawing_fontsetsubpixel) | Sets whether the font uses subpixel rendering.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL. |
| [bool OH_Drawing_FontIsSubpixel(const OH_Drawing_Font* font)](#oh_drawing_fontissubpixel) | Obtains whether the font uses subpixel rendering.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL. |
| [void OH_Drawing_FontSetForceAutoHinting(OH_Drawing_Font* font, bool isForceAutoHinting)](#oh_drawing_fontsetforceautohinting) | Sets whether to forcibly use auto hinting, that is, whether to always hint glyphs.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_FontIsForceAutoHinting(const OH_Drawing_Font* font)](#oh_drawing_fontisforceautohinting) | Checks whether auto hinting is forcibly used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetTypeface(OH_Drawing_Font* font, OH_Drawing_Typeface* typeface)](#oh_drawing_fontsettypeface) | Sets a typeface for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_Typeface* OH_Drawing_FontGetTypeface(OH_Drawing_Font* font)](#oh_drawing_fontgettypeface) | Obtains the typeface of a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetTextSize(OH_Drawing_Font* font, float textSize)](#oh_drawing_fontsettextsize) | Sets the text size for a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_FontGetTextSize(const OH_Drawing_Font* font)](#oh_drawing_fontgettextsize) | Obtains the text size of a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [int OH_Drawing_FontCountText(OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding)](#oh_drawing_fontcounttext) | Obtains the number of glyphs represented by text.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **font** or **text** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_FontTextToGlyphs(const OH_Drawing_Font* font, const void* text, uint32_t byteLength,OH_Drawing_TextEncoding encoding, uint16_t* glyphs, int maxGlyphCount)](#oh_drawing_fonttexttoglyphs) | Converts text into glyph indices.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **font**, **text**, and **glyphs** is NULL, **byteLength** is **0**, or **maxGlyphCount** is less than or equal to 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontGetWidths(const OH_Drawing_Font* font, const uint16_t* glyphs, int count, float* widths)](#oh_drawing_fontgetwidths) | Obtains the width of each glyph in the glyph array.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of font, glyphs, or widths is NULL, or if count is less than or equal to 0. |
| [OH_Drawing_ErrorCode OH_Drawing_FontMeasureSingleCharacter(const OH_Drawing_Font* font, const char* str,float* textWidth)](#oh_drawing_fontmeasuresinglecharacter) | Measures the width of a single character. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.|
| [OH_Drawing_ErrorCode OH_Drawing_FontMeasureText(const OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding, OH_Drawing_Rect* bounds, float* textWidth)](#oh_drawing_fontmeasuretext) | Obtains the text width and bounding box.|
| [void OH_Drawing_FontSetLinearText(OH_Drawing_Font* font, bool isLinearText)](#oh_drawing_fontsetlineartext) | Sets linear scaling for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_FontIsLinearText(const OH_Drawing_Font* font)](#oh_drawing_fontislineartext) | Checks whether linear scaling is used for a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetTextSkewX(OH_Drawing_Font* font, float skewX)](#oh_drawing_fontsettextskewx) | Sets a horizontal skew factor for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_FontGetTextSkewX(const OH_Drawing_Font* font)](#oh_drawing_fontgettextskewx) | Obtains the horizontal skew factor of a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetFakeBoldText(OH_Drawing_Font* font, bool isFakeBoldText)](#oh_drawing_fontsetfakeboldtext) | Sets fake bold for a font by increasing the stroke width.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_FontIsFakeBoldText(const OH_Drawing_Font* font)](#oh_drawing_fontisfakeboldtext) | Obtains whether to increase the stroke width to approximate a bold font.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL. |
| [void OH_Drawing_FontSetScaleX(OH_Drawing_Font* font, float scaleX)](#oh_drawing_fontsetscalex) | Sets a horizontal scale factor for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_FontGetScaleX(const OH_Drawing_Font* font)](#oh_drawing_fontgetscalex) | Obtains the horizontal scale ratio of this font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetHinting(OH_Drawing_Font* font, OH_Drawing_FontHinting fontHinting)](#oh_drawing_fontsethinting) | Sets a font hinting effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **fontHinting** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_FontHinting OH_Drawing_FontGetHinting(const OH_Drawing_Font* font)](#oh_drawing_fontgethinting) | Obtains the font hinting effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetEmbeddedBitmaps(OH_Drawing_Font* font, bool isEmbeddedBitmaps)](#oh_drawing_fontsetembeddedbitmaps) | Sets whether to use bitmaps in a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_FontIsEmbeddedBitmaps(const OH_Drawing_Font* font)](#oh_drawing_fontisembeddedbitmaps) | Checks whether bitmaps are used in a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontSetEdging(OH_Drawing_Font* font, OH_Drawing_FontEdging fontEdging)](#oh_drawing_fontsetedging) | Sets a font edging effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **fontEdging** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_FontEdging OH_Drawing_FontGetEdging(const OH_Drawing_Font* font)](#oh_drawing_fontgetedging) | Obtains the font edging effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_FontDestroy(OH_Drawing_Font* font)](#oh_drawing_fontdestroy) | Destroys an **OH_Drawing_Font** object and reclaims the memory occupied by the object.|
| [float OH_Drawing_FontGetMetrics(OH_Drawing_Font* font, OH_Drawing_Font_Metrics* fontMetrics)](#oh_drawing_fontgetmetrics) | Obtains the measurement information about a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **font** or **fontMetrics** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_FontGetBounds(const OH_Drawing_Font* font, const uint16_t* glyphs, uint32_t count,OH_Drawing_Array* bounds)](#oh_drawing_fontgetbounds) | Obtains the rectangular bounding box for each glyph in the glyph array.|
| [OH_Drawing_ErrorCode OH_Drawing_FontGetPathForGlyph(const OH_Drawing_Font* font, uint16_t glyph,OH_Drawing_Path* path)](#oh_drawing_fontgetpathforglyph) | Obtains the outline path of the specified glyph index of the font. |
| [OH_Drawing_ErrorCode OH_Drawing_FontGetTextPath(const OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding, float x, float y, OH_Drawing_Path* path)](#oh_drawing_fontgettextpath) | Obtains the text outline path.|
| [OH_Drawing_ErrorCode OH_Drawing_FontGetTextPathWithFallback(const OH_Drawing_Font* font, const void* text, size_t byteLength, OH_Drawing_TextEncoding encoding, float x, float y, OH_Drawing_Path* path)](#oh_drawing_fontgettextpathwithfallback) | Obtains the text outline path, with font fallback support. |
| [OH_Drawing_ErrorCode OH_Drawing_FontSetThemeFontFollowed(OH_Drawing_Font* font, bool followed)](#oh_drawing_fontsetthemefontfollowed) | Sets whether to follow the theme font. When **followed** is set to **true**, the theme font is used if it is enabled by the system and no typeface is set.|
| [OH_Drawing_ErrorCode OH_Drawing_FontIsThemeFontFollowed(const OH_Drawing_Font* font, bool* followed)](#oh_drawing_fontisthemefontfollowed) | Checks whether the font follows the theme font. By default, the theme font is not followed.|
| [OH_Drawing_ErrorCode OH_Drawing_FontMeasureSingleCharacterWithFeatures(const OH_Drawing_Font* font, const char* str,const OH_Drawing_FontFeatures* fontFeatures, float* textWidth)](#oh_drawing_fontmeasuresinglecharacterwithfeatures) | Measures the width of a single character with font features. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.|
| [OH_Drawing_FontFeatures* OH_Drawing_FontFeaturesCreate(void)](#oh_drawing_fontfeaturescreate) | Creates an **OH_Drawing_FontFeatures** object.|
| [OH_Drawing_ErrorCode OH_Drawing_FontFeaturesAddFeature(OH_Drawing_FontFeatures* fontFeatures,const char* name, float value)](#oh_drawing_fontfeaturesaddfeature) | Adds a font feature to an **OH_Drawing_FontFeatures** object.|
| [OH_Drawing_ErrorCode OH_Drawing_FontFeaturesDestroy(OH_Drawing_FontFeatures* fontFeatures)](#oh_drawing_fontfeaturesdestroy) | Destroys an **OH_Drawing_FontFeatures** object and reclaims the memory occupied by the object.|

## Enum Description

### OH_Drawing_FontHinting

```c
enum OH_Drawing_FontHinting
```

**Description**

Defines an enum for the font hinting types.

**Since**: 12

| Value| Description|
| -- | -- |
| FONT_HINTING_NONE | No font hinting is used.|
| FONT_HINTING_SLIGHT | Slight font hinting is used to improve contrast.|
| FONT_HINTING_NORMAL | Normal font hinting is used to improve contrast.|
| FONT_HINTING_FULL | Full font hinting is used to improve contrast.|

### OH_Drawing_FontEdging

```c
enum OH_Drawing_FontEdging
```

**Description**

Enumerates the font edging types.

**Since**: 12

| Value| Description|
| -- | -- |
| FONT_EDGING_ALIAS | No anti-aliasing processing is used.|
| FONT_EDGING_ANTI_ALIAS | Uses anti-aliasing to smooth the jagged edges.|
| FONT_EDGING_SUBPIXEL_ANTI_ALIAS | Uses sub-pixel anti-aliasing to provide a smoother effect for jagged edges.|

## Function Description

### OH_Drawing_FontMeasureSingleCharacterWithFeatures()

```c
OH_Drawing_ErrorCode OH_Drawing_FontMeasureSingleCharacterWithFeatures(const OH_Drawing_Font* font, const char* str, const OH_Drawing_FontFeatures* fontFeatures, float* textWidth)
```

**Description**

Measures the width of a single character with font features. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object.|
| const char* str | Pointer to the single character to measure. A string can be passed in, but only the first character in the string is parsed and measured in UTF-8 encoding.|
| [const OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md)* fontFeatures | Pointer to the [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md) object. If no font feature is set, the preset font feature in the TrueType fonts (TTF) file is used.|
| float* textWidth | Pointer to the character width obtained, used as an output parameter. The unit is physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if at least one of the parameters **font**, **str**, **fontFeatures**, or **textWidth** is NULL, or the length of **str** is **0**.|

### OH_Drawing_FontFeaturesCreate()

```c
OH_Drawing_FontFeatures* OH_Drawing_FontFeaturesCreate(void)
```

**Description**

Creates an **OH_Drawing_FontFeatures** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md)* | The function returns a pointer to the created font feature container object OH_Drawing_FontFeatures.<br>If the returned object pointer is null, the font feature container object fails to be created. The possible cause is insufficient memory. |

### OH_Drawing_FontFeaturesAddFeature()

```c
OH_Drawing_ErrorCode OH_Drawing_FontFeaturesAddFeature(OH_Drawing_FontFeatures* fontFeatures, const char* name, float value)
```

**Description**

Adds a font feature to an **OH_Drawing_FontFeatures** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md)* fontFeatures | Pointer to the font features container object OH_Drawing_FontFeatures. |
| const char* name | Name of a font feature. Common font feature names include **liga**, **frac**, and **case**. A font feature needs a TTF file to work.|
| float value | Value of the font feature. You are advised to determine the valid value range by using a font viewing tool or referring to the font document.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if **fontFeatures** or **name** is a null pointer.|

### OH_Drawing_FontFeaturesDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_FontFeaturesDestroy(OH_Drawing_FontFeatures* fontFeatures)
```

**Description**

Destroys an **OH_Drawing_FontFeatures** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md)* fontFeatures | Pointer to the font feature container object OH_Drawing_FontFeatures. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if **fontFeatures** is NULL.|

### OH_Drawing_FontMeasureTextWithBrushOrPen()

```c
OH_Drawing_ErrorCode OH_Drawing_FontMeasureTextWithBrushOrPen(const OH_Drawing_Font* font, const void* text,size_t byteLength, OH_Drawing_TextEncoding encoding, const OH_Drawing_Brush* brush, const OH_Drawing_Pen* pen,OH_Drawing_Rect* bounds, float* textWidth)
```

**Description**

Obtains the width and bounding box of the text with a brush or pen.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const void* text | Pointer to the text.|
| size_t byteLength | Length of the text, in bytes.|
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Encoding type of the text.|
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the brush object OH_Drawing_Brush. |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* bounds | Used to carry the obtained bounding box. It can be NULL. When it is NULL, the bounding box information is not returned, and only the text width is returned. |
| float* textWidth | Used to store the obtained text width, as an output parameter. The unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of font, text, and textWidth is null, byteLength is 0, or both brush and pen are not null. |

### OH_Drawing_FontGetWidthsBounds()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetWidthsBounds(const OH_Drawing_Font* font, const uint16_t* glyphs, int count,const OH_Drawing_Brush* brush, const OH_Drawing_Pen* pen, float* widths, OH_Drawing_Array* bounds)
```

**Description**

Obtains the width and bounding box of each glyph in a glyph array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const uint16_t* glyphs | Pointer to the start address for storing the glyph indices.|
| int count | Number of glyph indices, which must be the same as the size of glyphs array.|
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the brush object OH_Drawing_Brush, used to specify the brush style for obtaining the glyph width and bounding box. |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen, used to specify the pen style for obtaining the glyph width and bounding box. |
| float* widths | Starting address for storing the obtained glyph widths, returned to the caller as the return value. The unit is physical pixel (px). |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* bounds | Starting address for storing the obtained glyph bounding boxes, used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of font and glyphs is null, count is not greater than 0, both brush and pen are not null, or both widths and bounds are null. |

### OH_Drawing_FontGetPos()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetPos(const OH_Drawing_Font* font, const uint16_t* glyphs, int count,const OH_Drawing_Point* origin, OH_Drawing_Point2D* points)
```

**Description**

Obtains the relative position of each glyph from the specified origin.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const uint16_t* glyphs | Pointer to the start address for storing the glyph indices.|
| int count | Number of glyph indices, which must be the same as the size of glyphs array.|
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* origin | Pointer to the position of the first glyph. This parameter can be NULL, in which case the position defaults to (0, 0). |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* points | Start address for storing the relative position of a glyph.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of font, glyphs, and points is null, or count is not greater than 0. |

### OH_Drawing_FontGetSpacing()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetSpacing(const OH_Drawing_Font* font, float* spacing)
```

**Description**

Obtains the recommended line spacing for a font.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| float* spacing | Pointer to the recommended line spacing of the font, returned to the caller. The unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of font and spacing is a null pointer. |

### OH_Drawing_FontCreate()

```c
OH_Drawing_Font* OH_Drawing_FontCreate(void)
```

**Description**

Creates an **OH_Drawing_Font** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* | The function returns a pointer to the created font object OH_Drawing_Font. |

### OH_Drawing_FontSetBaselineSnap()

```c
void OH_Drawing_FontSetBaselineSnap(OH_Drawing_Font* font, bool baselineSnap)
```

**Description**

Sets whether to request that baselines be snapped to pixels when the current canvas matrix is axis aligned.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool baselineSnap | Whether the font baseline is snapped to pixels. **true** means yes; **false** otherwise.|

### OH_Drawing_FontIsBaselineSnap()

```c
bool OH_Drawing_FontIsBaselineSnap(const OH_Drawing_Font* font)
```

**Description**

Checks whether baselines are requested to be snapped to pixels when the current canvas matrix is axis aligned.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the font baseline is snapped to pixels. **true** means yes; **false** otherwise.|

### OH_Drawing_FontSetSubpixel()

```c
void OH_Drawing_FontSetSubpixel(OH_Drawing_Font* font, bool isSubpixel)
```

**Description**

Sets whether to use subpixel rendering for the font.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool isSubpixel | Whether the font uses subpixel rendering. The value true means to use it, and false means not to use it. |

### OH_Drawing_FontIsSubpixel()

```c
bool OH_Drawing_FontIsSubpixel(const OH_Drawing_Font* font)
```

**Description**

Obtains whether the font uses subpixel rendering.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the font uses subpixel rendering. true indicates that it is used, and false indicates the opposite. |

### OH_Drawing_FontSetForceAutoHinting()

```c
void OH_Drawing_FontSetForceAutoHinting(OH_Drawing_Font* font, bool isForceAutoHinting)
```

**Description**

Sets whether to forcibly use auto hinting, that is, whether to always hint glyphs.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool isForceAutoHinting | Whether to forcibly use auto hinting, that is, whether to always hint glyphs. **true** means yes; **false** otherwise.|

### OH_Drawing_FontIsForceAutoHinting()

```c
bool OH_Drawing_FontIsForceAutoHinting(const OH_Drawing_Font* font)
```

**Description**

Checks whether auto hinting is forcibly used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether auto hinting is forcibly used. **true** means yes; **false** otherwise.|

### OH_Drawing_FontSetTypeface()

```c
void OH_Drawing_FontSetTypeface(OH_Drawing_Font* font, OH_Drawing_Typeface* typeface)
```

**Description**

Sets a typeface for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* typeface | Pointer to an **OH_Drawing_Typeface** object. If NULL is passed in, the default **OH_Drawing_Typeface** object is used.|

### OH_Drawing_FontGetTypeface()

```c
OH_Drawing_Typeface* OH_Drawing_FontGetTypeface(OH_Drawing_Font* font)
```

**Description**

Obtains the typeface of a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | The function returns a pointer to the font object OH_Drawing_Typeface. |

### OH_Drawing_FontSetTextSize()

```c
void OH_Drawing_FontSetTextSize(OH_Drawing_Font* font, float textSize)
```

**Description**

Sets the text size for a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| float textSize | Text size, in physical pixels (px). This parameter is a floating-point number. If it is a negative number, the font size is set to 0. When the font size is 0, the drawn text is not displayed. |

### OH_Drawing_FontGetTextSize()

```c
float OH_Drawing_FontGetTextSize(const OH_Drawing_Font* font)
```

**Description**

Obtains the text size of a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns a floating point number representing the text size.|

### OH_Drawing_FontCountText()

```c
int OH_Drawing_FontCountText(OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding)
```

**Description**

Obtains the number of glyphs represented by text.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **font** or **text** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const void* text | Pointer to the start address of the storage.|
| size_t byteLength | Length of the text, in bytes. If this byte length is greater than the byte length of the text string, undefined behavior occurs. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Text encoding type OH_Drawing_TextEncoding. |

**Returns**

| Type| Description|
| -- | -- |
| int | Number of glyphs represented by the text. The value is an integer.|

### OH_Drawing_FontTextToGlyphs()

```c
uint32_t OH_Drawing_FontTextToGlyphs(const OH_Drawing_Font* font, const void* text, uint32_t byteLength,OH_Drawing_TextEncoding encoding, uint16_t* glyphs, int maxGlyphCount)
```

**Description**

Converts text into glyph indices.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **font**, **text**, and **glyphs** is NULL, **byteLength** is **0**, or **maxGlyphCount** is less than or equal to 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const void* text | Pointer to the start address of the storage.|
| uint32_t byteLength | Text length, in bytes.|
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Text encoding type OH_Drawing_TextEncoding. |
| uint16_t* glyphs | Pointer to the start address for storing the glyph indices.|
| int maxGlyphCount | Maximum number of glyphs represented by the text. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns the number of glyph indices.|

### OH_Drawing_FontGetWidths()

```c
void OH_Drawing_FontGetWidths(const OH_Drawing_Font* font, const uint16_t* glyphs, int count, float* widths)
```

**Description**

Obtains the width of each glyph in the glyph array.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of font, glyphs, or widths is NULL, or if count is less than or equal to 0.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const uint16_t* glyphs | Pointer to the start address for storing the glyph indices.|
| int count | Number of glyph indexes, which is the same as the size of the glyphs array. |
| float* widths | Pointer to the start address for storing the obtained glyph widths, in physical pixels (px). |

### OH_Drawing_FontMeasureSingleCharacter()

```c
OH_Drawing_ErrorCode OH_Drawing_FontMeasureSingleCharacter(const OH_Drawing_Font* font, const char* str,float* textWidth)
```

**Description**

Measures the width of a single character. If the typeface of the current font does not support the character to measure, the system typeface is used to measure the character width.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| const char* str | Pointer to the single character to measure. A string can be passed in, but only the first character in the string is parsed and measured in UTF-8 encoding.|
| float* textWidth | Pointer to the obtained character width, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if at least one of the parameters **font**, **str**, or **textWidth** is NULL, or the length of **str** is **0**.|

### OH_Drawing_FontMeasureText()

```c
OH_Drawing_ErrorCode OH_Drawing_FontMeasureText(const OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding, OH_Drawing_Rect* bounds, float* textWidth)
```

**Description**

Obtains the text width and bounding box.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const void* text | Pointer to the text.|
| size_t byteLength | Indicates the text length in bytes. If this byte length is greater than the byte length of the text string, undefined behavior occurs. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Encoding type of the text.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* bounds | Used to carry the obtained bounding box. It can be NULL. When it is NULL, the bounding box information is not returned, and only the text width is returned. |
| float* textWidth | Used to store the obtained text width as an output parameter. The unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if at least one of the parameters **font**, **text**, and **textWidth** is NULL, or **byteLength** is **0**.|

### OH_Drawing_FontSetLinearText()

```c
void OH_Drawing_FontSetLinearText(OH_Drawing_Font* font, bool isLinearText)
```

**Description**

Sets linear scaling for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool isLinearText | Whether to enable linearly scalable font. The value true means to enable it, and false means to disable it. |

### OH_Drawing_FontIsLinearText()

```c
bool OH_Drawing_FontIsLinearText(const OH_Drawing_Font* font)
```

**Description**

Checks whether linear scaling is used for a font object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if linear scaling is used; returns **false** otherwise.|

### OH_Drawing_FontSetTextSkewX()

```c
void OH_Drawing_FontSetTextSkewX(OH_Drawing_Font* font, float skewX)
```

**Description**

Sets a horizontal skew factor for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| float skewX | Skew of the X axis relative to the Y axis. |

### OH_Drawing_FontGetTextSkewX()

```c
float OH_Drawing_FontGetTextSkewX(const OH_Drawing_Font* font)
```

**Description**

Obtains the horizontal skew factor of a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns a floating point number representing the horizontal skew factor.|

### OH_Drawing_FontSetFakeBoldText()

```c
void OH_Drawing_FontSetFakeBoldText(OH_Drawing_Font* font, bool isFakeBoldText)
```

**Description**

Sets fake bold for a font by increasing the stroke width.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| bool isFakeBoldText | Whether to enable increasing the stroke width. The value true means to enable it, and false means not to enable it. |

### OH_Drawing_FontIsFakeBoldText()

```c
bool OH_Drawing_FontIsFakeBoldText(const OH_Drawing_Font* font)
```

**Description**

Obtains whether to increase the stroke width to approximate a bold font.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if font is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns whether to increase the stroke width to approximate a bold font. true means increase, and false means do not increase. |

### OH_Drawing_FontSetScaleX()

```c
void OH_Drawing_FontSetScaleX(OH_Drawing_Font* font, float scaleX)
```

**Description**

Sets a horizontal scale factor for a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| float scaleX | Horizontal scale factor.|

### OH_Drawing_FontGetScaleX()

```c
float OH_Drawing_FontGetScaleX(const OH_Drawing_Font* font)
```

**Description**

Obtains the horizontal scale ratio of this font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the horizontal scale factor.|

### OH_Drawing_FontSetHinting()

```c
void OH_Drawing_FontSetHinting(OH_Drawing_Font* font, OH_Drawing_FontHinting fontHinting)
```

**Description**

Sets a font hinting effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **fontHinting** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| [OH_Drawing_FontHinting](#oh_drawing_fonthinting) fontHinting | Font outline effect type enumerated by OH_Drawing_FontHinting. |

### OH_Drawing_FontGetHinting()

```c
OH_Drawing_FontHinting OH_Drawing_FontGetHinting(const OH_Drawing_Font* font)
```

**Description**

Obtains the font hinting effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontHinting](#oh_drawing_fonthinting) | Returns the font outline effect enumeration type OH_Drawing_FontHinting. |

### OH_Drawing_FontSetEmbeddedBitmaps()

```c
void OH_Drawing_FontSetEmbeddedBitmaps(OH_Drawing_Font* font, bool isEmbeddedBitmaps)
```

**Description**

Sets whether to use bitmaps in a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool isEmbeddedBitmaps | Whether to use bitmaps in the font. The value **true** means to use bitmaps in the font, and **false** means the opposite.|

### OH_Drawing_FontIsEmbeddedBitmaps()

```c
bool OH_Drawing_FontIsEmbeddedBitmaps(const OH_Drawing_Font* font)
```

**Description**

Checks whether bitmaps are used in a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if bitmaps are used; returns **false** otherwise.|

### OH_Drawing_FontSetEdging()

```c
void OH_Drawing_FontSetEdging(OH_Drawing_Font* font, OH_Drawing_FontEdging fontEdging)
```

**Description**

Sets a font edging effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **fontEdging** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_FontEdging](#oh_drawing_fontedging) fontEdging | Font edge effect enum type OH_Drawing_FontEdging. |

### OH_Drawing_FontGetEdging()

```c
OH_Drawing_FontEdging OH_Drawing_FontGetEdging(const OH_Drawing_Font* font)
```

**Description**

Obtains the font edging effect.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontEdging](#oh_drawing_fontedging) | Font edging effect.|

### OH_Drawing_FontDestroy()

```c
void OH_Drawing_FontDestroy(OH_Drawing_Font* font)
```

**Description**

Destroys an **OH_Drawing_Font** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |

### OH_Drawing_FontGetMetrics()

```c
float OH_Drawing_FontGetMetrics(OH_Drawing_Font* font, OH_Drawing_Font_Metrics* fontMetrics)
```

**Description**

Obtains the measurement information about a font.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **font** or **fontMetrics** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md)* fontMetrics | Pointer to the font metrics information object OH_Drawing_Font_Metrics. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns a floating-point variable that indicates the recommended interline spacing.|

### OH_Drawing_FontGetBounds()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetBounds(const OH_Drawing_Font* font, const uint16_t* glyphs, uint32_t count,OH_Drawing_Array* bounds)
```

**Description**

Obtains the rectangular bounding box for each glyph in the glyph array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the OH_Drawing_Font object. |
| const uint16_t* glyphs | Pointer to a glyph array.|
| uint32_t count | Length of the glyph array.|
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* bounds | Pointer to the array of rectangular bounds, used to store the obtained glyph rectangular bounds as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if any of **font**, **glyphs**, or **bounds** is NULL or **count** is **0**.|

### OH_Drawing_FontGetPathForGlyph()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetPathForGlyph(const OH_Drawing_Font* font, uint16_t glyph,OH_Drawing_Path* path)
```

**Description**

Obtains the outline path of the specified glyph index of the font.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| uint16_t glyph | Specified glyph index. It must be a valid glyph index that exists in the current font; otherwise, an error is returned. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the path object OH_Drawing_Path, used to store the obtained glyph path. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **font** or **path** is NULL or the specified glyph does not exist.|

### OH_Drawing_FontGetTextPath()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetTextPath(const OH_Drawing_Font* font, const void* text, size_t byteLength,OH_Drawing_TextEncoding encoding, float x, float y, OH_Drawing_Path* path)
```

**Description**

Obtains the text outline path.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| const void* text | Pointer to the text string whose outline path is to be obtained. |
| size_t byteLength | Byte length of the text. If this byte length is greater than the byte length of the text string, undefined behavior occurs. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Text encoding format, which supports UTF-8, UTF-16, UTF-32, and glyph index. For details about the specific type format, see OH_Drawing_TextEncoding. |
| float x | X coordinate of the text in the drawing area with the origin as the starting position, in physical pixels (px). |
| float y | Y coordinate of the text in the drawing area with the origin as the starting position, in physical pixels (px). |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Output parameter that returns the obtained text outline path object. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns OH_DRAWING_SUCCESS if the operation is successful.<br> Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of font, text, or path is a null pointer. |

### OH_Drawing_FontGetTextPathWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_FontGetTextPathWithFallback(const OH_Drawing_Font* font, const void* text, size_t byteLength, OH_Drawing_TextEncoding encoding, float x, float y, OH_Drawing_Path* path)
```

**Description**

Obtains the text outline path with font fallback support.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object.|
| const void* text | Pointer to the text string.|
| size_t byteLength | Length of the text path. If the length is greater than the length of the text string, undefined behavior occurs.|
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) encoding | Text encoding format, which supports UTF-8, UTF-16, UTF-32, and glyph indexes. |
| float x | X coordinate of the text in the drawing area, with the origin as the start point.|
| float y | Y coordinate of the text in the drawing area, with the origin as the start point.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the text outline path.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br> Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if any of font, text, or path is a null pointer, or byteLength is 0. |

### OH_Drawing_FontSetThemeFontFollowed()

```c
OH_Drawing_ErrorCode OH_Drawing_FontSetThemeFontFollowed(OH_Drawing_Font* font, bool followed)
```

**Description**

Sets whether to follow the theme font. When **followed** is set to **true**, the theme font is used if it is enabled by the system and no typeface is set.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool followed | Whether to follow the theme font. The value **true** means to follow the theme font, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if **font** is NULL.|

### OH_Drawing_FontIsThemeFontFollowed()

```c
OH_Drawing_ErrorCode OH_Drawing_FontIsThemeFontFollowed(const OH_Drawing_Font* font, bool* followed)
```

**Description**

Checks whether the font follows the theme font. By default, the theme font is not followed.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| bool* followed | Check result. The value **true** means that the theme font is followed, and **false** means the opposite. It is used as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **font** or **followed** is NULL.|