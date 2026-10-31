# drawing_pen.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=420af6019e8cfddc483defe1fc789f2af88ace4e translatedAt=2026-08-24T08:46:54.840Z pushedAt=2026-08-31T09:11:33.571Z -->

## Overview

The file defines the functions related to the pen.<br>This module uses a single-thread model. The caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include**: <native_drawing/drawing_pen.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md) | OH_NativeColorSpaceManager | Declares a color space manager object to provide the capability of obtaining basic color space attributes.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_PenLineCapStyle](#oh_drawing_penlinecapstyle) | OH_Drawing_PenLineCapStyle | Defines an enum for the line cap styles of a pen. The line cap style defines the style of both ends of a line segment drawn by the pen.|
| [OH_Drawing_PenLineJoinStyle](#oh_drawing_penlinejoinstyle) | OH_Drawing_PenLineJoinStyle | Enumerates the line join styles of a pen. The line join style defines the shape of the joints of a polyline segment drawn by the pen.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen* OH_Drawing_PenCreate(void)](#oh_drawing_pencreate) | Creates an **OH_Drawing_Pen** object.|
| [OH_Drawing_Pen* OH_Drawing_PenCopy(OH_Drawing_Pen* pen)](#oh_drawing_pencopy) | Creates a copy of the [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md) object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenDestroy(OH_Drawing_Pen* pen)](#oh_drawing_pendestroy) | Destroys an **OH_Drawing_Pen** object and reclaims the memory occupied by the object.|
| [bool OH_Drawing_PenIsAntiAlias(const OH_Drawing_Pen* pen)](#oh_drawing_penisantialias) | Checks whether anti-aliasing is enabled for a pen. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetAntiAlias(OH_Drawing_Pen* pen, bool antiAlias)](#oh_drawing_pensetantialias) | Enables or disables anti-aliasing for a pen. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_PenGetColor(const OH_Drawing_Pen* pen)](#oh_drawing_pengetcolor) | Obtains the color of a pen. The color is used by the pen to outline a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetColor(OH_Drawing_Pen* pen, uint32_t color)](#oh_drawing_pensetcolor) | Sets the color for a pen. The color is used by the pen to outline a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint8_t OH_Drawing_PenGetAlpha(const OH_Drawing_Pen* pen)](#oh_drawing_pengetalpha) | Obtains the alpha value of a pen. This value is used by the alpha channel when the pen outlines a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetAlpha(OH_Drawing_Pen* pen, uint8_t alpha)](#oh_drawing_pensetalpha) | Sets the pen alpha. The alpha channel uses this value when the pen draws a shape outline.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if pen is NULL. |
| [float OH_Drawing_PenGetWidth(const OH_Drawing_Pen* pen)](#oh_drawing_pengetwidth) | Obtains the thickness of a pen. This thickness determines the width of the outline of a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetWidth(OH_Drawing_Pen* pen, float width)](#oh_drawing_pensetwidth) | Sets the thickness for a pen. This thickness determines the width of the outline of a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_PenGetMiterLimit(const OH_Drawing_Pen* pen)](#oh_drawing_pengetmiterlimit) | Used to obtain the limit value of the polyline sharp corner. When the pen draws a polyline and the corner type is set to sharp, this attribute is used to limit the sharp corner length. If the limit value is exceeded, the corner is displayed as flat; if not exceeded, the sharp corner is kept.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if pen is NULL. |
| [void OH_Drawing_PenSetMiterLimit(OH_Drawing_Pen* pen, float miter)](#oh_drawing_pensetmiterlimit) | Used to set the limit value of the polyline sharp corner. When the pen draws a polyline and the corner type is set to sharp, this attribute is used to limit the sharp corner length. If the limit value is exceeded, the corner is displayed as flat; if not exceeded, the sharp corner is kept.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if pen is NULL. |
| [OH_Drawing_PenLineCapStyle OH_Drawing_PenGetCap(const OH_Drawing_Pen* pen)](#oh_drawing_pengetcap) | Obtains the line cap style of a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetCap(OH_Drawing_Pen* pen, OH_Drawing_PenLineCapStyle capStyle)](#oh_drawing_pensetcap) | Sets the line cap style for a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **capStyle** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_PenLineJoinStyle OH_Drawing_PenGetJoin(const OH_Drawing_Pen* pen)](#oh_drawing_pengetjoin) | Obtains the line join style of a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetJoin(OH_Drawing_Pen* pen, OH_Drawing_PenLineJoinStyle joinStyle)](#oh_drawing_pensetjoin) | Sets the join style for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **joinStyle** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [void OH_Drawing_PenSetShaderEffect(OH_Drawing_Pen* pen, OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_pensetshadereffect) | Sets the shader effect for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetShadowLayer(OH_Drawing_Pen* pen, OH_Drawing_ShadowLayer* shadowLayer)](#oh_drawing_pensetshadowlayer) | Sets the shadow layer for a pen. The shadow layer effect takes effect only when text is drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetPathEffect(OH_Drawing_Pen* pen, OH_Drawing_PathEffect* pathEffect)](#oh_drawing_pensetpatheffect) | Sets the path effect for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetFilter(OH_Drawing_Pen* pen, OH_Drawing_Filter* filter)](#oh_drawing_pensetfilter) | Sets a filter for a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenGetFilter(OH_Drawing_Pen* pen, OH_Drawing_Filter* filter)](#oh_drawing_pengetfilter) | Obtains the [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object from the pen. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **pen** or **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenSetBlendMode(OH_Drawing_Pen* pen, OH_Drawing_BlendMode blendMode)](#oh_drawing_pensetblendmode) | Sets a blender for a pen. The blender implements the specified blend mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **blendMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [bool OH_Drawing_PenGetFillPath(OH_Drawing_Pen* pen, const OH_Drawing_Path* src, OH_Drawing_Path* dst,const OH_Drawing_Rect* rect, const OH_Drawing_Matrix* matrix)](#oh_drawing_pengetfillpath) | Obtains the source path outline drawn using this pen and represents it using a destination path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **pen**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PenReset(OH_Drawing_Pen* pen)](#oh_drawing_penreset) | Resets a pen to the initial state.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_PenSetColor4f(OH_Drawing_Pen* pen, float a, float r, float g, float b,OH_NativeColorSpaceManager* colorSpaceManager)](#oh_drawing_pensetcolor4f) | Used to set the pen color attribute, which describes the color used when the pen draws a shape outline.<br>The color is in ARGB format represented by floating-point numbers, and the color space is specified by [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md).<br>If colorSpaceManager is NULL, the SRGB color space (the standard red, green, and blue color space based on IEC 61966-2.1:1999) is used as the default. |
| [OH_Drawing_ErrorCode OH_Drawing_PenGetAlphaFloat(OH_Drawing_Pen* pen, float* a)](#oh_drawing_pengetalphafloat) | Obtains the alpha value of the pen color.|
| [OH_Drawing_ErrorCode OH_Drawing_PenGetRedFloat(OH_Drawing_Pen* pen, float* r)](#oh_drawing_pengetredfloat) | Obtains the red component of the pen color.|
| [OH_Drawing_ErrorCode OH_Drawing_PenGetGreenFloat(OH_Drawing_Pen* pen, float* g)](#oh_drawing_pengetgreenfloat) | Obtains the green component of the pen color.|
| [OH_Drawing_ErrorCode OH_Drawing_PenGetBlueFloat(OH_Drawing_Pen* pen, float* b)](#oh_drawing_pengetbluefloat) | Obtains the blue component of the pen color.|

## Enum Description

### OH_Drawing_PenLineCapStyle

```c
enum OH_Drawing_PenLineCapStyle
```

**Description**

Enumerates the line cap styles of a pen. The line cap style defines the style of both ends of a line segment drawn by the pen.

**Since**: 8

| Enum| Description|
| -- | -- |
| LINE_FLAT_CAP | There is no cap style. Both ends of the line segment are cut off square.|
| LINE_SQUARE_CAP | Square cap style. Both ends have a square, the height of which is half of the width of the line segment, with the same width.|
| LINE_ROUND_CAP | Round cap style. Both ends have a semicircle centered, the diameter of which is the same as the width of the line segment.|

### OH_Drawing_PenLineJoinStyle

```c
enum OH_Drawing_PenLineJoinStyle
```

**Description**

Enumerates the line join styles of a pen. The line join style defines the shape of the joints of a polyline segment drawn by the pen.

**Since**: 8

| Enum| Description|
| -- | -- |
| LINE_MITER_JOIN | Mitered corner. If the angle of a polyline is small, its miter length may be inappropriate. In this case, you need to use the miter limit to limit the miter length.|
| LINE_ROUND_JOIN | Round corner.|
| LINE_BEVEL_JOIN | The corner type is bevel. |

## Function Description

### OH_Drawing_PenCreate()

```c
OH_Drawing_Pen* OH_Drawing_PenCreate(void)
```

**Description**

Creates an **OH_Drawing_Pen** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* | Returns the pointer to the **OH_Drawing_Pen** object created.|

### OH_Drawing_PenCopy()

```c
OH_Drawing_Pen* OH_Drawing_PenCopy(OH_Drawing_Pen* pen)
```

**Description**

Creates a copy of the [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md) object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* | The function returns a pointer to the created copy of the pen object OH_Drawing_Pen. If the return value is NULL, the creation fails. Possible causes include insufficient memory or pen being NULL. |

### OH_Drawing_PenDestroy()

```c
void OH_Drawing_PenDestroy(OH_Drawing_Pen* pen)
```

**Description**

Destroys an **OH_Drawing_Pen** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

### OH_Drawing_PenIsAntiAlias()

```c
bool OH_Drawing_PenIsAntiAlias(const OH_Drawing_Pen* pen)
```

**Description**

Checks whether anti-aliasing is enabled for a pen. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen pen object. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if anti-aliasing is enabled; returns **false** otherwise.|

### OH_Drawing_PenSetAntiAlias()

```c
void OH_Drawing_PenSetAntiAlias(OH_Drawing_Pen* pen, bool antiAlias)
```

**Description**

Enables or disables anti-aliasing for a pen. Anti-aliasing makes the pixels around the shape edges semi-transparent.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| bool antiAlias | Whether to enable anti-aliasing. The value **true** means to enable anti-aliasing, and **false** means the opposite.|

### OH_Drawing_PenGetColor()

```c
uint32_t OH_Drawing_PenGetColor(const OH_Drawing_Pen* pen)
```

**Description**

Obtains the color of a pen. The color is used by the pen to outline a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns a 32-bit (ARGB) variable that describes the color.|

### OH_Drawing_PenSetColor()

```c
void OH_Drawing_PenSetColor(OH_Drawing_Pen* pen, uint32_t color)
```

**Description**

Sets the color for a pen. The color is used by the pen to outline a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| uint32_t color | Color, which is a 32-bit (ARGB) variable.|

### OH_Drawing_PenGetAlpha()

```c
uint8_t OH_Drawing_PenGetAlpha(const OH_Drawing_Pen* pen)
```

**Description**

Obtains the alpha value of a pen. This value is used by the alpha channel when the pen outlines a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen pen object. |

**Returns**

| Type| Description|
| -- | -- |
| uint8_t | Returns an 8-bit variable that describes the alpha value.|

### OH_Drawing_PenSetAlpha()

```c
void OH_Drawing_PenSetAlpha(OH_Drawing_Pen* pen, uint8_t alpha)
```

**Description**

Sets the pen alpha. The alpha channel is used when the pen draws a shape outline.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If pen is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen object. |
| uint8_t alpha | Alpha value to set, an 8-bit variable ranging from 0 to 255, where 0 indicates fully transparent and 255 indicates fully opaque. |

### OH_Drawing_PenGetWidth()

```c
float OH_Drawing_PenGetWidth(const OH_Drawing_Pen* pen)
```

**Description**

Obtains the thickness of a pen. This thickness determines the width of the outline of a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the Pen Object OH_Drawing_Pen. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the thickness.|

### OH_Drawing_PenSetWidth()

```c
void OH_Drawing_PenSetWidth(OH_Drawing_Pen* pen, float width)
```

**Description**

Sets the thickness for a pen. This thickness determines the width of the outline of a shape.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen pen object. |
| float width | Variable that describes the pen thickness, in physical pixels (px). The value range is the float range. |

### OH_Drawing_PenGetMiterLimit()

```c
float OH_Drawing_PenGetMiterLimit(const OH_Drawing_Pen* pen)
```

**Description**

Used to obtain the limit value of a polyline sharp corner. When the pen draws a polyline and the corner type is set to sharp, this attribute is used to limit the length range of the sharp corner. If the limit value is exceeded, the corner is displayed as flat; otherwise, the sharp corner is kept.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If pen is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen pen object. |

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the miter limit.|

### OH_Drawing_PenSetMiterLimit()

```c
void OH_Drawing_PenSetMiterLimit(OH_Drawing_Pen* pen, float miter)
```

**Description**

Used to set the limit value of a polyline sharp corner. When the pen draws a polyline and the corner type is set to sharp, this attribute is used to limit the length range of the sharp corner. If the limit value is exceeded, the corner is displayed as flat; otherwise, the sharp corner is kept.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>If pen is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| float miter | Stroke miter limit, which is a variable.|

### OH_Drawing_PenGetCap()

```c
OH_Drawing_PenLineCapStyle OH_Drawing_PenGetCap(const OH_Drawing_Pen* pen)
```

**Description**

Obtains the line cap style of a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PenLineCapStyle](#oh_drawing_penlinecapstyle) | Returns the line cap style.|

### OH_Drawing_PenSetCap()

```c
void OH_Drawing_PenSetCap(OH_Drawing_Pen* pen, OH_Drawing_PenLineCapStyle capStyle)
```

**Description**

Sets the line cap style for a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **capStyle** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_PenLineCapStyle](#oh_drawing_penlinecapstyle) capStyle | Line cap style, which is a variable.|

### OH_Drawing_PenGetJoin()

```c
OH_Drawing_PenLineJoinStyle OH_Drawing_PenGetJoin(const OH_Drawing_Pen* pen)
```

**Description**

Obtains the line join style of a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PenLineJoinStyle](#oh_drawing_penlinejoinstyle) | Returns the line join style.|

### OH_Drawing_PenSetJoin()

```c
void OH_Drawing_PenSetJoin(OH_Drawing_Pen* pen, OH_Drawing_PenLineJoinStyle joinStyle)
```

**Description**

Sets the join style for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **joinStyle** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the OH_Drawing_Pen object. |
| [OH_Drawing_PenLineJoinStyle](#oh_drawing_penlinejoinstyle) joinStyle | Enumeration that describes the line join style. |

### OH_Drawing_PenSetShaderEffect()

```c
void OH_Drawing_PenSetShaderEffect(OH_Drawing_Pen* pen, OH_Drawing_ShaderEffect* shaderEffect)
```

**Description**

Sets the shader effect for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | Pointer to the shader object OH_Drawing_ShaderEffect. NULL indicates that the shader effect is cleared. |

### OH_Drawing_PenSetShadowLayer()

```c
void OH_Drawing_PenSetShadowLayer(OH_Drawing_Pen* pen, OH_Drawing_ShadowLayer* shadowLayer)
```

**Description**

Sets the shadow layer for a pen. The shadow layer effect takes effect only when text is drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md)* shadowLayer | Pointer to the shadow layer object OH_Drawing_ShadowLayer. NULL indicates that the shadow layer effect is cleared. |

### OH_Drawing_PenSetPathEffect()

```c
void OH_Drawing_PenSetPathEffect(OH_Drawing_Pen* pen, OH_Drawing_PathEffect* pathEffect)
```

**Description**

Sets the path effect for this pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* pathEffect | Pointer to the path effect object OH_Drawing_PathEffect. NULL indicates that the path effect is cleared. |

### OH_Drawing_PenSetFilter()

```c
void OH_Drawing_PenSetFilter(OH_Drawing_Pen* pen, OH_Drawing_Filter* filter)
```

**Description**

Sets a filter for a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | Pointer to the filter OH_Drawing_Filter. NULL indicates clearing the pen filter. |

### OH_Drawing_PenGetFilter()

```c
void OH_Drawing_PenGetFilter(OH_Drawing_Pen* pen, OH_Drawing_Filter* filter)
```

**Description**

Obtains the [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object from the pen. The filter is a container that holds a mask filter and color filter.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **pen** or **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | Pointer to the filter object OH_Drawing_Filter. |

### OH_Drawing_PenSetBlendMode()

```c
void OH_Drawing_PenSetBlendMode(OH_Drawing_Pen* pen, OH_Drawing_BlendMode blendMode)
```

**Description**

Sets a blender for a pen. The blender implements the specified blend mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **blendMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | Blend mode enum. |

### OH_Drawing_PenGetFillPath()

```c
bool OH_Drawing_PenGetFillPath(OH_Drawing_Pen* pen, const OH_Drawing_Path* src, OH_Drawing_Path* dst, const OH_Drawing_Rect* rect, const OH_Drawing_Matrix* matrix)
```

**Description**

Obtains the source path outline drawn using this pen and represents it using a destination path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **pen**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the source path object OH_Drawing_Path. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* dst | Pointer to the destination path object OH_Drawing_Path. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. NULL is recommended, in which case no clipping rectangle is specified. |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the matrix object OH_Drawing_Matrix. NULL is recommended, in which case the identity matrix is used by default, meaning no transformation is applied. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the destination path is obtained; returns **false** otherwise.|

### OH_Drawing_PenReset()

```c
void OH_Drawing_PenReset(OH_Drawing_Pen* pen)
```

**Description**

Resets a pen to the initial state.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to the pen object OH_Drawing_Pen. |

### OH_Drawing_PenSetColor4f()

```c
OH_Drawing_ErrorCode OH_Drawing_PenSetColor4f(OH_Drawing_Pen* pen, float a, float r, float g, float b, OH_NativeColorSpaceManager* colorSpaceManager)
```

**Description**

Used to set the color attribute of the pen. The color attribute describes the color used when the pen draws a shape outline.<br>The color is in ARGB format represented by floating-point numbers. The color space is specified by [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md).<br>If colorSpaceManager is NULL, the SRGB color space (the standard red, green, and blue color space based on IEC 61966-2.1:1999) is used as the default.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an **OH_Drawing_Pen** instance. |
| float a | Alpha value of the color, which is a floating-point number ranging from 0.0 to 1.0. Values above 1.0 default to 1.0, while values below 0.0 default to 0.0.|
| float r | Red component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values above 1.0 default to 1.0, while values below 0.0 default to 0.0.|
| float g | Green component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values above 1.0 default to 1.0, while values below 0.0 default to 0.0.|
| float b | Blue component of the color, which is a floating-point number ranging from 0.0 to 1.0. Values above 1.0 default to 1.0, while values below 0.0 default to 0.0.|
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)* colorSpaceManager | Pointer to an **OH_NativeColorSpaceManager** instance. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if the parameter pen is NULL. |

### OH_Drawing_PenGetAlphaFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_PenGetAlphaFloat(OH_Drawing_Pen* pen, float* a)
```

**Description**

Obtains the alpha value of the pen color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an OH_Drawing_Pen object. |
| float* a | Alpha value of the pen color. The value is a floating-point number ranging from 0.0 to 1.0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if pen or a is NULL. |

### OH_Drawing_PenGetRedFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_PenGetRedFloat(OH_Drawing_Pen* pen, float* r)
```

**Description**

Obtains the red component of the pen color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an OH_Drawing_Pen object. |
| float* r | Red component of the pen color. The value is a floating-point number ranging from 0.0 to 1.0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns **OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if pen or r is NULL. |

### OH_Drawing_PenGetGreenFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_PenGetGreenFloat(OH_Drawing_Pen* pen, float* g)
```

**Description**

Obtains the green component of the pen color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an OH_Drawing_Pen object. |
| float* g | Green component of the pen color. The value is a floating-point number ranging from 0.0 to 1.0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if pen or g is a null pointer. |

### OH_Drawing_PenGetBlueFloat()

```c
OH_Drawing_ErrorCode OH_Drawing_PenGetBlueFloat(OH_Drawing_Pen* pen, float* b)
```

**Description**

Obtains the blue component of the pen color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an OH_Drawing_Pen object. |
| float* b | Blue component of the pen color. The value is a floating-point number ranging from 0.0 to 1.0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if pen or b is a null pointer. |