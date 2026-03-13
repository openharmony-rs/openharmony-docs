# drawing_typeface.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the typeface in the drawing module.<br>Different platforms have their own default typefaces. You can also parse the .ttf file to obtain the typefaces specified by the third party, such as SimSun and SimHei.

**File to include**: <native_drawing/drawing_typeface.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateDefault(void)](#oh_drawing_typefacecreatedefault) | Creates a default **OH_Drawing_Typeface** object.|
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFile(const char* path, int index)](#oh_drawing_typefacecreatefromfile) | Creates an **OH_Drawing_Typeface** object through a file.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFileWithArguments(const char* path,const OH_Drawing_FontArguments* fontArguments)](#oh_drawing_typefacecreatefromfilewitharguments) | Creates an **OH_Drawing_Typeface** object with font arguments through a file.<br>If the **OH_Drawing_Typeface** object does not support the variation described in the font arguments, this function creates an **OH_Drawing_Typeface** object with the default font arguments.<br>In this case, this function provides the same capability as [OH_Drawing_TypefaceCreateFromFile](capi-drawing-typeface-h.md#oh_drawing_typefacecreatefromfile).|
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromCurrent(const OH_Drawing_Typeface* current,const OH_Drawing_FontArguments* fontArguments)](#oh_drawing_typefacecreatefromcurrent) | Creates an **OH_Drawing_Typeface** object with font arguments based on an existing **OH_Drawing_Typeface** object.|
| [OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromStream(OH_Drawing_MemoryStream* memoryStream, int32_t index)](#oh_drawing_typefacecreatefromstream) | Creates an **OH_Drawing_Typeface** object through a memory stream. If the memory stream is an invalid font file, a null pointer is returned. After the memory stream is passed in, the ownership is transferred and you cannot release it.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **memoryStream** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_TypefaceDestroy(OH_Drawing_Typeface* typeface)](#oh_drawing_typefacedestroy) | Destroys an **OH_Drawing_Typeface** object and reclaims the memory occupied by the object.|
| [OH_Drawing_FontArguments* OH_Drawing_FontArgumentsCreate(void)](#oh_drawing_fontargumentscreate) | Creates an **OH_Drawing_FontArguments** object. The font arguments are used to create an **OH_Drawing_Typeface** object with custom attributes.|
| [OH_Drawing_ErrorCode OH_Drawing_FontArgumentsAddVariation(OH_Drawing_FontArguments* fontArguments,const char* axis, float value)](#oh_drawing_fontargumentsaddvariation) | Adds a variation to an **OH_Drawing_FontArguments** object.|
| [OH_Drawing_ErrorCode OH_Drawing_FontArgumentsDestroy(OH_Drawing_FontArguments* fontArguments)](#oh_drawing_fontargumentsdestroy) | Destroys an **OH_Drawing_FontArguments** object.|
| [OH_Drawing_ErrorCode OH_Drawing_TypefaceIsBold(const OH_Drawing_Typeface* typeface, bool* isBold)](#oh_drawing_typefaceisbold) | Checks whether the typeface is bold.|
| [OH_Drawing_ErrorCode OH_Drawing_TypefaceIsItalic(const OH_Drawing_Typeface* typeface, bool* isItalic)](#oh_drawing_typefaceisitalic) | Checks whether the typeface is italic.|

## Function Description

### OH_Drawing_TypefaceCreateDefault()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateDefault(void)
```

**Description**

Creates a default **OH_Drawing_Typeface** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | Returns the pointer to the **OH_Drawing_Typeface** object created.|

### OH_Drawing_TypefaceCreateFromFile()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFile(const char* path, int index)
```

**Description**

Creates an **OH_Drawing_Typeface** object through a file.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const char* path | Pointer to the file path.|
| int index | File index.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | Returns a pointer to the created [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.|

### OH_Drawing_TypefaceCreateFromFileWithArguments()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromFileWithArguments(const char* path,const OH_Drawing_FontArguments* fontArguments)
```

**Description**

Creates an **OH_Drawing_Typeface** object with font arguments through a file.<br>If the **OH_Drawing_Typeface** object does not support the variation described in the font arguments, this function creates an **OH_Drawing_Typeface** object with the default font arguments.<br>In this case, this function provides the same capability as [OH_Drawing_TypefaceCreateFromFile](capi-drawing-typeface-h.md#oh_drawing_typefacecreatefromfile).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| const char* path | Pointer to the file path.|
| const [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md)* fontArguments | Pointer to an [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | Returns a pointer to the created [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.<br> If a null pointer is returned, the creation fails. Possible causes are that no memory is available, the passed-in **path** or **fontArguments** is NULL, or the path is invalid.|

### OH_Drawing_TypefaceCreateFromCurrent()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromCurrent(const OH_Drawing_Typeface* current,const OH_Drawing_FontArguments* fontArguments)
```

**Description**

Creates an **OH_Drawing_Typeface** object with font arguments based on an existing **OH_Drawing_Typeface** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* current | Pointer to the [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.|
| const [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md)* fontArguments | Pointer to an [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | Returns a pointer to the created [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.<br> If a null pointer is returned, the creation fails. Possible causes are that no memory is available, the passed-in **path** or **fontArguments** is NULL, or the existing **OH_Drawing_FontArguments** object does not support the variation described in the font arguments.|

### OH_Drawing_TypefaceCreateFromStream()

```c
OH_Drawing_Typeface* OH_Drawing_TypefaceCreateFromStream(OH_Drawing_MemoryStream* memoryStream, int32_t index)
```

**Description**

Creates an **OH_Drawing_Typeface** object through a memory stream. If the memory stream is an invalid font file, a null pointer is returned. After the memory stream is passed in, the ownership is transferred and you cannot release it.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **memoryStream** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)* memoryStream | Pointer to an [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md) object.|
| int32_t index | Index of the memory stream.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* | Returns a pointer to the created [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.|

### OH_Drawing_TypefaceDestroy()

```c
void OH_Drawing_TypefaceDestroy(OH_Drawing_Typeface* typeface)
```

**Description**

Destroys an **OH_Drawing_Typeface** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* typeface | Pointer to an **OH_Drawing_Typeface** object.|

### OH_Drawing_FontArgumentsCreate()

```c
OH_Drawing_FontArguments* OH_Drawing_FontArgumentsCreate(void)
```

**Description**

Creates an **OH_Drawing_FontArguments** object. The font arguments are used to create an **OH_Drawing_Typeface** object with custom attributes.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md)* | Returns the pointer to the **OH_Drawing_FontArguments** object created.|

### OH_Drawing_FontArgumentsAddVariation()

```c
OH_Drawing_ErrorCode OH_Drawing_FontArgumentsAddVariation(OH_Drawing_FontArguments* fontArguments,const char* axis, float value)
```

**Description**

Adds a variation to an **OH_Drawing_FontArguments** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md)* fontArguments | Pointer to an [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md) object.|
| const char* axis | Pointer to the label of the variation. The value must contain four ASCII characters. The supported labels depend on the loaded font file. For example, **'wght'** is the font weight label.|
| float value | Value of the variation label.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **fontArguments** or **axis** is NULL or the length of **axis** is not 4.|

### OH_Drawing_FontArgumentsDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_FontArgumentsDestroy(OH_Drawing_FontArguments* fontArguments)
```

**Description**

Destroys an **OH_Drawing_FontArguments** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md)* fontArguments | Pointer to an [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **fontArguments** is NULL.|


### OH_Drawing_TypefaceIsBold()

```c
OH_Drawing_ErrorCode OH_Drawing_TypefaceIsBold(const OH_Drawing_Typeface* typeface, bool* isBold)
```

**Description**

Checks whether the typeface is bold.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* typeface | Pointer to the [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.|
| bool* isBold | Whether the typeface is bold. It is used as an output parameter. **true** if the typeface is bold; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **typeface** or **isBold** is a null pointer.|

### OH_Drawing_TypefaceIsItalic()

```c
OH_Drawing_ErrorCode OH_Drawing_TypefaceIsItalic(const OH_Drawing_Typeface* typeface, bool* isItalic)
```

**Description**

Checks whether the typeface is italic.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)* typeface | Pointer to the [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) object.|
| bool* isItalic | Whether the typeface is italic. It is used as an output parameter. **true** if the typeface is italic; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **typeface** or **isItalic** is a null pointer.|
