# drawing_text_blob.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=29d41186dac135b3ba0b2c25ccc33837bb3c597b translatedAt=2026-11-02T14:34:29.322Z pushedAt=2026-11-03T03:53:52.040Z nl=2 -->

## Overview
Defines the text-related functions in the file.<br>This module adopts a single-thread model, and the caller must manage thread safety and context state switching.

**File to include**: <native_drawing/drawing_text_blob.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_RunBuffer](capi-drawing-oh-drawing-runbuffer.md) | OH_Drawing_RunBuffer | Describes a block of memory used to store text and position information. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)](#oh_drawing_textblobbuildercreate) | Creates an **OH_Drawing_TextBlobBuilder** object.|
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength,const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromtext) | Creates an **OH_Drawing_TextBlob** object from the text.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **text** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromtextwithfallback) | Creates a group of text objects from text, with font fallback support. If the current font does not support certain characters in the text (no corresponding glyph), the system automatically searches the system fonts for a fallback font that supports the character and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. All text objects share the coordinate system of the entire string: the glyph position of each text object already includes the width of the preceding text, so all text objects should be drawn at the same origin. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength,OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefrompostext) | Creates an **OH_Drawing_TextBlob** object from the text. The coordinates of each character in the **OH_Drawing_TextBlob** object are determined by the coordinate information in the **OH_Drawing_Point2D** array.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **text**, **point2D**, and **font** is NULL or **byteLength** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefrompostextwithfallback) | Creates a group of text objects from text, with font fallback support. If the current font does not support certain characters in the text (no corresponding glyph), the system automatically searches the system fonts for a fallback font that supports the character and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. The coordinate of each character in the text object is determined by the corresponding coordinate information in the OH_Drawing_Point2D array. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str,const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromstring) | Creates an **OH_Drawing_TextBlob** object from a string.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **str** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromstringwithfallback) | Creates a group of text objects from a string, with font fallback support. If the current font does not support certain characters in the text (no corresponding glyph), the system automatically searches the system fonts for a fallback font that supports the character and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. All text objects share the coordinate system of the entire string: the glyph position of each text object already includes the width of the preceding text, so all text objects should be drawn at the same origin. |
| [void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)](#oh_drawing_textblobgetbounds) | Obtains the bounds of an **OH_Drawing_TextBlob** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **textBlob** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobuniqueid) | Obtains the unique identifier of a text object. The identifier is a non-zero value.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder,const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)](#oh_drawing_textblobbuilderallocrunpos) | Allocates a run to store glyphs and positions. The pointer returned does not need to be managed by the caller. It can no longer be used after [OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake) is called.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **textBlobBuilder** or **font** is NULL or **count** is less than or equal to 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuildermake) | Makes an **OH_Drawing_TextBlob** object from an **OH_Drawing_TextBlobBuilder**.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **textBlobBuilder** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobdestroy) | Destroys a text object and reclaims the memory occupied by the object. |
| [void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuilderdestroy) | Destroys a text blob builder object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob** textBlobs, uint32_t count)](#oh_drawing_textblobsarraydestroy) | Destroys an array of OH_Drawing_TextBlob objects and reclaims the memory occupied by the array. This function destroys the text objects in the array and releases the array itself. |

## Function Description

### OH_Drawing_TextBlobBuilderCreate()

```c
OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)
```

**Description**

Creates an **OH_Drawing_TextBlobBuilder** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* | The function returns a pointer to the created text blob builder object. |

### OH_Drawing_TextBlobCreateFromText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from the text.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **text** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const void* text | Pointer to the text.|
| size_t byteLength | Length of the text, in bytes.|
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* | Pointer to the created text object OH_Drawing_TextBlob. |

### OH_Drawing_TextBlobCreateFromTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a group of text objects from text, with support for font fallback. If the current font does not support certain characters in the text (no corresponding glyph), the system automatically searches the system fonts for a fallback font that supports the character and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is still used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. All text objects share the coordinate system of the entire string: the glyph position of each text object already includes the width of the preceding text, so all text objects should be drawn at the same origin.

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| const void *text | [Input] Pointer to the text. |
| uint32_t byteLength | [Input] Length of the text, in bytes. |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [Input] Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [Input] Text encoding type. |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [Output] Pointer to the array of OH_Drawing_TextBlob objects. When no longer needed, use [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array. |
| uint32_t *textBlobsCount | [Output] Returns the number of text objects in the array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns OH_DRAWING_SUCCESS, indicating that the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER, indicating that any of the parameters text, font, textBlobs, or textBlobsCount is null, or byteLength is 0.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE, indicating that textEncoding is outside the enumeration range.<br>Returns OH_DRAWING_ERROR_ALLOCATION_FAILED, indicating that array memory allocation failed. |

### OH_Drawing_TextBlobCreateFromPosText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength, OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from the text. The coordinates of each character in the **OH_Drawing_TextBlob** object are determined by the coordinate information in the **OH_Drawing_Point2D** array.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **text**, **point2D**, and **font** is NULL or **byteLength** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const void* text | Pointer to the text.|
| size_t byteLength | Length of the text, in bytes.|
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* point2D | Pointer to the first address of the array of 2D points OH_Drawing_Point2D. The number of elements in the array is determined by the result of [OH_Drawing_FontCountText](capi-drawing-font-h.md#oh_drawing_fontcounttext). |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* | Pointer to the created text object OH_Drawing_TextBlob. |

### OH_Drawing_TextBlobCreateFromPosTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a group of text objects from text, with font fallback support. If the current font does not support certain characters in the text (no corresponding glyphs), the system automatically searches the system fonts for a fallback font that supports those characters and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is still used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. The coordinate of each character in the text object is determined by the corresponding coordinate information in the OH_Drawing_Point2D array.

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| const void *text | [In] Pointer to the text. |
| uint32_t byteLength | [In] Length of the text, in bytes. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) *point2D | [In] Address of the first element of the OH_Drawing_Point2D array. The number of elements in the array is determined by the result of [OH_Drawing_FontCountText](capi-drawing-font-h.md#oh_drawing_fontcounttext). |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [In] Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [In] Text encoding type. |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [Out] Pointer to the array of OH_Drawing_TextBlob objects. When no longer needed, use [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array. |
| uint32_t *textBlobsCount | [Out] Returns the number of text objects in the array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns OH_DRAWING_SUCCESS, indicating that the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER, indicating that any of text, point2D, font, textBlobs, or textBlobsCount is null, or byteLength is 0.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE, indicating that textEncoding is out of the enumeration range.<br>Returns OH_DRAWING_ERROR_ALLOCATION_FAILED, indicating that array memory allocation failed. |

### OH_Drawing_TextBlobCreateFromString()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from a string.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **str** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const char* str | Pointer to a string.|
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* | Pointer to the created text object OH_Drawing_TextBlob. |

### OH_Drawing_TextBlobCreateFromStringWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a group of text objects from a string, with font fallback support. If the current font does not support certain characters in the text (no corresponding glyphs), the system automatically searches the system fonts for a fallback font that supports the character and uses the glyph index of the fallback font. If no fallback font is found, the notdef placeholder glyph of the current font is still used. Each contiguous glyph segment that uses the same font (the current font or a fallback font) creates a corresponding TextBlob object. All text objects share the coordinate system of the entire string: the glyph position of each text object already includes the width of the preceding text, so all text objects should be drawn at the same origin.

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| const char *str | [Input] Pointer to the string. |
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [Input] Pointer to the font object OH_Drawing_Font. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [Input] Text encoding type. |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [Output] Pointer to the array of OH_Drawing_TextBlob objects. When no longer needed, use [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array. |
| uint32_t *textBlobsCount | [Output] Returns the number of text objects in the array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns OH_DRAWING_SUCCESS, indicating that the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER, indicating that any of the parameters str, font, textBlobs, or textBlobsCount is null.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE, indicating that textEncoding is outside the enumeration range.<br>Returns OH_DRAWING_ERROR_ALLOCATION_FAILED, indicating that array memory allocation failed. |

### OH_Drawing_TextBlobGetBounds()

```c
void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)
```

**Description**

Obtains the bounds of an **OH_Drawing_TextBlob** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **textBlob** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to the text object OH_Drawing_TextBlob. |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect, which developers can create by calling the OH_Drawing_Rect API. |

### OH_Drawing_TextBlobUniqueID()

```c
uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)
```

**Description**

Obtains the unique identifier of a text blob. The identifier is a non-zero value.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to the text object OH_Drawing_TextBlob. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns the unique identifier of the text blob.|

### OH_Drawing_TextBlobBuilderAllocRunPos()

```c
const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder, const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)
```

**Description**

Allocates a run to store glyphs and positions. The pointer returned does not need to be managed by the caller. It can no longer be used after [OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake) is called.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **textBlobBuilder** or **font** is NULL or **count** is less than or equal to 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object.|
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object OH_Drawing_Font. |
| int32_t count | Number of text blobs.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Rectangle of the text blob. The value NULL means that no rectangle is set.|

### OH_Drawing_TextBlobBuilderMake()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**Description**

Makes an **OH_Drawing_TextBlob** object from an **OH_Drawing_TextBlobBuilder**.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **textBlobBuilder** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* | Pointer to the created text object OH_Drawing_TextBlob. |

### OH_Drawing_TextBlobDestroy()

```c
void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)
```

**Description**

Destroys a text object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to the text object OH_Drawing_TextBlob. |

### OH_Drawing_TextBlobBuilderDestroy()

```c
void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**Description**

Destroys a text blob builder object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object.|


### OH_Drawing_TextBlobsArrayDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob** textBlobs, uint32_t count)
```

**Description**

Destroys an array of **OH_Drawing_TextBlob** objects and reclaims the memory occupied by the array. This function destroys the text objects in the array and releases the array itself.

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)** textBlobs | [Input] Pointer to an array of **OH_Drawing_TextBlob** objects. |
| uint32_t count | [Input] Size of the array. count must exactly match the number returned when the array was created. Passing any other value results in undefined behavior. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns OH_DRAWING_SUCCESS, indicating that the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER, indicating that textBlobs is null or count is 0. |
