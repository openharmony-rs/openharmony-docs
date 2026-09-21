# drawing_filter.h

## Overview

This file declares the functions related to the filter in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Filter* OH_Drawing_FilterCreate(void)](#oh_drawing_filtercreate) | Creates an **OH_Drawing_Filter** object. |
| [void OH_Drawing_FilterSetImageFilter(OH_Drawing_Filter* filter, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_filtersetimagefilter) | Sets an **OH_Drawing_ImageFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_FilterSetMaskFilter(OH_Drawing_Filter* filter, OH_Drawing_MaskFilter* maskFilter)](#oh_drawing_filtersetmaskfilter) | Sets an **OH_Drawing_MaskFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_FilterSetColorFilter(OH_Drawing_Filter* filter, OH_Drawing_ColorFilter* colorFilter)](#oh_drawing_filtersetcolorfilter) | Sets an **OH_Drawing_ColorFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_FilterGetColorFilter(OH_Drawing_Filter* filter, OH_Drawing_ColorFilter* colorFilter)](#oh_drawing_filtergetcolorfilter) | Obtains an **OH_Drawing_ColorFilter** object from an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **filter** or **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_FilterDestroy(OH_Drawing_Filter* filter)](#oh_drawing_filterdestroy) | Destroys an **OH_Drawing_Filter** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_FilterCreate()

```c
OH_Drawing_Filter* OH_Drawing_FilterCreate(void)
```

**Description**

Creates an **OH_Drawing_Filter** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Filter* | Returns the pointer to the <b>OH_Drawing_Filter</b> object created. |

### OH_Drawing_FilterSetImageFilter()

```c
void OH_Drawing_FilterSetImageFilter(OH_Drawing_Filter* filter, OH_Drawing_ImageFilter* imageFilter)
```

**Description**

Sets an **OH_Drawing_ImageFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Filter* filter | Pointer to an [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object. |
| OH_Drawing_ImageFilter* imageFilter | Pointer to an [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) object. If NULL is passed in, the image filter effect of the object will be cleared. |

### OH_Drawing_FilterSetMaskFilter()

```c
void OH_Drawing_FilterSetMaskFilter(OH_Drawing_Filter* filter, OH_Drawing_MaskFilter* maskFilter)
```

**Description**

Sets an **OH_Drawing_MaskFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Filter* filter | Pointer to an [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object. |
| OH_Drawing_MaskFilter* maskFilter | Pointer to an [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) object. If NULL is passed in, the mask filter effect of the object will be cleared. |

### OH_Drawing_FilterSetColorFilter()

```c
void OH_Drawing_FilterSetColorFilter(OH_Drawing_Filter* filter, OH_Drawing_ColorFilter* colorFilter)
```

**Description**

Sets an **OH_Drawing_ColorFilter** object for an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **filter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Filter* filter | Pointer to an [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object. |
| OH_Drawing_ColorFilter* colorFilter | Pointer to an [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) object. If NULL is passed in, the color filter effect of the object will be cleared. |

### OH_Drawing_FilterGetColorFilter()

```c
void OH_Drawing_FilterGetColorFilter(OH_Drawing_Filter* filter, OH_Drawing_ColorFilter* colorFilter)
```

**Description**

Obtains an **OH_Drawing_ColorFilter** object from an **OH_Drawing_Filter** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **filter** or **colorFilter** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Filter* filter | Pointer to an [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object. |
| OH_Drawing_ColorFilter* colorFilter | Pointer to an [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) object. |

### OH_Drawing_FilterDestroy()

```c
void OH_Drawing_FilterDestroy(OH_Drawing_Filter* filter)
```

**Description**

Destroys an **OH_Drawing_Filter** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Filter* filter | Pointer to an [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) object. |


