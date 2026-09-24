# effect_types.h

## Overview

Declares the data types for filter effects, used to define the matrices, status codes, and tile modes for filter effects, and supports scenarios such as creating custom filter effects and processing image shader tiling.

**Library**: libnative_effect.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [effectKit](capi-effectkit.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md) | - | Defines a 4x5 matrix for creating a filter effect, with elements of floating-point numbers. |
| [OH_Filter](capi-effectkit-oh-filter.md) | OH_Filter | Defines a filter struct used with EffectKit module APIs to implement filter effect processing. |
| [OH_PixelmapNative](capi-effectkit-oh-pixelmapnative.md) | OH_PixelmapNative | Declares a pixel map object defined by the image framework. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [EffectErrorCode](#effecterrorcode) | EffectErrorCode | Enumerates the status codes of the filter effect. |
| [EffectTileMode](#effecttilemode) | EffectTileMode | Enumerates the tile modes of the shader effect. |

## Enum type description

### EffectErrorCode

```c
enum EffectErrorCode
```

**Description**

Enumerates the status codes of the filter effect.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_SUCCESS = 0 | The operation is successful. |
| EFFECT_BAD_PARAMETER = 401 | Invalid parameter. Check the parameter type and range. |
| EFFECT_UNSUPPORTED_OPERATION = 7600201 | The operation is not supported. Check the API usage. |
| EFFECT_UNKNOWN_ERROR = 7600901 | An unidentified error occurred. Possible causes include abnormal system resources or improper API calling. Check the API call parameters and system resource |

### EffectTileMode

```c
enum EffectTileMode
```

**Description**

Enumerates the tile modes of the shader effect.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 14

| Enum item | Description |
| -- | -- |
| CLAMP = 0 | Clamp mode. If the shader effect exceeds its original bounds, the remaining area is filled with the edge color of the shader. Applicable to scenarios requiring |
| REPEAT | Repeat mode. Repeats the shader effect in both horizontal and vertical directions. Applicable to scenarios requiring seamless tiled textures, such as background |
| MIRROR | Mirror mode. Repeats the shader effect in both horizontal and vertical directions, alternating mirrored images so that adjacent images always join seamlessly. Applicable to scenarios requiring continuity while avoiding abrupt repeating |
| DECAL | Decal mode. Renders the shader effect only within its original bounds. Applicable to scenarios requiring precise control over shader boundaries, where areas outside the bounds remain transparent or retain the original |


