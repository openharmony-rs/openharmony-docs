# drawing_shader_effect.h

## Overview

This file declares the functions related to the shader effect in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) | OH_Drawing_TileMode | Defines an enum for the tile modes of the shader effect. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateColorShader(const uint32_t color)](#oh_drawing_shadereffectcreatecolorshader) | Creates an **OH_Drawing_ShaderEffect** object with a single color. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradient(const OH_Drawing_Point* startPt, const OH_Drawing_Point* endPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreatelineargradient) | Creates a **ShaderEffect** object that generates a linear gradient between two points. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix(const OH_Drawing_Point2D* startPt, const OH_Drawing_Point2D* endPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatelineargradientwithlocalmatrix) | Creates a **ShaderEffect** object that generates a linear gradient between two points. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradient(const OH_Drawing_Point* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreateradialgradient) | Creates an **OH_Drawing_ShaderEffect** object that generates a radial gradient based on the center and radius of a circle. The radial gradient transitions colors from the center to the ending shape in a radial manner. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix(const OH_Drawing_Point2D* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreateradialgradientwithlocalmatrix) | Creates an **OH_Drawing_ShaderEffect** object that generates a radial gradient based on the center and radius of a circle. The radial gradient transitions colors from the center to the ending shape in a radial manner. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix(const OH_Drawing_Point* centerPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatesweepgradientwithlocalmatrix) | Creates an **OH_Drawing_ShaderEffect** object that generates a sweep gradient based on the matrix transformation at the given center. A sweep gradient paints a gradient in a sweeping arc ranging from 0° to 360°. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradient(const OH_Drawing_Point* centerPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreatesweepgradient) | Creates an **OH_Drawing_ShaderEffect** object that generates a sweep gradient based on the center. A sweep gradient paints a gradient in a sweeping arc ranging from 0° to 360°. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateImageShader(OH_Drawing_Image* image, OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreateimageshader) | Creates an **OH_Drawing_ShaderEffect** object for an image shader. You are advised not to use the function for the canvas of the capture type because it affects the performance. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **image** or **samplingOptions** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If either **tileX** or **tileY** is not set to one of the enumerated values, **<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreatePixelMapShader(OH_Drawing_PixelMap* pixelMap, OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatepixelmapshader) | Creates a PixelMap shader object. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateTwoPointConicalGradient(const OH_Drawing_Point2D* startPt, float startRadius, const OH_Drawing_Point2D* endPt, float endRadius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatetwopointconicalgradient) | Creates an **OH_Drawing_ShaderEffect** object that generates a gradient between two given circles. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateCompose(OH_Drawing_ShaderEffect* dst, OH_Drawing_ShaderEffect* src, OH_Drawing_BlendMode mode)](#oh_drawing_shadereffectcreatecompose) | Creates a shader by blending two existing shaders in a certain way. |
| [void OH_Drawing_ShaderEffectDestroy(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_shadereffectdestroy) | Destroys an **OH_Drawing_ShaderEffect** object and reclaims the memory occupied by the object. |

## Enum type description

### OH_Drawing_TileMode

```c
enum OH_Drawing_TileMode
```

**Description**

Defines an enum for the tile modes of the shader effect.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

| Enum item | Description |
| -- | -- |
| CLAMP | Replicates the edge color if the shader effect draws outside of its original boundary. |
| REPEAT | Repeats the shader effect's image in both horizontal and vertical directions. |
| MIRROR | Repeats the shader effect's image in both horizontal and vertical directions, alternating mirror images. |
| DECAL | Renders the shader effect's image only within the original boundary, and returns transparent black elsewhere. |


## Function description

### OH_Drawing_ShaderEffectCreateColorShader()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateColorShader(const uint32_t color)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object with a single color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const uint32_t color | Color in the ARGB format. The value is a 32-bit unsigned integer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created. If NULL is returned, the creation  fails. The possible failure cause is that no memory is available. |

### OH_Drawing_ShaderEffectCreateLinearGradient()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradient(const OH_Drawing_Point* startPt, const OH_Drawing_Point* endPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**Description**

Creates a **ShaderEffect** object that generates a linear gradient between two points. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point* startPt | Start point. |
| const OH_Drawing_Point* endPt | End point. |
| const uint32_t* colors | Colors to distribute between the two points. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed between the start point and end point. |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the OH_Drawing_ShaderEffect object created. |

### OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix(const OH_Drawing_Point2D* startPt, const OH_Drawing_Point2D* endPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates a **ShaderEffect** object that generates a linear gradient between two points. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point2D* startPt | Start point. |
| const OH_Drawing_Point2D* endPt | End point. |
| const uint32_t* colors | Colors to distribute between the two points. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed between the start point and end point. |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_Matrix* matrix | Matrix applied on the shader effect. If **matrix** is NULL, an identity matrix is applied by default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created. If NULL is returned, the creation  fails. The possible failure cause is that no memory is available or at least one of the parameters startPt,   endPt, and colors is NULL. |

### OH_Drawing_ShaderEffectCreateRadialGradient()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradient(const OH_Drawing_Point* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object that generates a radial gradient based on the center and radius of a circle. The radial gradient transitions colors from the center to the ending shape in a radial manner. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point* centerPt | Center of the circle. |
| float radius | Radius of the gradient. The value should be a non-negative number. |
| const uint32_t* colors | Colors to distribute in the radial direction. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed in the radial direction. |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the OH_Drawing_ShaderEffect object created. |

### OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix(const OH_Drawing_Point2D* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object that generates a radial gradient based on the center and radius of a circle. The radial gradient transitions colors from the center to the ending shape in a radial manner. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point2D* centerPt | Center of the circle. |
| float radius | Radius of the gradient. |
| const uint32_t* colors | Colors to distribute in the radial direction. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed in the radial direction. |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_Matrix* matrix | Matrix applied on the shader effect. If **matrix** is NULL, an identity matrix is applied by default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created. If NULL is returned, the creation  fails. The possible failure cause is that no memory is available or at least one of the parameters centerPt and   colors is NULL. |

### OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix(const OH_Drawing_Point* centerPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object that generates a sweep gradient based on the matrix transformation at the given center. A sweep gradient paints a gradient in a sweeping arc ranging from 0° to 360°.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point* centerPt | Center of the circle. |
| const uint32_t* colors | Colors to distribute between the two points. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed between the start angle (0°) and end angle (360°). |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_Matrix* matrix | Matrix applied on the shader effect. If **matrix** is NULL, an identity matrix is applied by default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created.  A null pointer is returned if any of the following conditions is met:  - The available memory is empty.  - centerPt or colors is NULL.  - The value of tileMode is out of the enumerated value range. |

### OH_Drawing_ShaderEffectCreateSweepGradient()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradient(const OH_Drawing_Point* centerPt, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object that generates a sweep gradient based on the center. A sweep gradient paints a gradient in a sweeping arc ranging from 0° to 360°. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **centerPt** or **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point* centerPt | Center of the circle. |
| const uint32_t* colors | Colors to distribute between the two points. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed between the start angle (0°) and end angle (360°). |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created.  A null pointer is returned if any of the following conditions is met:  - The available memory is empty.  - centerPt or colors is NULL.  - The value of tileMode is out of the enumerated value range. |

### OH_Drawing_ShaderEffectCreateImageShader()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateImageShader(OH_Drawing_Image* image, OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object for an image shader. You are advised not to use the function for the canvas of the capture type because it affects the performance. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **image** or **samplingOptions** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If either **tileX** or **tileY** is not set to one of the enumerated values, **<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Image* image | Pointer to the [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) object. |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileX | Tile mode of the shader effect in the horizontal direction. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileY | Tile mode of the shader effect in the vertical direction. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. If the pointer array is empty, the identity matrix is passed in. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created.  A null pointer is returned if any of the following conditions is met:  - The available memory is empty.  - image or samplingOptions is NULL.  - The value of tileX or tileY is out of the enumerated value range. |

### OH_Drawing_ShaderEffectCreatePixelMapShader()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreatePixelMapShader(OH_Drawing_PixelMap* pixelMap, OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates a PixelMap shader object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_PixelMap* pixelMap | Pointer to the [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object. |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileX | Tile mode of the shader effect in the horizontal direction. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileY | Tile mode of the shader effect in the vertical direction. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. If the pointer array is empty, the identity matrix is passed in. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the OH_Drawing_ShaderEffect object created. |

### OH_Drawing_ShaderEffectCreateTwoPointConicalGradient()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateTwoPointConicalGradient(const OH_Drawing_Point2D* startPt, float startRadius, const OH_Drawing_Point2D* endPt, float endRadius, const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**Description**

Creates an **OH_Drawing_ShaderEffect** object that generates a gradient between two given circles. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **startPt**, **endPt**, and **colors** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **tileMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Point2D* startPt | Pointer to the center of the start circle. |
| float startRadius | Start radius of the gradient. The value should be a non-negative number. |
| const OH_Drawing_Point2D* endPt | Pointer to the center of the end circle. |
| float endRadius | End radius of the gradient. The value should be a non-negative number. |
| const uint32_t* colors | Colors to distribute between the two circles. |
| const float* pos | Relative position of each color in the color array. The array length must be the same as that of **colors*<br>*. If **pos** is NULL, colors are evenly distributed between the two circles. |
| uint32_t size | Number of colors and positions (if **pos** is not NULL). |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | Tile mode of the shader effect. For details about the available options, see [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) . |
| const OH_Drawing_Matrix* matrix | Matrix applied on the shader effect. If **matrix** is NULL, an identity matrix is applied by default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created. If the returned pointer is NULL,  the creation fails. The possible causes are as follows:  - The available memory is empty.  - startPt, endPt, or colors is NULL.  - The value of tileMode is out of the enumerated value range. |

### OH_Drawing_ShaderEffectCreateCompose()

```c
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateCompose(OH_Drawing_ShaderEffect* dst, OH_Drawing_ShaderEffect* src, OH_Drawing_BlendMode mode)
```

**Description**

Creates a shader by blending two existing shaders in a certain way.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* dst | Shader that serves as the destination color in blend mode. |
| OH_Drawing_ShaderEffect* src | Shader that serves as the source color in blend mode. |
| OH_Drawing_BlendMode mode | Blend mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* | Returns the pointer to the [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) object created.  If the returned pointer is NULL, the creation fails. The possible causes are as follows:  - The available memory is empty.  - dst or src is NULL.  - The value of mode is out of the enumerated value range. |

### OH_Drawing_ShaderEffectDestroy()

```c
void OH_Drawing_ShaderEffectDestroy(OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Destroys an **OH_Drawing_ShaderEffect** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ShaderEffect* shaderEffect | Pointer to an **OH_Drawing_ShaderEffect** object. |


