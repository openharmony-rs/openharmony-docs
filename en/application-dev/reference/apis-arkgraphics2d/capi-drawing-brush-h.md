# drawing_brush.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:22:39.490Z pushedAt=2026-08-31T03:17:39.933Z -->

## Overview

The file defines the functions related to the brush.<br>This module adopts a single-thread model, and the caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include:** \<native_drawing/drawing_brush.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md) | OH_NativeColorSpaceManager | Declares a color space management object and provides the capability to obtain the basic attributes of a color space. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush* OH_Drawing_BrushCreate(void)](#oh_drawing_brushcreate) | Creates a brush object. After the brush object created by this API is used, you must call [OH_Drawing_BrushDestroy](#oh_drawing_brushdestroy) to destroy it and reclaim the memory. Otherwise, a memory leak occurs. |
| [OH_Drawing_Brush* OH_Drawing_BrushCopy(OH_Drawing_Brush* brush)](#oh_drawing_brushcopy) | Copies an existing brush object to create a copy of it, [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md). After the brush object created by this API is used, you must call [OH_Drawing_BrushDestroy](#oh_drawing_brushdestroy) to destroy it and reclaim the memory. Otherwise, a memory leak occurs.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when brush is NULL. |
| [void OH_Drawing_BrushDestroy(OH_Drawing_Brush* brush)](#oh_drawing_brushdestroy) | Destroys a brush object and reclaims the memory occupied by the object. This API should be used in pair with [OH_Drawing_BrushCreate](#oh_drawing_brushcreate) or [OH_Drawing_BrushCopy](#oh_drawing_brushcopy) to release the created or copied brush object and avoid memory leaks. |
| [bool OH_Drawing_BrushIsAntiAlias(const OH_Drawing_Brush* brush)](#oh_drawing_brushisantialias) | Checks whether anti-aliasing is enabled for a brush. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetAntiAlias(OH_Drawing_Brush* brush, bool antiAlias)](#oh_drawing_brushsetantialias) | Enables or disables anti-aliasing for a brush. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_BrushGetColor(const OH_Drawing_Brush* brush)](#oh_drawing_brushgetcolor) | Obtains the color of a brush. The color is used by the brush to fill in a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetColor(OH_Drawing_Brush* brush, uint32_t color)](#oh_drawing_brushsetcolor) | Sets the color attribute of a brush. The color attribute describes the color used by the brush to fill a shape, represented by a 32-bit (ARGB) variable. When color space management or high-precision color representation is required, use [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f) instead.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when brush is NULL. |
| [uint8_t OH_Drawing_BrushGetAlpha(const OH_Drawing_Brush* brush)](#oh_drawing_brushgetalpha) | Obtains the alpha value of a brush. The alpha channel uses this value when the brush fills a shape. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use [OH_Drawing_BrushGetAlphaFloat](#oh_drawing_brushgetalphafloat) to obtain the alpha value to avoid precision loss.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when brush is NULL. |
| [void OH_Drawing_BrushSetAlpha(OH_Drawing_Brush* brush, uint8_t alpha)](#oh_drawing_brushsetalpha) | Sets the alpha value for a brush. This value is used by the alpha channel when the brush fills in a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetShaderEffect(OH_Drawing_Brush* brush, OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_brushsetshadereffect) | Sets the shader effect for a brush.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetShadowLayer(OH_Drawing_Brush* brush, OH_Drawing_ShadowLayer* shadowLayer)](#oh_drawing_brushsetshadowlayer) | Sets the shadow layer for a brush. The shadow layer effect takes effect only when text is drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)](#oh_drawing_brushsetfilter) | Sets the filter [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) for a brush. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushGetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)](#oh_drawing_brushgetfilter) | Obtains the [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object from the brush. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **brush** or **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_BrushSetBlendMode(OH_Drawing_Brush* brush, OH_Drawing_BlendMode blendMode)](#oh_drawing_brushsetblendmode) | Sets the blend mode for a brush. The specified blend mode enum determines how source pixels are composited with destination pixels when the brush draws.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when brush is NULL;<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned when blendMode is out of the enum range. |
| [void OH_Drawing_BrushReset(OH_Drawing_Brush* brush)](#oh_drawing_brushreset) | Resets a brush to the initial state. All configured attributes are cleared.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_BrushSetColor4f(OH_Drawing_Brush* brush, float a, float r, float g, float b, OH_NativeColorSpaceManager* colorSpaceManager)](#oh_drawing_brushsetcolor4f) | Sets the color of a brush. The brush uses this color to fill a shape.<br>Compared with [OH_Drawing_BrushSetColor](#oh_drawing_brushsetcolor), this API uses floating-point numbers to represent the ARGB components, providing higher precision, and supports specifying a color space through colorSpaceManager. When color space management or high-precision color representation is required, use this API.<br> The color uses the ARGB format represented by floating-point numbers, and the color space is specified by [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md).<br> If colorSpaceManager is NULL, the sRGB color space (the standard red, green, and blue color space based on IEC 61966-2.1:1999) is used as the default. |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetAlphaFloat(const OH_Drawing_Brush* brush, float* a)](#oh_drawing_brushgetalphafloat) | Obtains the alpha value of the brush color, represented as a floating-point number. Compared with [OH_Drawing_BrushGetAlpha](#oh_drawing_brushgetalpha), this API returns the alpha value as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the alpha value to avoid precision loss. |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetRedFloat(const OH_Drawing_Brush* brush, float* r)](#oh_drawing_brushgetredfloat) | Obtains the red component of the brush color, represented as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the red component to avoid precision loss. |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetGreenFloat(const OH_Drawing_Brush* brush, float* g)](#oh_drawing_brushgetgreenfloat) | Obtains the green component of the brush color, represented as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the green component to avoid precision loss. |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetBlueFloat(const OH_Drawing_Brush* brush, float* b)](#oh_drawing_brushgetbluefloat) | Obtains the blue component of the brush color, represented as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the blue component to avoid precision loss. |

## Function Description

### OH_Drawing_BrushCreate()

```c
OH_Drawing_Brush* OH_Drawing_BrushCreate(void)
```

**Description**

Creates a brush object. After the brush object created by this API is used, it must be destroyed by calling [OH_Drawing_BrushDestroy](#oh_drawing_brushdestroy) to reclaim the memory. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* | Pointer to the created brush object. NULL is returned if the creation fails, possibly due to insufficient memory. |

### OH_Drawing_BrushCopy()

```c
OH_Drawing_Brush* OH_Drawing_BrushCopy(OH_Drawing_Brush* brush)
```

**Description**

Copies an existing brush object to create a copy of the brush object [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md). After the brush object created by this API is used, it must be destroyed by calling [OH_Drawing_BrushDestroy](#oh_drawing_brushdestroy) to reclaim the memory. Otherwise, a memory leak occurs.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if brush is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* | The function returns a pointer to the created copy of the brush object [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md). If NULL is returned, the creation fails. The possible cause is insufficient available memory, or brush is NULL. |

### OH_Drawing_BrushDestroy()

```c
void OH_Drawing_BrushDestroy(OH_Drawing_Brush* brush)
```

**Description**

Destroys a brush object and reclaims the memory occupied by the object. This API must be used together with [OH_Drawing_BrushCreate](#oh_drawing_brushcreate) or [OH_Drawing_BrushCopy](#oh_drawing_brushcopy) to release the brush object that has been created or copied, so as to avoid memory leaks.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

### OH_Drawing_BrushIsAntiAlias()

```c
bool OH_Drawing_BrushIsAntiAlias(const OH_Drawing_Brush* brush)
```

**Description**

Checks whether anti-aliasing is enabled for a brush. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if anti-aliasing is enabled; returns **false** otherwise.|

### OH_Drawing_BrushSetAntiAlias()

```c
void OH_Drawing_BrushSetAntiAlias(OH_Drawing_Brush* brush, bool antiAlias)
```

**Description**

Enables or disables anti-aliasing for a brush. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| bool antiAlias | Whether to enable anti-aliasing. The value **true** means to enable anti-aliasing, and **false** means the opposite.|

### OH_Drawing_BrushGetColor()

```c
uint32_t OH_Drawing_BrushGetColor(const OH_Drawing_Brush* brush)
```

**Description**

Obtains the color of a brush. The color is used by the brush to fill in a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | The function returns a 32-bit (ARGB) variable that describes the color, with each color channel in the range [0, 255]. |

### OH_Drawing_BrushSetColor()

```c
void OH_Drawing_BrushSetColor(OH_Drawing_Brush* brush, uint32_t color)
```

**Description**

Sets the color attribute of the brush. The color attribute describes the color used by the brush to fill a shape, represented by a 32-bit (ARGB) variable. When color space management or high-precision color representation is required, use [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f) first.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if brush is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| uint32_t color | 32-bit (ARGB) variable that describes the color. The value range of each color channel is [0, 255]. |

### OH_Drawing_BrushGetAlpha()

```c
uint8_t OH_Drawing_BrushGetAlpha(const OH_Drawing_Brush* brush)
```

**Description**

Obtains the alpha value of the brush. The alpha channel uses this value when the brush fills a shape. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use [OH_Drawing_BrushGetAlphaFloat](#oh_drawing_brushgetalphafloat) to obtain the alpha value to avoid precision loss.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if brush is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to a brush object. |

**Returns**

| Type| Description|
| -- | -- |
| uint8_t | 8-bit unsigned integer that represents the alpha value, ranging from 0 to 255, where 0 indicates fully transparent and 255 indicates fully opaque. |

### OH_Drawing_BrushSetAlpha()

```c
void OH_Drawing_BrushSetAlpha(OH_Drawing_Brush* brush, uint8_t alpha)
```

**Description**

Sets the alpha value for a brush. This value is used by the alpha channel when the brush fills in a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| uint8_t alpha | Indicates the alpha value to set, which is an 8-bit unsigned integer in the range [0, 255], where 0 indicates fully transparent and 255 indicates fully opaque. |

### OH_Drawing_BrushSetShaderEffect()

```c
void OH_Drawing_BrushSetShaderEffect(OH_Drawing_Brush* brush, OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Sets the shader effect for a brush.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | Pointer to an **OH_Drawing_ShaderEffect** object. If NULL is passed in, the shader effect of the brush will be cleared.|

### OH_Drawing_BrushSetShadowLayer()

```c
void OH_Drawing_BrushSetShadowLayer(OH_Drawing_Brush* brush, OH_Drawing_ShadowLayer* shadowLayer)
```

**Description**

Sets the shadow layer for a brush. The shadow layer effect takes effect only when text is drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md)* shadowLayer | Pointer to an **OH_Drawing_ShadowLayer** object. If NULL is passed in, the shadow layer effect of the brush will be cleared.|

### OH_Drawing_BrushSetFilter()

```c
void OH_Drawing_BrushSetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)
```

**Description**

Sets the filter [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) for a brush. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | Pointer to an **OH_Drawing_Filter** object. If null is passed in, the filter will be cleared.|

### OH_Drawing_BrushGetFilter()

```c
void OH_Drawing_BrushGetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)
```

**Description**

Obtains the [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object from the brush. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **brush** or **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | Pointer to the filter object [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md), used to receive the filter obtained from the brush. Memory must be allocated before the call, and the function writes the result. |

### OH_Drawing_BrushSetBlendMode()

```c
void OH_Drawing_BrushSetBlendMode(OH_Drawing_Brush* brush, OH_Drawing_BlendMode blendMode)
```

**Description**

Sets the blend mode for the brush. The specified blend mode enum determines how the source pixels are composited with the destination pixels when the brush draws.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if brush is NULL;<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned if blendMode is out of the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | Blend mode to set, which specifies how source pixels are blended with destination pixels when the brush draws. Enum type [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode). |

### OH_Drawing_BrushReset()

```c
void OH_Drawing_BrushReset(OH_Drawing_Brush* brush)
```

**Description**

Resets a brush to the initial state. All configured attributes are cleared.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|

### OH_Drawing_BrushSetColor4f()

```c
OH_Drawing_ErrorCode OH_Drawing_BrushSetColor4f(OH_Drawing_Brush* brush, float a, float r, float g, float b, OH_NativeColorSpaceManager* colorSpaceManager)
```

**Description**

Sets the color of the brush. The brush uses this color to fill a shape.<br>Compared with [OH_Drawing_BrushSetColor](#oh_drawing_brushsetcolor), this API uses floating-point numbers to represent the ARGB components, providing higher precision, and supports specifying the color space through colorSpaceManager. When color space management or high-precision color representation is required, use this API first.<br> The color uses the ARGB format represented by floating-point numbers, and the color space is specified by [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md).<br> If colorSpaceManager is NULL, the sRGB color space (the standard red, green, and blue color space based on IEC 61966-2.1:1999) is used as the default.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to the [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object. |
| float a | Alpha value in the color, represented by a floating-point number in the range [0.0, 1.0]. Values greater than 1.0 are treated as 1.0, and values less than 0.0 are treated as 0.0. |
| float r | Red component in the color, represented by a floating-point number in the range [0.0, 1.0]. Values greater than 1.0 are treated as 1.0, and values less than 0.0 are treated as 0.0. |
| float g | Green component in the color, represented by a floating-point number in the range [0.0, 1.0]. Values greater than 1.0 are treated as 1.0, and values less than 0.0 are treated as 0.0. |
| float b | Blue component in the color, represented by a floating-point number in the range [0.0, 1.0]. Values greater than 1.0 are treated as 1.0, and values less than 0.0 are treated as 0.0. |
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)* colorSpaceManager | Pointer to an [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **brush** is NULL.|

### OH_Drawing_BrushGetAlphaFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_BrushGetAlphaFloat(const OH_Drawing_Brush* brush, float* a)
```

**Description**

Obtains the alpha value of the brush color, represented as a floating-point number. Compared with [OH_Drawing_BrushGetAlpha](#oh_drawing_brushgetalpha), this API returns the alpha value represented by a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the alpha value to avoid precision loss.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| float* a | Pointer to a floating-point number, used to receive the alpha value of the brush color. The value ranges from 0.0 to 1.0. Ensure that the pointer points to valid memory before calling. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **brush** or **a** is NULL.|

### OH_Drawing_BrushGetRedFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_BrushGetRedFloat(const OH_Drawing_Brush* brush, float* r)
```

**Description**

Obtains the red component of the brush color, expressed as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the red component to avoid precision loss.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| float* r | Pointer to a floating-point number, used to receive the red component value of the brush color, with a value range of [0.0, 1.0]. Ensure that the pointer points to valid memory before calling. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **brush** or **r** is NULL.|

### OH_Drawing_BrushGetGreenFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_BrushGetGreenFloat(const OH_Drawing_Brush* brush, float* g)
```

**Description**

Obtains the green component of the brush color, expressed as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the green component to avoid precision loss.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| float* g | Pointer to a floating-point number, used to receive the green component of the brush color, with a value range of [0.0, 1.0]. Ensure that the pointer points to valid memory before calling this API. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **brush** or **g** is NULL.|

### OH_Drawing_BrushGetBlueFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_BrushGetBlueFloat(const OH_Drawing_Brush* brush, float* b)
```

**Description**

Obtains the blue component of the brush color, expressed as a floating-point number. Compared with [OH_Drawing_BrushGetColor](#oh_drawing_brushgetcolor), this API returns the color component as a floating-point number with higher precision. When the brush color is set through [OH_Drawing_BrushSetColor4f](#oh_drawing_brushsetcolor4f), use this API to obtain the blue component to avoid precision loss.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object.|
| float* b | Pointer to a floating-point number, used to receive the blue component value of the brush color, with a value range of [0.0, 1.0]. Ensure that the pointer points to valid memory before calling. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **brush** or **b** is NULL.|