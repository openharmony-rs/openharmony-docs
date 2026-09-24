# drawing_color_filter.h

## Overview

This file declares the functions related to the color filter in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)](#oh_drawing_colorfiltercreateblendmode) | Creates an **OH_Drawing_ColorFilter** object with a given blend mode. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter, OH_Drawing_ColorFilter* innerColorFilter)](#oh_drawing_colorfiltercreatecompose) | Creates an **OH_Drawing_ColorFilter** object by combining another two color filters. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **outerColorFilter** or **innerColorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])](#oh_drawing_colorfiltercreatematrix) | Creates an **OH_Drawing_ColorFilter** object with a given 5x4 color matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)](#oh_drawing_colorfiltercreatelineartosrgbgamma) | Creates an **OH_Drawing_ColorFilter** object that applies the sRGB gamma curve to the RGB channels. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)](#oh_drawing_colorfiltercreatesrgbgammatolinear) | Creates an **OH_Drawing_ColorFilter** object that applies the RGB channels to the sRGB gamma curve. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)](#oh_drawing_colorfiltercreateluma) | Creates a **ColorFilter** object that multiplies the luma into the alpha channel and sets the RGB channels to zero. |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)](#oh_drawing_colorfiltercreatelighting) | Creates a lighting color filter. It multiplies the RGB channel values by one color and then adds another color value. The final output stays between 0 and 255. |
| [void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)](#oh_drawing_colorfilterdestroy) | Destroys an **OH_Drawing_ColorFilter** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_ColorFilterCreateBlendMode()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)
```

**Description**

Creates an **OH_Drawing_ColorFilter** object with a given blend mode.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t color | Color, which is a 32-bit (ARGB) variable. |
| OH_Drawing_BlendMode blendMode | Blend mode. For details about the available options, see [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateCompose()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter, OH_Drawing_ColorFilter* innerColorFilter)
```

**Description**

Creates an **OH_Drawing_ColorFilter** object by combining another two color filters. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **outerColorFilter** or **innerColorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ColorFilter* outerColorFilter | Pointer to the first color filter. |
| OH_Drawing_ColorFilter* innerColorFilter | Pointer to the second color filter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateMatrix()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])
```

**Description**

Creates an **OH_Drawing_ColorFilter** object with a given 5x4 color matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const float matrix[20] | Matrix, which is represented by a floating-point array with a length of 20. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateLinearToSrgbGamma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)
```

**Description**

Creates an **OH_Drawing_ColorFilter** object that applies the sRGB gamma curve to the RGB channels.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateSrgbGammaToLinear()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)
```

**Description**

Creates an **OH_Drawing_ColorFilter** object that applies the RGB channels to the sRGB gamma curve.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateLuma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)
```

**Description**

Creates a **ColorFilter** object that multiplies the luma into the alpha channel and sets the RGB channels to zero.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterCreateLighting()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)
```

**Description**

Creates a lighting color filter. It multiplies the RGB channel values by one color and then adds another color value. The final output stays between 0 and 255.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t mulColor | Color value used for multiplication. |
| uint32_t addColor | Color value used for addition. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorFilter* | Returns the pointer to the OH_Drawing_ColorFilter object created. |

### OH_Drawing_ColorFilterDestroy()

```c
void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)
```

**Description**

Destroys an **OH_Drawing_ColorFilter** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ColorFilter* colorFilter | Pointer to an **OH_Drawing_ColorFilter** object. |


