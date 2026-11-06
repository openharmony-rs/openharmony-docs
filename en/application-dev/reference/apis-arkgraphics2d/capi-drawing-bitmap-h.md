# drawing_bitmap.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:21:40.179Z pushedAt=2026-08-31T03:16:48.812Z -->

## Overview

The file defines bitmap-related functions, supporting operations such as creating and destroying bitmaps, initializing the width, height, and pixel format, obtaining the bitmap width, height, row bytes, pixel storage format, alpha format, pixel address, and bitmap information, and reading bitmap pixel data into a specified memory buffer.<br>This module uses a single-thread model policy, and the caller is required to manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include**: <native_drawing/drawing_bitmap.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_BitmapFormat](capi-drawing-oh-drawing-bitmapformat.md) | OH_Drawing_BitmapFormat | Defines the pixel format of a bitmap, including the color type and alpha type.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap* OH_Drawing_BitmapCreate(void)](#oh_drawing_bitmapcreate) | Creates a bitmap object. After the bitmap object created by this API is used, [OH_Drawing_BitmapDestroy](#oh_drawing_bitmapdestroy) must be called to destroy it and release the memory. Otherwise, a memory leak occurs. |
| [void OH_Drawing_BitmapDestroy(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapdestroy) | Destroys a bitmap object and reclaims the memory occupied by the object. This API must be used together with [OH_Drawing_BitmapCreate](#oh_drawing_bitmapcreate) or [OH_Drawing_BitmapCreateFromPixels](#oh_drawing_bitmapcreatefrompixels) to release the created bitmap object and avoid memory leaks. |
| [OH_Drawing_Bitmap* OH_Drawing_BitmapCreateFromPixels(OH_Drawing_Image_Info* imageInfo, void* pixels, uint32_t rowBytes)](#oh_drawing_bitmapcreatefrompixels) | Creates a bitmap object and sets the memory address for storing the bitmap pixels to the memory address requested by the developer. After the bitmap object created by this API is used, [OH_Drawing_BitmapDestroy](#oh_drawing_bitmapdestroy) must be called to destroy it and release the memory. Otherwise, a memory leak occurs.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If either imageInfo or pixels is NULL, or rowBytes is 0, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| [void OH_Drawing_BitmapBuild(OH_Drawing_Bitmap* bitmap, const uint32_t width, const uint32_t height, const OH_Drawing_BitmapFormat* bitmapFormat)](#oh_drawing_bitmapbuild) | Initializes the width and height of a bitmap object and sets the pixel format for the bitmap.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If either bitmap or bitmapFormat is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| [uint32_t OH_Drawing_BitmapGetWidth(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetwidth) | Obtains the width of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_BitmapGetHeight(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetheight) | Obtains the height of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_BitmapGetRowBytes(OH_Drawing_Bitmap* bitmap, uint32_t* bytes)](#oh_drawing_bitmapgetrowbytes) | Obtains the number of bytes per row of the specified bitmap. |
| [OH_Drawing_ColorFormat OH_Drawing_BitmapGetColorFormat(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetcolorformat) | Obtains the pixel format of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_AlphaFormat OH_Drawing_BitmapGetAlphaFormat(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetalphaformat) | Obtains the alpha component of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void* OH_Drawing_BitmapGetPixels(OH_Drawing_Bitmap* bitmap)](#oh_drawing_bitmapgetpixels) | Obtains the pixel address of a bitmap. You can use this address to obtain the pixel data of the bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BitmapGetImageInfo(OH_Drawing_Bitmap* bitmap, OH_Drawing_Image_Info* imageInfo)](#oh_drawing_bitmapgetimageinfo) | Obtains the image information of the specified bitmap, including the width, height, color type, and alpha type.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If either bitmap or imageInfo is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| [bool OH_Drawing_BitmapReadPixels(OH_Drawing_Bitmap* bitmap, const OH_Drawing_Image_Info* dstInfo, void* dstPixels, size_t dstRowBytes, int32_t srcX, int32_t srcY)](#oh_drawing_bitmapreadpixels) | Reads the pixel data of a rectangular area in the bitmap into the specified memory buffer.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If any of bitmap, dstInfo, or dstPixels is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |

## Function Description

### OH_Drawing_BitmapCreate()

```c
OH_Drawing_Bitmap* OH_Drawing_BitmapCreate(void)
```

**Description**

Used to create a bitmap object. After the bitmap object created by this method is no longer needed, [OH_Drawing_BitmapDestroy](#oh_drawing_bitmapdestroy) must be called to destroy it and release the memory. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* | Pointer to the created bitmap object. |

### OH_Drawing_BitmapDestroy()

```c
void OH_Drawing_BitmapDestroy(OH_Drawing_Bitmap* bitmap)
```

**Description**

Used to destroy a bitmap object and reclaim the memory occupied by the object. It should be used together with [OH_Drawing_BitmapCreate](#oh_drawing_bitmapcreate) or [OH_Drawing_BitmapCreateFromPixels](#oh_drawing_bitmapcreatefrompixels) to release the created bitmap object and avoid memory leaks.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

### OH_Drawing_BitmapCreateFromPixels()

```c
OH_Drawing_Bitmap* OH_Drawing_BitmapCreateFromPixels(OH_Drawing_Image_Info* imageInfo, void* pixels, uint32_t rowBytes)
```

**Description**

Used to create a bitmap object and set the memory address for storing bitmap pixels to the memory address requested by the developer. After the bitmap object created by this method is no longer needed, [OH_Drawing_BitmapDestroy](#oh_drawing_bitmapdestroy) must be called to destroy it and release the memory. Otherwise, a memory leak occurs.<br>This API may generate an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either imageInfo or pixels is NULL, or rowBytes is 0, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* imageInfo | Pointer to the image information object [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md), used to specify the size and pixel format information for creating the bitmap. |
| void* pixels | Pointer to the start address of the pixel storage memory. The memory is allocated by the developer and must remain valid and sufficiently large while the bitmap is in use. The minimum required memory size is rowBytes × the height value in imageInfo. |
| uint32_t rowBytes | Number of bytes of pixel data per row. The value 0 is invalid. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* | Returns a pointer to the [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md) object created.|

### OH_Drawing_BitmapBuild()

```c
void OH_Drawing_BitmapBuild(OH_Drawing_Bitmap* bitmap, const uint32_t width, const uint32_t height, const OH_Drawing_BitmapFormat* bitmapFormat)
```

**Description**

Initializes the width and height of a bitmap and sets the pixel format for the bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **bitmap** or **bitmapFormat** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|
| const uint32_t width | Width of the bitmap to be initialized, in physical pixels (px). The value must be greater than 0. |
| const uint32_t height | Height of the bitmap to be initialized, in physical pixels (px). The value must be greater than 0. |
| const [OH_Drawing_BitmapFormat](capi-drawing-oh-drawing-bitmapformat.md)* bitmapFormat | Pointer to the pixel format of the bitmap to be initialized, including the pixel color type and alpha type.|

### OH_Drawing_BitmapGetWidth()

```c
uint32_t OH_Drawing_BitmapGetWidth(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the width of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | The function returns the width of the bitmap, in physical pixels (px). |

### OH_Drawing_BitmapGetHeight()

```c
uint32_t OH_Drawing_BitmapGetHeight(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the height of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Height of the bitmap, in physical pixels (px). |

### OH_Drawing_BitmapGetRowBytes()

```c
OH_Drawing_ErrorCode OH_Drawing_BitmapGetRowBytes(OH_Drawing_Bitmap* bitmap, uint32_t* bytes)
```

**Description**

Obtains the number of bytes per row of the specified bitmap.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |
| uint32_t* bytes | Pointer to a uint32_t variable, used as an output parameter to receive the number of bytes per row of the bitmap. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if bitmap or bytes is NULL. |

### OH_Drawing_BitmapGetColorFormat()

```c
OH_Drawing_ColorFormat OH_Drawing_BitmapGetColorFormat(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the pixel format of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFormat](capi-drawing-types-h.md#oh_drawing_colorformat) | Returns the pixel format. For details about the supported formats, see [OH_Drawing_ColorFormat](capi-drawing-types-h.md#oh_drawing_colorformat).|

### OH_Drawing_BitmapGetAlphaFormat()

```c
OH_Drawing_AlphaFormat OH_Drawing_BitmapGetAlphaFormat(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the alpha component of a bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_AlphaFormat](capi-drawing-types-h.md#oh_drawing_alphaformat) | Returns the alpha component. For details about the supported formats, see [OH_Drawing_AlphaFormat](capi-drawing-types-h.md#oh_drawing_alphaformat).|

### OH_Drawing_BitmapGetPixels()

```c
void* OH_Drawing_BitmapGetPixels(OH_Drawing_Bitmap* bitmap)
```

**Description**

Obtains the pixel address of a bitmap. You can use this address to obtain the pixel data of the bitmap.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

**Returns**

| Type| Description|
| -- | -- |
| void* | Returns the pixel address.|

### OH_Drawing_BitmapGetImageInfo()

```c
void OH_Drawing_BitmapGetImageInfo(OH_Drawing_Bitmap* bitmap, OH_Drawing_Image_Info* imageInfo)
```

**Description**

Obtains the image information of the specified bitmap, including the width, height, color type, and alpha type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either bitmap or imageInfo is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to the [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md) object.|
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* imageInfo | Pointer to the image information object [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md). Used as an output parameter to receive the obtained image information. |

### OH_Drawing_BitmapReadPixels()

```c
bool OH_Drawing_BitmapReadPixels(OH_Drawing_Bitmap* bitmap, const OH_Drawing_Image_Info* dstInfo, void* dstPixels, size_t dstRowBytes, int32_t srcX, int32_t srcY)
```

**Description**

Reads pixels of a rectangle in a bitmap to the specified buffer.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **bitmap**, **dstInfo**, and **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to the bitmap object. |
| const [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* dstInfo | Pointer to the target image information object [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md), which specifies the format information of the target pixels and the width and height of the region to read. |
| void* dstPixels | Pointer to the start address of the memory area for storing the target pixels. The memory is allocated by the developer and must be large enough and valid. The minimum required buffer size is dstRowBytes multiplied by the height value in dstInfo. |
| size_t dstRowBytes | Number of bytes per row of the target pixel data. It must be greater than or equal to the minimum number of bytes per row in the image information object, which is determined by the width and color type of the target region. |
| int32_t srcX | Start x-coordinate for reading pixel data from the source bitmap, in physical pixels (px). The value must be less than the width of the source bitmap. |
| int32_t srcY | Start y-coordinate for reading pixel data from the source bitmap, in physical pixels (px). The value must be less than the height of the source bitmap. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Result indicating whether the API call succeeds. true indicates that the read succeeds, and false indicates that the read fails. |