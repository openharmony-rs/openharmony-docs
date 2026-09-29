# drawing_text_blob.h

## Overview

This file declares the functions related to the text blob in the drawing module.

**Library**: libnative_drawing.so

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_RunBuffer](capi-drawing-oh-drawing-runbuffer.md) | OH_Drawing_RunBuffer | This struct describes a run, which provides storage for glyphs and positions. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)](#oh_drawing_textblobbuildercreate) | Creates an **OH_Drawing_TextBlobBuilder** object. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromtext) | Creates an **OH_Drawing_TextBlob** object from the text. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **text** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromtextwithfallback) | Creates a sequence of `OH_Drawing_TextBlob` objects from the text with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. One text blob is created per run of consecutive codepoints that share the same typeface. All blobs share the coordinate system of the whole string: each blob's glyph positions already include the advance of preceding runs, so every blob should be drawn at the same origin. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength, OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefrompostext) | Creates an **OH_Drawing_TextBlob** object from the text. The coordinates of each character in the **<br>OH_Drawing_TextBlob** object are determined by the coordinate information in the **OH_Drawing_Point2D** array. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **text**, **point2D**, and **font** is NULL or **byteLength** is **0**, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefrompostextwithfallback) | Creates a sequence of `OH_Drawing_TextBlob` objects from text with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. If no fallback typeface is found, the typeface of the current font is still used. One text blob is created per run of consecutive codepoints that share the same typeface. The coordinates of each character in the `OH_Drawing_TextBlob` object are determined by the coordinate information in the `OH_Drawing_Point2D` array. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)](#oh_drawing_textblobcreatefromstring) | Creates an **OH_Drawing_TextBlob** object from a string. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **str** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)](#oh_drawing_textblobcreatefromstringwithfallback) | Creates a sequence of `OH_Drawing_TextBlob` objects from a string with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. One text blob is created per run of consecutive codepoints that share the same typeface. All blobs share the coordinate system of the whole string: each blob's glyph positions already include the advance of preceding runs, so every blob should be drawn at the same origin. |
| [void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)](#oh_drawing_textblobgetbounds) | Obtains the bounds of an **OH_Drawing_TextBlob** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **textBlob** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobuniqueid) | Obtains the unique identifier of a text blob. The identifier is a non-zero value. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder, const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)](#oh_drawing_textblobbuilderallocrunpos) | Allocates a run to store glyphs and positions. The pointer returned does not need to be managed by the caller. It can no longer be used after [OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake) is called. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **textBlobBuilder** or **font** is NULL or **count** is less than or equal to 0, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuildermake) | Makes an **OH_Drawing_TextBlob** object from an **OH_Drawing_TextBlobBuilder**. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **textBlobBuilder** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)](#oh_drawing_textblobdestroy) | Destroys an **OH_Drawing_TextBlob** object and reclaims the memory occupied by the object. |
| [void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)](#oh_drawing_textblobbuilderdestroy) | Destroys an **OH_Drawing_TextBlobBuilder** object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob **textBlobs, uint32_t count)](#oh_drawing_textblobsarraydestroy) | Destroys an array of `OH_Drawing_TextBlob` objects and reclaims the memory occupied by the array. This function destroys every text blob in the array that is still alive and releases the array itself. <b>count</b> must be exactly the number reported when the array was created; passing any other value results in undefined behavior. |

## Function description

### OH_Drawing_TextBlobBuilderCreate()

```c
OH_Drawing_TextBlobBuilder* OH_Drawing_TextBlobBuilderCreate(void)
```

**Description**

Creates an **OH_Drawing_TextBlobBuilder** object.

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_TextBlobBuilder*](capi-drawing-oh-drawing-textblobbuilder.md) | Returns the pointer to the **OH_Drawing_TextBlobBuilder** object created. |

### OH_Drawing_TextBlobCreateFromText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromText(const void* text, size_t byteLength, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from the text. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **text** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void* text | Pointer to the text. |
| size_t byteLength | Length of the text, in bytes. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_TextBlob*](capi-drawing-oh-drawing-textblob.md) | Returns a pointer to the created [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) object. |

### OH_Drawing_TextBlobCreateFromTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromTextWithFallback(const void *text, uint32_t byteLength, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a sequence of `OH_Drawing_TextBlob` objects from the text with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. One text blob is created per run of consecutive codepoints that share the same typeface. All blobs share the coordinate system of the whole string: each blob's glyph positions already include the advance of preceding runs, so every blob should be drawn at the same origin.

