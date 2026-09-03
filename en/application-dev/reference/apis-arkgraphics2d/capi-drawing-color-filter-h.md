# drawing_color_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T08:23:32.875Z pushedAt=2026-08-31T03:32:21.973Z -->

## Overview

Declares functions related to color filter objects in the drawing module. It supports creating various color filter effects such as blend mode, composition, matrix, gamma conversion, luma, and lighting, which are suitable for color adjustment and special effect processing scenarios in image rendering.<br>This module uses a single-thread model policy, and the caller needs to manage thread safety and context state switching.

**File to include**: <native_drawing/drawing_color_filter.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)](#oh_drawing_colorfiltercreateblendmode) | Creates a color filter with a blend mode, which is suitable for scenarios where the source color and destination color need to be composited according to the specified blend mode. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter,OH_Drawing_ColorFilter* innerColorFilter)](#oh_drawing_colorfiltercreatecompose) | Combines two color filters into a new color filter. During composition, innerColorFilter is applied first for filtering, and then outerColorFilter is applied.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either outerColorFilter or innerColorFilter is NULL. Check and ensure that the passed outerColorFilter and innerColorFilter are valid color filter object pointers. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])](#oh_drawing_colorfiltercreatematrix) | Creates a color filter with a 4x5 color matrix, which is suitable for scenarios where custom color transformation is required.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if matrix is NULL. Check and ensure that the passed matrix is a valid floating-point array pointer. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)](#oh_drawing_colorfiltercreatelineartosrgbgamma) | Creates a color filter that converts from the linear color space to the SRGB color space. This API is the inverse of OH_Drawing_ColorFilterCreateSrgbGammaToLinear. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)](#oh_drawing_colorfiltercreatesrgbgammatolinear) | Creates a color filter that converts from the SRGB color space to the linear color space. This API is the inverse of OH_Drawing_ColorFilterCreateLinearToSrgbGamma. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)](#oh_drawing_colorfiltercreateluma) | Creates a color filter that multiplies the luma value of its input by the alpha channel value, and sets the red, green, and blue channels to zero. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)](#oh_drawing_colorfiltercreatelighting) | Creates a lighting color filter. It multiplies the RGB channel values by one color and then adds another color value. The final output stays between 0 and 255.|
| [void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)](#oh_drawing_colorfilterdestroy) | Destroys an **OH_Drawing_ColorFilter** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_ColorFilterCreateBlendMode()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)
```

**Description**

Creates a color filter with a blend mode, which is suitable for scenarios where the source color and destination color need to be composited according to a specified blend mode.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| uint32_t color | Color, which is a 32-bit (ARGB) variable.|
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | Blend mode. | For details about the supported blend modes, see the [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) enum. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateCompose()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter, OH_Drawing_ColorFilter* innerColorFilter)
```

**Description**

Combines two color filters into a new color filter. During composition, the innerColorFilter is applied first for filtering, and then the outerColorFilter is applied.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either outerColorFilter or innerColorFilter is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. Check and ensure that the passed outerColorFilter and innerColorFilter are valid pointers to color filter objects.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* outerColorFilter | Pointer to the outer color filter object in the color filter. |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* innerColorFilter | Pointer to the inner color filter object in the color filter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateMatrix()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])
```

**Description**

Creates a color filter with a 4x5 color matrix, which is suitable for scenarios where custom color transformation is required.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If matrix is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. Check and ensure that the passed matrix is a valid pointer to a floating-point array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| const float matrix[20] | Represents a 4x5 color matrix used to perform linear transformation on the color channels of an image. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateLinearToSrgbGamma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)
```

**Description**

Creates a color filter that converts from the linear color space to the SRGB color space. This API is the inverse operation of OH_Drawing_ColorFilterCreateSrgbGammaToLinear.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateSrgbGammaToLinear()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)
```

**Description**

Creates a color filter that converts from the SRGB color space to the linear color space. This API is the inverse operation of OH_Drawing_ColorFilterCreateLinearToSrgbGamma.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateLuma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)
```

**Description**

Creates a color filter that multiplies the luma value of its input by the alpha channel value and sets the red, green, and blue channels to zero.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterCreateLighting()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)
```

**Description**

Creates a lighting color filter. It multiplies the RGB channel values by one color and then adds another color value. The final output stays between 0 and 255.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| uint32_t mulColor | Color value used for multiplication, which is a 32-bit (ARGB) variable. |
| uint32_t addColor | Color value used for addition, which is a 32-bit (ARGB) variable. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | Returns the pointer to the **OH_Drawing_ColorFilter** object created.|

### OH_Drawing_ColorFilterDestroy()

```c
void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)
```

**Description**

Destroys a color filter object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* colorFilter | Pointer to an **OH_Drawing_ColorFilter** object.|