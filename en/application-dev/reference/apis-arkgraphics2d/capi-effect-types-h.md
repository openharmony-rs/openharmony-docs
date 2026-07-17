# effect_types.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cb84f8fe2e38bbeba25c5506a75a0804a063c158 translatedAt=2026-07-16T06:36:35.636Z pushedAt=2026-07-16T07:16:04.916Z -->

## Overview

Declares the data types for filter effects, used to define the matrices, status codes, and tile modes for filter effects, and supports scenarios such as creating custom filter effects and processing image shader tiling.

The status code types defined in this document are used for status returns of related APIs. For the usage instructions of status codes for specific APIs, see the corresponding API documentation.

**File to include**: <native_effect/effect_types.h>

**Library**: libnative_effect.so

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [effectKit](capi-effectkit.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md) | - | Defines a 4x5 matrix for creating a filter effect, with elements of floating-point numbers. |
| [OH_Filter](capi-effectkit-oh-filter.md) | OH_Filter | Defines a filter struct used with EffectKit module APIs to implement filter effect processing. |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) | OH_PixelmapNative | Declares a pixel map object defined by the image framework. |

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [EffectErrorCode](#effecterrorcode) | EffectErrorCode | Enumerates the status codes of the filter effect. These status codes are returned when filter effect APIs are used. Developers should determine the operation result based on the returned status code and handle it accordingly. For usage instructions of the status codes for specific APIs, see the corresponding API documentation. |
| [EffectTileMode](#effecttilemode) | EffectTileMode | Enumerates the tile modes of the shader effect.|

## Enum Description

### EffectErrorCode

```c
enum EffectErrorCode
```

**Description**

Enumerates the status codes of the filter effect. These status codes are returned when using filter effect APIs. Developers should determine the operation result based on the returned status code and handle it accordingly. For the usage instructions of status codes for specific APIs, see the corresponding API documentation.

**Since**: 12

| Value| Description|
| -- | -- |
| EFFECT_SUCCESS = 0 | The operation is successful. |
| EFFECT_BAD_PARAMETER = 401 | Invalid parameter. Check the parameter type and range. |
| EFFECT_UNSUPPORTED_OPERATION = 7600201 | The operation is not supported. Check the API usage. |
| EFFECT_UNKNOWN_ERROR = 7600901 | An unidentified error occurred. Possible causes include abnormal system resources or improper API calling. Check the API call parameters and system resource status first. |

### EffectTileMode

```c
enum EffectTileMode
```

**Description**

Enumerates the tile modes of the shader effect.

**Since**: 14

| Value| Description|
| -- | -- |
| CLAMP = 0 | Clamp mode. If the shader effect exceeds its original bounds, the remaining area is filled with the edge color of the shader. Applicable to scenarios requiring a smooth transition to a solid color background. |
| REPEAT = 1 | Repeat mode. Repeats the shader effect in both horizontal and vertical directions. Applicable to scenarios requiring seamless tiled textures, such as background pattern filling. |
| MIRROR = 2 | Mirror mode. Repeats the shader effect in both horizontal and vertical directions, alternating mirrored images so that adjacent images always join seamlessly. Applicable to scenarios requiring continuity while avoiding abrupt repeating edges, such as gradient backgrounds. |
| DECAL = 3 | Decal mode. Renders the shader effect only within its original bounds. Applicable to scenarios requiring precise control over shader boundaries, where areas outside the bounds remain transparent or retain the original content. |