**Since**: 26.0.1

**Resource release**: drawing_text_blob/OH_Drawing_TextBlobsArrayDestroy {textBlobs}

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void *text | [in] Pointer to the text. |
| uint32_t byteLength | [in] Length of the text, in bytes. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [in] Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [in] Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [out] Pointer to an array of `OH_Drawing_TextBlob` objects. It is used as an output parameter. Uses [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array when it is no longer needed. |
| uint32_t *textBlobsCount | [out] Pointer to the count of TextBlob in the array. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.</li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if any of text, font, textBlobs, or textBlobsCount is NULL, or byteLength is 0.</li> <li>[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) if textEncoding is not set to one of the enumerated values.</li> <li>[OH_DRAWING_ERROR_ALLOCATION_FAILED](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the result array cannot be allocated.</li> </ul> |

### OH_Drawing_TextBlobCreateFromPosText()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromPosText(const void* text, size_t byteLength, OH_Drawing_Point2D* point2D, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from the text. The coordinates of each character in the **<br>OH_Drawing_TextBlob** object are determined by the coordinate information in the **OH_Drawing_Point2D** array. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **text**, **point2D**, and **font** is NULL or **byteLength** is **0**, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void* text | Pointer to the text. |
| size_t byteLength | Length of the text, in bytes. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* point2D | Pointer to the start address of the  [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) array. The number of entries in the array is determined by  [OH_Drawing_FontCountText](capi-drawing-font-h.md#oh_drawing_fontcounttext) . |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_TextBlob*](capi-drawing-oh-drawing-textblob.md) | Returns a pointer to the created [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) object. |

### OH_Drawing_TextBlobCreateFromPosTextWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromPosTextWithFallback(const void *text, uint32_t byteLength, OH_Drawing_Point2D *point2D, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a sequence of `OH_Drawing_TextBlob` objects from text with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. If no fallback typeface is found, the typeface of the current font is still used. One text blob is created per run of consecutive codepoints that share the same typeface. The coordinates of each character in the `OH_Drawing_TextBlob` object are determined by the coordinate information in the `OH_Drawing_Point2D` array.

**Since**: 26.0.1

**Resource release**: drawing_text_blob/OH_Drawing_TextBlobsArrayDestroy {textBlobs}

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void *text | [in] Pointer to the text. |
| uint32_t byteLength | [in] Length of the text, in bytes. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) *point2D | [in] Pointer to the start address of the [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) array. The number of elements in the array is determined by [OH_Drawing_FontCountText](capi-drawing-font-h.md#oh_drawing_fontcounttext). |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [in] Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [in] Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [out] Pointer to an array of <b>OH_Drawing_TextBlob</b> objects. It is used as an output parameter. Uses [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array when it is no longer needed. |
| uint32_t *textBlobsCount | [out] Pointer to the count of TextBlob in the array. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.</li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if any of text, point2D, font, textBlobs, and textBlobsCount is NULL, or byteLength is 0.</li> <li>[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) if textEncoding is not set to one of the enumerated values.</li> <li>[OH_DRAWING_ERROR_ALLOCATION_FAILED](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the result array cannot be allocated.</li> </ul> |

### OH_Drawing_TextBlobCreateFromString()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobCreateFromString(const char* str, const OH_Drawing_Font* font, OH_Drawing_TextEncoding textEncoding)
```

**Description**

Creates an **OH_Drawing_TextBlob** object from a string. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **str** or **font** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **textEncoding** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* str | Pointer to a string. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_TextBlob*](capi-drawing-oh-drawing-textblob.md) | Returns a pointer to the created [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) object. |

### OH_Drawing_TextBlobCreateFromStringWithFallback()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobCreateFromStringWithFallback(const char *str, const OH_Drawing_Font *font, OH_Drawing_TextEncoding textEncoding, OH_Drawing_TextBlob ***textBlobs, uint32_t *textBlobsCount)
```

**Description**

Creates a sequence of `OH_Drawing_TextBlob` objects from a string with font fallback support. When the typeface of the current font does not support certain characters, it automatically finds fallback typefaces from the system. One text blob is created per run of consecutive codepoints that share the same typeface. All blobs share the coordinate system of the whole string: each blob's glyph positions already include the advance of preceding runs, so every blob should be drawn at the same origin.

**Since**: 26.0.1

**Resource release**: drawing_text_blob/OH_Drawing_TextBlobsArrayDestroy {textBlobs}

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *str | [in] Pointer to a string. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md) *font | [in] Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object. |
| [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding) textEncoding | [in] Text encoding type [OH_Drawing_TextEncoding](capi-drawing-types-h.md#oh_drawing_textencoding). |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) ***textBlobs | [out] Pointer to an array of `OH_Drawing_TextBlob` objects. It is used as an output parameter. Uses [OH_Drawing_TextBlobsArrayDestroy](capi-drawing-text-blob-h.md#oh_drawing_textblobsarraydestroy) to release the array when it is no longer needed. |
| uint32_t *textBlobsCount | [out] Pointer to the count of TextBlob in the array. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.</li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if any of str, font, textBlobs, or textBlobsCount is NULL.</li> <li>[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) if textEncoding is not set to one of the enumerated values.</li> <li>[OH_DRAWING_ERROR_ALLOCATION_FAILED](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the result array cannot be allocated.</li> </ul> |

### OH_Drawing_TextBlobGetBounds()

```c
void OH_Drawing_TextBlobGetBounds(OH_Drawing_TextBlob* textBlob, OH_Drawing_Rect* rect)
```

**Description**

Obtains the bounds of an **OH_Drawing_TextBlob** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **textBlob** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to the [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) object. |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object. You can call [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) to create a rectangle object. |

### OH_Drawing_TextBlobUniqueID()

```c
uint32_t OH_Drawing_TextBlobUniqueID(const OH_Drawing_TextBlob* textBlob)
```

**Description**

Obtains the unique identifier of a text blob. The identifier is a non-zero value. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to the [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the unique identifier of the text blob. |

### OH_Drawing_TextBlobBuilderAllocRunPos()

```c
const OH_Drawing_RunBuffer* OH_Drawing_TextBlobBuilderAllocRunPos(OH_Drawing_TextBlobBuilder* textBlobBuilder, const OH_Drawing_Font* font, int32_t count, const OH_Drawing_Rect* rect)
```

**Description**

Allocates a run to store glyphs and positions. The pointer returned does not need to be managed by the caller. It can no longer be used after [OH_Drawing_TextBlobBuilderMake](capi-drawing-text-blob-h.md#oh_drawing_textblobbuildermake) is called. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **textBlobBuilder** or **font** is NULL or **count** is less than or equal to 0, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to an **OH_Drawing_Font** object. |
| int32_t count | Number of text blobs. |
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Rectangle of the text blob. The value NULL means that no rectangle is set. |

**Returns**:

| Type | Description |
| -- | -- |
| [const OH_Drawing_RunBuffer*](capi-drawing-oh-drawing-runbuffer.md) | Returns the pointer to the **OH_Drawing_RunBuffer** object created. |

### OH_Drawing_TextBlobBuilderMake()

```c
OH_Drawing_TextBlob* OH_Drawing_TextBlobBuilderMake(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**Description**

Makes an **OH_Drawing_TextBlob** object from an **OH_Drawing_TextBlobBuilder**. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **textBlobBuilder** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_TextBlob*](capi-drawing-oh-drawing-textblob.md) | Returns the pointer to the **OH_Drawing_TextBlob** object created. |

### OH_Drawing_TextBlobDestroy()

```c
void OH_Drawing_TextBlobDestroy(OH_Drawing_TextBlob* textBlob)
```

**Description**

Destroys an **OH_Drawing_TextBlob** object and reclaims the memory occupied by the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to an **OH_Drawing_TextBlob** object. |

### OH_Drawing_TextBlobBuilderDestroy()

```c
void OH_Drawing_TextBlobBuilderDestroy(OH_Drawing_TextBlobBuilder* textBlobBuilder)
```

**Description**

Destroys an **OH_Drawing_TextBlobBuilder** object and reclaims the memory occupied by the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md)* textBlobBuilder | Pointer to an **OH_Drawing_TextBlobBuilder** object. |

### OH_Drawing_TextBlobsArrayDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_TextBlobsArrayDestroy(OH_Drawing_TextBlob **textBlobs, uint32_t count)
```

**Description**

Destroys an array of `OH_Drawing_TextBlob` objects and reclaims the memory occupied by the array. This function destroys every text blob in the array that is still alive and releases the array itself. <b>count</b> must be exactly the number reported when the array was created; passing any other value results in undefined behavior.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) **textBlobs | [in] Pointer to an array of `OH_Drawing_TextBlob` objects. |
| uint32_t count | [in] The size of textBlobs array. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.</li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if textBlobs is NULL or count is 0.</li> </ul> |


