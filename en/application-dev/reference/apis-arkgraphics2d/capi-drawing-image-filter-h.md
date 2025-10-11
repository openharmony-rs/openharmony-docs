# drawing_image_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the image filter in the drawing module.

**File to include**: <native_drawing/drawing_image_filter.h>

**Library**: libnative_drawing.so

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode,OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateblur) | Creates an image filter with a given blur effect.|
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY,OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)](#oh_drawing_imagefiltercreateblurwithcrop) | Creates an image filter with a given blur effect.<br> You can pass a cropping rectangle to limit the blur effect to take effect only in the specified rectangular area of the image.​ |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter,OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreatefromcolorfilter) | Creates an **OH_Drawing_ImageFilter** object with a color filter effect. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateoffset) | Creates an offset filter to translate the input filter based on the specified vector.|
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_imagefiltercreatefromshadereffect) | Creates an **ImageFilter** object based on a shader.|
| [void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefilterdestroy) | Destroys an **OH_Drawing_ImageFilter** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_ImageFilterCreateBlur()

```
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode,OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an image filter with a given blur effect.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur to apply along the X axis. The value must be greater than 0.|
| float sigmaY | Standard deviation of the Gaussian blur to apply along the Y axis. The value must be greater than 0.|
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode).|
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Returns the pointer to the [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object created. If NULL is returned, the creation fails. The possible failure cause is that no memory is available.|

### OH_Drawing_ImageFilterCreateBlurWithCrop()

```
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)
```

**Description**

Creates an image filter with a given blur effect.

You can pass a cropping rectangle to limit the blur effect to take effect only in the specified rectangular area of the image.​

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur to apply along the X axis. The value must be greater than 0.0.|
| float sigmaY | Standard deviation of the Gaussian blur to apply along the Y axis. The value must be greater than 0.0.|
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode).|
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* input | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image.|
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangular region to be cropped. If NULL is passed in, the blur effect is directly applied to the entire image.|

**Return value**

| Type| Description|
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object created. If NULL is returned, the creation fails. The possible failure cause is that no memory is available.|

### OH_Drawing_ImageFilterCreateFromColorFilter()

```
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter,OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an **OH_Drawing_ImageFilter** object with a color filter effect. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* colorFilter | Pointer to an [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) object.|
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Returns the pointer to the [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object created. If NULL is returned, the creation fails. The possible failure cause is that no memory is available or **colorFilter** is NULL.|

### OH_Drawing_ImageFilterCreateOffset()

```
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an offset filter to translate the input filter based on the specified vector.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| float x | Distance to translate on the X axis.|
| float y | Distance to translate on the Y axis.|
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Filter to be translated. If NULL is passed in, the drawing result without the filtering effect is translated.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Returns the pointer to the [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object created. If NULL is returned, the creation fails. The possible failure cause is that no memory is available.|

### OH_Drawing_ImageFilterCreateFromShaderEffect()

```
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Creates an **ImageFilter** object based on a shader.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | Shader effect to be applied to the image.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | Returns the pointer to the [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object created. If NULL is returned, the creation fails. The possible failure cause is that no memory is available.|

### OH_Drawing_ImageFilterDestroy()

```
void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Destroys an **OH_Drawing_ImageFilter** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | Pointer to an [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object.|
