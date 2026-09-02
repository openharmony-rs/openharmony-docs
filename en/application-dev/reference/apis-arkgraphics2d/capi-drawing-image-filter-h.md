# drawing_image_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T08:29:47.288Z pushedAt=2026-08-31T07:29:38.287Z -->

## Overview

Declares functions related to image filter objects in the drawing module. It supports creating various image filter effects such as blur, color transformation, offset, and shader-based filters, and supports destroying filter objects. It is applicable to scenarios such as image processing and visual effect enhancement.<br>This module adopts a single-thread model policy, and the caller is responsible for managing thread safety and context state switching.

**File to include**: <native_drawing/drawing_image_filter.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateblur) | Creates an image filter with a blur effect. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it. Otherwise, a memory leak occurs. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)](#oh_drawing_imagefiltercreateblurwithcrop) | Creates an image filter with a blur effect. A crop rectangle can be passed in to restrict the blur effect to the specified rectangular area of the image. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it. Otherwise, a memory leak occurs. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreatefromcolorfilter) | Creates an image filter with a color transformation effect. This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). OH_DRAWING_ERROR_INVALID_PARAMETER is returned when colorFilter is NULL; an error code is also generated when insufficient available memory causes memory allocation to fail. Check and ensure that the passed colorFilter is a valid pointer to a color filter object. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it. Otherwise, a memory leak occurs. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateoffset) | Creates an offset filter that translates the input filter by the specified vector. It is suitable for scenarios such as creating shadow offset effects or displacement animations. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it. Otherwise, a memory leak occurs. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_imagefiltercreatefromshadereffect) | Creates an image filter based on a shader. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it. Otherwise, a memory leak occurs. |
| [void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefilterdestroy) | Destroys the image filter object and reclaims the memory occupied by the object. |

## Function Description

### OH_Drawing_ImageFilterCreateBlur()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an image filter with a blur effect. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it; otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur along the x-axis direction, in px. The value does not take effect if it is less than or equal to 0. |
| float sigmaY | Standard deviation of the Gaussian blur along the y-axis direction, in px. The value does not take effect if it is less than or equal to 0. |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode used to control the image filter effect at the image boundary. |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to the input filter to be composited with the current image filter. If it is NULL, the current image filter is applied directly to the original image. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | The function returns a pointer to the created image filter object [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md). If NULL is returned, the creation fails, possibly due to insufficient available memory. |

### OH_Drawing_ImageFilterCreateBlurWithCrop()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)
```

**Description**

Creates an image filter with a given blur effect.

Supports passing in a crop rectangle to limit the blur effect to a specified rectangular area of the image. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it; otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur along the x-axis direction, in px. The value must be greater than 0.0. A value less than or equal to 0 does not take effect. |
| float sigmaY | Standard deviation of the Gaussian blur along the y-axis direction, in px. The value must be greater than 0.0. A value less than or equal to 0 does not take effect. |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode used to control the image filter effect at the image boundary. |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* input | Pointer to the input filter to be superimposed with the current image filter. If this parameter is NULL, the current image filter is directly applied to the original image. |
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangular region to be cropped. If NULL is passed in, the blur effect is directly applied to the entire image.|

**Return value**

| Type| Description|
| -- | -- |
| OH_Drawing_ImageFilter* | Pointer to the created image filter object [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md). If NULL is returned, the creation fails; the possible cause is insufficient available memory. |

### OH_Drawing_ImageFilterCreateFromColorFilter()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an image filter with a color transformation effect. This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If colorFilter is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. An error code is also generated when memory allocation fails due to insufficient available memory. Ensure that the passed colorFilter is a valid color filter object pointer. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it; otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* colorFilter | Pointer to the color filter object [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) with a color transformation effect. If it is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Input filter to be superimposed with the current image filter. If it is NULL, the current image filter is applied directly to the original image. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Pointer to the created image filter object [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md). If NULL is returned, the creation fails. The possible cause is insufficient available memory or a NULL colorFilter. |

### OH_Drawing_ImageFilterCreateOffset()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an offset filter that translates the input filter by a specified vector. It is applicable to scenarios such as creating shadow offset effects or displacement animations. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it; otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| float x | Translation distance along the x-axis. |
| float y | Translation distance along the y-axis. |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to the filter to be translated. If NULL, the drawing result without filtering effect is translated. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Pointer to the created image filter object [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md). If NULL is returned, the creation fails, possibly due to insufficient available memory. |

### OH_Drawing_ImageFilterCreateFromShaderEffect()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Creates an image filter based on a shader. After using the image filter object created by this function, you must call [OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy) to destroy it; otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | Shader effect to be applied to the image.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Pointer to the created image filter object [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md). If NULL is returned, the creation fails. The possible causes are insufficient available memory or a NULL shaderEffect. |

### OH_Drawing_ImageFilterDestroy()

```c
void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Destroys an image filter object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to an [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object.|