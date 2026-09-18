# drawing_typeface.h

## Overview

This file declares the functions related to the typeface in the drawing module. Different platforms have their own default typefaces. You can also parse the .ttf file to obtain the typefaces specified by the third party, such as SimSun and SimHei.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateDefault(void)](#oh_drawing_typefacecreatedefault) | Creates a default **OH_Drawing_Typeface** object. |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFile(const char* path, int index)](#oh_drawing_typefacecreatefromfile) | Creates an **OH_Drawing_Typeface** object through a file. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFileWithArguments(const char* path, const OH_Drawing_FontArguments* fontArguments)](#oh_drawing_typefacecreatefromfilewitharguments) | Creates an **OH_Drawing_Typeface** object with font arguments through a file. If the **OH_Drawing_Typeface** object does not support the variation described in the font arguments, this function creates an **OH_Drawing_Typeface** object with the default font arguments. In this case, this function provides the same capability as [OH_Drawing_TypefaceCreateFromFile](capi-drawing-typeface-h.md#oh_drawing_typefacecreatefromfile). |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromCurrent(const OH_Drawing_Typeface* current, const OH_Drawing_FontArguments* fontArguments)](#oh_drawing_typefacecreatefromcurrent) | Creates an **OH_Drawing_Typeface** object with font arguments based on an existing **OH_Drawing_Typeface**<br>object. |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromStream(OH_Drawing_MemoryStream* memoryStream, int32_t index)](#oh_drawing_typefacecreatefromstream) | Creates an **OH_Drawing_Typeface** object through a memory stream. If the memory stream is an invalid font file, a null pointer is returned. After the memory stream is passed in, the ownership is transferred and you cannot release it. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **memoryStream** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_TypefaceDestroy(OH_Drawing_Typeface* typeface)](#oh_drawing_typefacedestroy) | Destroys an **OH_Drawing_Typeface** object and reclaims the memory occupied by the object. |
| [OH_Drawing_FontArguments* OH_Drawing_FontArgumentsCreate(void)](#oh_drawing_fontargumentscreate) | Creates an **OH_Drawing_FontArguments** object. The font arguments are used to create an **<br>OH_Drawing_Typeface** object with custom attributes. |
| [OH_Drawing_ErrorCode OH_Drawing_FontArgumentsAddVariation(OH_Drawing_FontArguments* fontArguments, const char* axis, float value)](#oh_drawing_fontargumentsaddvariation) | Adds a variation to an **OH_Drawing_FontArguments** object. |
| [OH_Drawing_ErrorCode OH_Drawing_FontArgumentsDestroy(OH_Drawing_FontArguments* fontArguments)](#oh_drawing_fontargumentsdestroy) | Destroys an **OH_Drawing_FontArguments** object. |
| [OH_Drawing_ErrorCode OH_Drawing_TypefaceIsBold(const OH_Drawing_Typeface* typeface, bool* isBold)](#oh_drawing_typefaceisbold) | Checks whether the typeface is bold. |
| [OH_Drawing_ErrorCode OH_Drawing_TypefaceIsItalic(const OH_Drawing_Typeface* typeface, bool* isItalic)](#oh_drawing_typefaceisitalic) | Checks whether the typeface is italic. |

## Function description

### OH_Drawing_TypefaceCreateDefault()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateDefault(void)
```

**Description**

Creates a default **OH_Drawing_Typeface** object.

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Returns the pointer to the OH_Drawing_Typeface object created. |

### OH_Drawing_TypefaceCreateFromFile()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFile(const char* path, int index)
```

**Description**

Creates an **OH_Drawing_Typeface** object through a file. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* path | Pointer to the file path. |
| int index | File index. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Returns a pointer to the created {@link OH_Drawing_Typeface} object. |

### OH_Drawing_TypefaceCreateFromFileWithArguments()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFileWithArguments(const char* path, const OH_Drawing_FontArguments* fontArguments)
```

**Description**

Creates an **OH_Drawing_Typeface** object with font arguments through a file. If the **OH_Drawing_Typeface** object does not support the variation described in the font arguments, this function creates an **OH_Drawing_Typeface** object with the default font arguments. In this case, this function provides the same capability as [OH_Drawing_TypefaceCreateFromFile](capi-drawing-typeface-h.md#oh_drawing_typefacecreatefromfile).

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* path | Pointer to the file path. |
| const OH_Drawing_FontArguments* fontArguments | Pointer to an {@link OH_Drawing_FontArguments} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Returns a pointer to the created {@link OH_Drawing_Typeface} object.  If a null pointer is returned, the creation fails. Possible causes are that no memory is available, the passed-in   path or fontArguments is NULL, or the path is invalid. |

### OH_Drawing_TypefaceCreateFromCurrent()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromCurrent(const OH_Drawing_Typeface* current, const OH_Drawing_FontArguments* fontArguments)
```

**Description**

Creates an **OH_Drawing_Typeface** object with font arguments based on an existing **OH_Drawing_Typeface**<br>object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Typeface* current | Pointer to the {@link OH_Drawing_Typeface} object. |
| const OH_Drawing_FontArguments* fontArguments | Pointer to an {@link OH_Drawing_FontArguments} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Returns a pointer to the created {@link OH_Drawing_Typeface} object.  If a null pointer is returned, the creation fails. Possible causes are that no memory is available, the passed-in   path or fontArguments is NULL, or the existing OH_Drawing_FontArguments object does not support the  variation described in the font arguments. |

### OH_Drawing_TypefaceCreateFromStream()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromStream(OH_Drawing_MemoryStream* memoryStream, int32_t index)
```

**Description**

Creates an **OH_Drawing_Typeface** object through a memory stream. If the memory stream is an invalid font file, a null pointer is returned. After the memory stream is passed in, the ownership is transferred and you cannot release it. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **memoryStream** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_MemoryStream* memoryStream | Pointer to an {@link OH_Drawing_MemoryStream} object. |
| int32_t index | Index of the memory stream. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Returns a pointer to the created {@link OH_Drawing_Typeface} object. |

### OH_Drawing_TypefaceDestroy()

```c
void OH_Drawing_TypefaceDestroy(OH_Drawing_Typeface* typeface)
```

**Description**

Destroys an **OH_Drawing_Typeface** object and reclaims the memory occupied by the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Typeface* typeface | Pointer to an **OH_Drawing_Typeface** object. |

### OH_Drawing_FontArgumentsCreate()

```c
OH_Drawing_FontArguments* OH_Drawing_FontArgumentsCreate(void)
```

**Description**

Creates an **OH_Drawing_FontArguments** object. The font arguments are used to create an **<br>OH_Drawing_Typeface** object with custom attributes.

**Since**: 13

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_FontArguments* | Returns the pointer to the OH_Drawing_FontArguments object created. |

### OH_Drawing_FontArgumentsAddVariation()

```c
OH_Drawing_ErrorCode OH_Drawing_FontArgumentsAddVariation(OH_Drawing_FontArguments* fontArguments, const char* axis, float value)
```

**Description**

Adds a variation to an **OH_Drawing_FontArguments** object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontArguments* fontArguments | Pointer to an {@link OH_Drawing_FontArguments} object. |
| const char* axis | Pointer to the label of the variation. The value must contain four ASCII characters. The supported labels depend on the loaded font file. For example, **'wght'** is the font weight label. |
| float value | Value of the variation label. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either fontArguments or axis is NULL or the length of axis is  not 4. |

### OH_Drawing_FontArgumentsDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_FontArgumentsDestroy(OH_Drawing_FontArguments* fontArguments)
```

**Description**

Destroys an **OH_Drawing_FontArguments** object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontArguments* fontArguments | Pointer to an {@link OH_Drawing_FontArguments} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if fontArguments is NULL. |

### OH_Drawing_TypefaceIsBold()

```c
OH_Drawing_ErrorCode OH_Drawing_TypefaceIsBold(const OH_Drawing_Typeface* typeface, bool* isBold)
```

**Description**

Checks whether the typeface is bold.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Typeface* typeface | Pointer to the {@link OH_Drawing_Typeface} object. |
| bool* isBold | Whether the typeface is bold. It is used as an output parameter. **true** if the typeface is bold; **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if typeface or isBold is a null pointer. |

### OH_Drawing_TypefaceIsItalic()

```c
OH_Drawing_ErrorCode OH_Drawing_TypefaceIsItalic(const OH_Drawing_Typeface* typeface, bool* isItalic)
```

**Description**

Checks whether the typeface is italic.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Typeface* typeface | Pointer to the {@link OH_Drawing_Typeface} object. |
| bool* isItalic | Whether the typeface is italic. It is used as an output parameter. **true** if the typeface is italic; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if typeface or isItalic is a null pointer. |


