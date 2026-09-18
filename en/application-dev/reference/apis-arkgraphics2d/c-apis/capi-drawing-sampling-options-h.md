# drawing_sampling_options.h

## Overview

This file declares the functions related to sampling in the drawing module. It is used for image or texture sampling.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_FilterMode](#oh_drawing_filtermode) | OH_Drawing_FilterMode | Defines an enum for the filter modes. |
| [OH_Drawing_MipmapMode](#oh_drawing_mipmapmode) | OH_Drawing_MipmapMode | Defines an enum for the mipmap modes. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCreate(OH_Drawing_FilterMode filterMode, OH_Drawing_MipmapMode mipmapMode)](#oh_drawing_samplingoptionscreate) | Creates an **OH_Drawing_SamplingOptions** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **mipmapMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCopy(OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_samplingoptionscopy) | Creates a copy of an {@link OH_Drawing_SamplingOptions} object. |
| [void OH_Drawing_SamplingOptionsDestroy(OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_samplingoptionsdestroy) | Destroys an **OH_Drawing_SamplingOptions** object and reclaims the memory occupied by the object. |

## Enum type description

### OH_Drawing_FilterMode

```c
enum OH_Drawing_FilterMode
```

**Description**

Defines an enum for the filter modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| FILTER_MODE_NEAREST | Nearest filter mode. |
| FILTER_MODE_LINEAR | Linear filter mode. |

### OH_Drawing_MipmapMode

```c
enum OH_Drawing_MipmapMode
```

**Description**

Defines an enum for the mipmap modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MIPMAP_MODE_NONE | Mipmap level ignored. |
| MIPMAP_MODE_NEAREST | Nearest sampling from two adjacent mipmap levels. |
| MIPMAP_MODE_LINEAR | Linear interpolation sampling between two adjacent mipmap levels. |


## Function description

### OH_Drawing_SamplingOptionsCreate()

```c
OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCreate(OH_Drawing_FilterMode filterMode, OH_Drawing_MipmapMode mipmapMode)
```

**Description**

Creates an **OH_Drawing_SamplingOptions** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **mipmapMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FilterMode](capi-drawing-sampling-options-h.md#oh_drawing_filtermode) filterMode | Filter sampling mode. |
| [OH_Drawing_MipmapMode](capi-drawing-sampling-options-h.md#oh_drawing_mipmapmode) mipmapMode | Mipmap mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_SamplingOptions* | Returns a pointer to the created {@link OH_Drawing_SamplingOptions} object. |

### OH_Drawing_SamplingOptionsCopy()

```c
OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCopy(OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Creates a copy of an {@link OH_Drawing_SamplingOptions} object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_SamplingOptions* | Returns a pointer to the created {@link OH_Drawing_SamplingOptions} object copy. If NULL is returned, the  creation fails. The possible failure cause is that no memory is available or samplingOptions is NULL. |

### OH_Drawing_SamplingOptionsDestroy()

```c
void OH_Drawing_SamplingOptionsDestroy(OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Destroys an **OH_Drawing_SamplingOptions** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. |


