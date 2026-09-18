# drawing_bitmap.h

## Overview

This file declares the functions related to the bitmap in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_BitmapFormat](capi-drawing-oh-drawing-bitmapformat.md) | OH_Drawing_BitmapFormat | This struct describes the pixel format of a bitmap, including the color type and alpha type. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Bitmap* OH_Drawing_BitmapCreate(void)](#oh_drawing_bitmapcreate) | Creates an **OH_Drawing_Bitmap** object. |
| [void OH_Drawing_BitmapDestroy(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapdestroy) | Destroys an **OH_Drawing_Bitmap** object and reclaims the memory occupied by the object. |
| [OH_Drawing_Bitmap* OH_Drawing_BitmapCreateFromPixels(OH_Drawing_Image_Info* imageInfo, void* pixels, uint32_t rowBytes)](#oh_drawing_bitmapcreatefrompixels) | Creates an **OH_Drawing_Bitmap** object, with the address of the memory for storing the bitmap pixels set to the memory address that you applied for. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **imageInfo** or **pixels** is NULL or **rowBytes** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_BitmapBuild(OH_Drawing_Bitmap* bitmap, const uint32_t width, const uint32_t height, const OH_Drawing_BitmapFormat* bitmapFormat)](#oh_drawing_bitmapbuild) | Initializes the width and height of a bitmap and sets the pixel format for the bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **bitmap** or **bitmapFormat** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [uint32_t OH_Drawing_BitmapGetWidth(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetwidth) | Obtains the width of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [uint32_t OH_Drawing_BitmapGetHeight(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetheight) | Obtains the height of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ColorFormat OH_Drawing_BitmapGetColorFormat(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetcolorformat) | Obtains the pixel format of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_AlphaFormat OH_Drawing_BitmapGetAlphaFormat(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetalphaformat) | Obtains the alpha component of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void* OH_Drawing_BitmapGetPixels(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetpixels) | Obtains the pixel address of a bitmap. You can use this address to obtain the pixel data of the bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_BitmapGetImageInfo(OH_Drawing_Bitmap* bitmap, OH_Drawing_Image_Info* imageInfo)](#oh_drawing_bitmapgetimageinfo) | Obtains the image information of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **bitmap** or **imageInfo** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_BitmapReadPixels(OH_Drawing_Bitmap* bitmap, const OH_Drawing_Image_Info* dstInfo, void* dstPixels, size_t dstRowBytes, int32_t srcX, int32_t srcY)](#oh_drawing_bitmapreadpixels) | Reads pixels of a rectangle in a bitmap to the specified buffer. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If any of **bitmap**, **dstInfo**, and **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_BitmapGetRowBytes(OH_Drawing_Bitmap* bitmap, uint32_t* bytes)](#oh_drawing_bitmapgetrowbytes) | Gets the row bytes of the bitmap. |

## Function description

### OH_Drawing_BitmapCreate()

```c
OH_Drawing_Bitmap* OH_Drawing_BitmapCreate(void)
```

**Description**

Creates an **OH_Drawing_Bitmap** object.

**Since**: 8

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Bitmap* | Returns the pointer to the OH_Drawing_Bitmap object created. |

### OH_Drawing_BitmapDestroy()

```c
void OH_Drawing_BitmapDestroy(OH_Drawing_Bitmap* bitmap)
```

**Description**

Destroys an **OH_Drawing_Bitmap** object and reclaims the memory occupied by the object.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

### OH_Drawing_BitmapCreateFromPixels()

```c
OH_Drawing_Bitmap* OH_Drawing_BitmapCreateFromPixels(OH_Drawing_Image_Info* imageInfo, void* pixels, uint32_t rowBytes)
```

**Description**

Creates an **OH_Drawing_Bitmap** object, with the address of the memory for storing the bitmap pixels set to the memory address that you applied for. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **imageInfo** or **pixels** is NULL or **rowBytes** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Image_Info* imageInfo | Pointer to an {@link OH_Drawing_Image_Info} object. |
| void* pixels | Pointer to the start address of the memory for storing the bitmap pixels. You need to apply for the memory and ensure its validity. |
| uint32_t rowBytes | Number of bytes in each row of pixels. The value is invalid if it is less than or equal to 0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Bitmap* | Returns a pointer to the {@link OH_Drawing_Bitmap} object created. |

### OH_Drawing_BitmapBuild()

```c
void OH_Drawing_BitmapBuild(OH_Drawing_Bitmap* bitmap, const uint32_t width, const uint32_t height, const OH_Drawing_BitmapFormat* bitmapFormat)
```

**Description**

Initializes the width and height of a bitmap and sets the pixel format for the bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **bitmap** or **bitmapFormat** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |
| const uint32_t width | Width of the bitmap to be initialized. |
| const uint32_t height | Height of the bitmap to be initialized. |
| [const OH_Drawing_BitmapFormat](capi-drawing-oh-drawing-bitmapformat.md)* bitmapFormat | Pointer to the pixel format of the bitmap to be initialized, including the pixel color type and alpha type. |

### OH_Drawing_BitmapGetWidth()

```c
uint32_t OH_Drawing_BitmapGetWidth(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the width of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the width. |

### OH_Drawing_BitmapGetHeight()

```c
uint32_t OH_Drawing_BitmapGetHeight(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the height of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the height. |

### OH_Drawing_BitmapGetColorFormat()

```c
OH_Drawing_ColorFormat OH_Drawing_BitmapGetColorFormat(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the pixel format of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFormat | Returns the pixel format. For details about the supported formats, see {@link OH_Drawing_ColorFormat}. |

### OH_Drawing_BitmapGetAlphaFormat()

```c
OH_Drawing_AlphaFormat OH_Drawing_BitmapGetAlphaFormat(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the alpha component of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_AlphaFormat | Returns the alpha component. For details about the supported formats, see {@link OH_Drawing_AlphaFormat}. |

### OH_Drawing_BitmapGetPixels()

```c
void* OH_Drawing_BitmapGetPixels(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the pixel address of a bitmap. You can use this address to obtain the pixel data of the bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the pixel address. |

### OH_Drawing_BitmapGetImageInfo()

```c
void OH_Drawing_BitmapGetImageInfo(OH_Drawing_Bitmap* bitmap, OH_Drawing_Image_Info* imageInfo)
```

**Description**

Obtains the image information of a bitmap. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **bitmap** or **imageInfo** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to the {@link OH_Drawing_Bitmap} object. |
| OH_Drawing_Image_Info* imageInfo | Pointer to an {@link OH_Drawing_Image_Info} object. |

### OH_Drawing_BitmapReadPixels()

```c
bool OH_Drawing_BitmapReadPixels(OH_Drawing_Bitmap* bitmap, const OH_Drawing_Image_Info* dstInfo, void* dstPixels, size_t dstRowBytes, int32_t srcX, int32_t srcY)
```

**Description**

Reads pixels of a rectangle in a bitmap to the specified buffer. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If any of **bitmap**, **dstInfo**, and **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Pointer to the {@link OH_Drawing_Bitmap} object. |
| const OH_Drawing_Image_Info* dstInfo | Pointer to an {@link OH_Drawing_Image_Info} object. |
| void* dstPixels | Pointer to the buffer for storing the pixels read. |
| size_t dstRowBytes | Number of bytes in each row of the pixel data read. The value must be greater than or equal to the minimum number of bytes in each row in the **OH_Drawing_Image_Info** object. |
| int32_t srcX | Start X coordinate of the pixel data to read from the bitmap. The value must be less than the width of the bitmap. |
| int32_t srcY | Start Y coordinate of the pixel data to read from the bitmap. The value must be less than the height of the bitmap. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the pixels are read; returns false otherwise. |

### OH_Drawing_BitmapGetRowBytes()

```c
OH_Drawing_ErrorCode OH_Drawing_BitmapGetRowBytes(OH_Drawing_Bitmap* bitmap, uint32_t* bytes)
```

**Description**

Gets the row bytes of the bitmap.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Bitmap* bitmap | Indicates the pointer to an <b>OH_Drawing_Bitmap</b> object. |
| uint32_t* bytes | Indicates the row bytes of the bitmap. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if bitmap or bytes is nullptr. |


