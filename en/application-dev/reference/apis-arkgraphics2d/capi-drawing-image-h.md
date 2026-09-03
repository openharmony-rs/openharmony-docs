# drawing_image.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:31:59.034Z pushedAt=2026-08-31T07:45:21.843Z -->

## Overview

This file declares the functions related to images.<br>This module uses a single-thread model, and the caller must manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_image.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Image* OH_Drawing_ImageCreate(void)](#oh_drawing_imagecreate) | Creates an image object that describes a two-dimensional pixel array to be drawn. After use, you must call [OH_Drawing_ImageDestroy](#oh_drawing_imagedestroy) to destroy the image object and reclaim the memory; otherwise, a memory leak occurs. |
| [void OH_Drawing_ImageDestroy(OH_Drawing_Image* image)](#oh_drawing_imagedestroy) | Destroys the image object and reclaims the memory occupied by the object. It is used together with [OH_Drawing_ImageCreate](#oh_drawing_imagecreate) to destroy the image object created by the latter. After destruction, the image object pointer should not be used again; otherwise, undefined behavior may occur. |
| [bool OH_Drawing_ImageBuildFromBitmap(OH_Drawing_Image* image, OH_Drawing_Bitmap* bitmap)](#oh_drawing_imagebuildfrombitmap) | Builds the image object content from a bitmap, sharing or copying the bitmap pixels. In scenarios where existing bitmap data needs to be drawn as an image on a canvas, this interface can be used to construct the bitmap data into an image object. If the bitmap is marked as immutable state, the pixel memory is shared; if the bitmap is not marked as immutable state (that is, the bitmap is in mutable state), the pixel memory will be copied.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns the error code OH_DRAWING_ERROR_INVALID_PARAMETER when either image or bitmap is NULL. |
| [int32_t OH_Drawing_ImageGetWidth(OH_Drawing_Image* image)](#oh_drawing_imagegetwidth) | Obtains the image width in physical pixels (px), that is, the pixel count per row.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns the error code OH_DRAWING_ERROR_INVALID_PARAMETER when image is NULL. |
| [int32_t OH_Drawing_ImageGetHeight(OH_Drawing_Image* image)](#oh_drawing_imagegetheight) | Obtains the image height in physical pixels (px), that is, the number of pixel rows.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns the error code OH_DRAWING_ERROR_INVALID_PARAMETER when image is NULL. |
| [void OH_Drawing_ImageGetImageInfo(OH_Drawing_Image* image, OH_Drawing_Image_Info* imageInfo)](#oh_drawing_imagegetimageinfo) | Obtains the image information. After this interface is called, the passed-in image information object is filled.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns the error code OH_DRAWING_ERROR_INVALID_PARAMETER when either image or imageInfo is NULL. |

## Function Description

### OH_Drawing_ImageCreate()

```c
OH_Drawing_Image* OH_Drawing_ImageCreate(void)
```

**Description**

Creates an image object that describes a two-dimensional pixel array to be drawn. After use, you must call [OH_Drawing_ImageDestroy](#oh_drawing_imagedestroy) to destroy the image object and reclaim the memory. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* | Pointer to the created image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md). |

### OH_Drawing_ImageDestroy()

```c
void OH_Drawing_ImageDestroy(OH_Drawing_Image* image)
```

**Description**

Destroys an image object and reclaims the memory occupied by the object. It is used together with [OH_Drawing_ImageCreate](#oh_drawing_imagecreate) to destroy the image object created by the latter. After destruction, the image object pointer should not be used again. Otherwise, undefined behavior may occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) created by [OH_Drawing_ImageCreate](#oh_drawing_imagecreate), used to destroy the image object and reclaim its memory. After destruction, this pointer should not be used again; otherwise, undefined behavior may occur. |

### OH_Drawing_ImageBuildFromBitmap()

```c
bool OH_Drawing_ImageBuildFromBitmap(OH_Drawing_Image* image, OH_Drawing_Bitmap* bitmap)
```

**Description**

Constructs the content of an image object from a bitmap, sharing or copying the bitmap pixels. In scenarios where existing bitmap data needs to be drawn as an image on a canvas, you can use this interface to construct the bitmap data into an image object. If the bitmap is marked as immutable, the pixel memory is shared. If the bitmap is not marked as immutable (that is, the bitmap is mutable), the pixel memory is copied.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either image or bitmap is NULL, the error code OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md), used as the target object to receive the image object content constructed from the bitmap. When the bitmap is marked as immutable state, the pixel memory of the image object is shared with the bitmap instead of being copied independently. |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to the bitmap object [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md), used as the source data to construct the image object content. If the bitmap is marked as immutable state, the pixel memory is shared; if the bitmap is not marked as immutable state (that is, the bitmap is in mutable state), the pixel memory will be copied. |

**Returns**

| Type| Description|
| -- | -- |
| bool | true indicates that the image content is constructed successfully, and false indicates that the image content fails to be constructed. |

### OH_Drawing_ImageGetWidth()

```c
int32_t OH_Drawing_ImageGetWidth(OH_Drawing_Image* image)
```

**Description**

Obtains the width of an image, in physical pixels (px), that is, the number of pixels per row.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If image is NULL, the error code OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) whose width is to be obtained. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | The function returns the image width, in physical pixels (px), that is, the number of pixels per row. |

### OH_Drawing_ImageGetHeight()

```c
int32_t OH_Drawing_ImageGetHeight(OH_Drawing_Image* image)
```

**Description**

Obtains the height of an image, in physical pixels (px), that is, the number of pixel rows.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If image is NULL, the error code OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) whose height is to be obtained. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Image height, in physical pixels (px), that is, the number of pixel rows. |

### OH_Drawing_ImageGetImageInfo()

```c
void OH_Drawing_ImageGetImageInfo(OH_Drawing_Image* image, OH_Drawing_Image_Info* imageInfo)
```

**Description**

Obtains image information. After this interface is called, the passed image information object is filled.<br>This interface generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either image or imageInfo is NULL, the error code OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the image object [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) from which the image information is obtained, serving as the data source of the image information. |
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* imageInfo | Pointer to the image information object [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md), used as an output parameter to receive the obtained image information. After this interface is called, the object is populated. Developers can create it by declaring the [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) struct. |