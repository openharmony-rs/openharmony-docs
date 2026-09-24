# drawing_image_filter.h

## Overview

This file declares the functions related to the image filter in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateblur) | Creates an image filter with a given blur effect. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)](#oh_drawing_imagefiltercreateblurwithcrop) | Creates an image filter with a given blur effect. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreatefromcolorfilter) | Creates an **OH_Drawing_ImageFilter** object with a color filter effect. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER**<br>is returned. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateoffset) | Creates an offset filter to translate the input filter based on the specified vector. |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_imagefiltercreatefromshadereffect) | Creates an **ImageFilter** object based on a shader. |
| [void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefilterdestroy) | Destroys an **OH_Drawing_ImageFilter** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_ImageFilterCreateBlur()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an image filter with a given blur effect.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur to apply along the X axis. The value must be greater than 0. |
| float sigmaY | Standard deviation of the Gaussian blur to apply along the Y axis. The value must be greater than 0. |
| OH_Drawing_TileMode tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| OH_Drawing_ImageFilter* imageFilter | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the <b>OH_Drawing_ImageFilter</b> object created.  If nullptr is returned, the creation fails.  The possible cause of the failure is that the available memory is empty. |

### OH_Drawing_ImageFilterCreateBlurWithCrop()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)
```

**Description**

Creates an image filter with a given blur effect.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| float sigmaX | Standard deviation of the Gaussian blur to apply along the X axis. The value must be greater than 0.0. |
| float sigmaY | Standard deviation of the Gaussian blur to apply along the Y axis. The value must be greater than 0.0. |
| OH_Drawing_TileMode tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| OH_Drawing_ImageFilter* input | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image. |
| const OH_Drawing_Rect* rect | Pointer to the rectangular region to be cropped. If NULL is passed in, the blur effect is directly applied to the entire image. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the <b>OH_Drawing_ImageFilter</b> object created. |

### OH_Drawing_ImageFilterCreateFromColorFilter()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an **OH_Drawing_ImageFilter** object with a color filter effect. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER**<br>is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ColorFilter* colorFilter | Pointer to an [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) object. |
| OH_Drawing_ImageFilter* imageFilter | Pointer to the filter to which the image filter will be applied. If NULL is passed in, the image filter is directly applied to the original image. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the <b>OH_Drawing_ImageFilter</b> object created.  If nullptr is returned, the creation fails.  The possible cause of the failure is that the available memory is empty or  a nullptr <b>OH_Drawing_ColorFilter</b> is passed. |

### OH_Drawing_ImageFilterCreateOffset()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Creates an offset filter to translate the input filter based on the specified vector.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| float x | Distance to translate on the X axis. |
| float y | Distance to translate on the Y axis. |
| OH_Drawing_ImageFilter* imageFilter | Filter to be translated. If NULL is passed in, the drawing result without the filtering effect is translated. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the <b>OH_Drawing_ImageFilter</b> object created.  If nullptr is returned, the creation fails.  The possible cause of the failure is that the available memory is empty. |

### OH_Drawing_ImageFilterCreateFromShaderEffect()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Creates an **ImageFilter** object based on a shader.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* shaderEffect | Shader effect to be applied to the image. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ImageFilter* | Returns the pointer to the <b>OH_Drawing_ImageFilter</b> object created.  If nullptr is returned, the creation fails.  The possible cause of the failure is that the available memory is empty or  a nullptr <b>OH_Drawing_ShaderEffect</b> is passed. |

### OH_Drawing_ImageFilterDestroy()

```c
void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Destroys an **OH_Drawing_ImageFilter** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ImageFilter* imageFilter | Pointer to an [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object. |


