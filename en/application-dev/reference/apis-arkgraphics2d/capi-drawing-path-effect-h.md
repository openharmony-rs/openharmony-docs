# drawing_path_effect.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:45:45.193Z pushedAt=2026-08-31T08:45:24.318Z -->

## Overview

This file declares the functions related to the path effect. A path effect is a mechanism that applies geometric transformation to a path being drawn. It modifies the geometric shape of the path before the path is drawn onto the canvas, for example, turning sharp corners into rounded corners and turning a continuous path into a dashed one. Multiple path effects can be used together by composing (applying them in sequence) or summing (applying them independently and then merging the results). It supports creating a compose path effect, a corner path effect, a dash path effect, a discrete path effect, a sum path effect, and so on.<br>This module uses a single-thread model policy. The caller must manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_path_effect.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_PathDashStyle](#oh_drawing_pathdashstyle) | OH_Drawing_PathDashStyle | Defines an enum for the drawing styles for path effects.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_PathEffect* OH_Drawing_CreateComposePathEffect(OH_Drawing_PathEffect* outer, OH_Drawing_PathEffect* inner)](#oh_drawing_createcomposepatheffect) | Creates a path effect object that composes two path effects. The inner path effect is applied first, and then the outer path effect is applied. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur. |
| [OH_Drawing_PathEffect* OH_Drawing_CreateCornerPathEffect(float radius)](#oh_drawing_createcornerpatheffect) | Creates a path effect object that turns the corners of a path into rounded corners with the specified radius. This path effect detects the corners (turning points) in the path and replaces the sharp corners with arcs of the specified radius, so that the path transitions smoothly at the corners. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur. |
| [OH_Drawing_PathEffect* OH_Drawing_CreateDashPathEffect(float* intervals, int count, float phase)](#oh_drawing_createdashpatheffect) | Creates a path effect object with a dashed effect. The dashed effect is determined by a set of dash-on interval and dash-off interval data. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the value of the error code.<br>If intervals is nullptr or count is less than or equal to 0, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| [OH_Drawing_PathEffect* OH_Drawing_CreateDiscretePathEffect(float segLength, float deviation)](#oh_drawing_creatediscretepatheffect) | Creates a path effect object that breaks a path into segments and produces irregular distribution on the path. This path effect divides the path into multiple line segments according to segLength, and randomly offsets the end point of each line segment within the deviation range, thereby producing an irregularly distributed visual effect. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur. |
| [OH_Drawing_PathEffect* OH_Drawing_CreatePathDashEffect(const OH_Drawing_Path* path, float advance, float phase, OH_Drawing_PathDashStyle type)](#oh_drawing_createpathdasheffect) | Creates a path effect object with a dashed effect, using the specified path as the dash segment style and repeatedly arranging it along the target path at the step specified by advance. Unlike [OH_Drawing_CreateDashPathEffect](#oh_drawing_createdashpatheffect), which uses a dash interval array to control on/off, this API uses the specified path as the dash segment shape. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur. |
| [OH_Drawing_PathEffect* OH_Drawing_CreateSumPathEffect(OH_Drawing_PathEffect* firstPathEffect, OH_Drawing_PathEffect* secondPathEffect)](#oh_drawing_createsumpatheffect) | Creates a path effect object that sums two path effects. Unlike [OH_Drawing_CreateComposePathEffect](#oh_drawing_createcomposepatheffect), which applies the two path effects in sequence, this API applies the two path effects independently and then sums the results. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur. |
| [void OH_Drawing_PathEffectDestroy(OH_Drawing_PathEffect* pathEffect)](#oh_drawing_patheffectdestroy) | Destroys the path effect object and reclaims the memory occupied by the object. After use, you must call this method to destroy the path effect; otherwise, memory leak will occur. |

## Enum Description

### OH_Drawing_PathDashStyle

```c
enum OH_Drawing_PathDashStyle
```

**Description**

Enumerates the drawing styles for path effects.

**Since**: 18

| Value| Description|
| -- | -- |
| DRAWING_PATH_DASH_STYLE_TRANSLATE | Indicates that the dashed segment is translated along the path without rotation or deformation. |
| DRAWING_PATH_DASH_STYLE_ROTATE | Indicates that the dashed segment rotates along the path so that its direction follows the tangent direction of the path. |
| DRAWING_PATH_DASH_STYLE_MORPH | Indicates that the dashed segment deforms along the path to adapt to the path direction. |

## Function Description

### OH_Drawing_CreateComposePathEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreateComposePathEffect(OH_Drawing_PathEffect* outer, OH_Drawing_PathEffect* inner)
```

**Description**

Creates a path effect object that composes two path effects. The inner path effect is applied first, and then the outer path effect is applied. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* outer | Pointer to an outer effect, which is an [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) object.|
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* inner | Pointer to an inner effect, which is an [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | Pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md).<br> If it returns nullptr, creation failure occurs, and the reason is that outer or inner is nullptr. |

### OH_Drawing_CreateCornerPathEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreateCornerPathEffect(float radius)
```

**Description**

Creates a path effect object that turns the corners of a path into rounded corners with a specified radius. This path effect detects the corners (turning points) in the path and replaces the sharp corners with arcs of the specified radius, so that the path transitions smoothly at the turning points. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| float radius | Radius of the corner. The value range is greater than 0, and the unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | Returns a pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md).<br> If it returns nullptr, creation fails, the reason is that radius is less than or equal to 0. |

### OH_Drawing_CreateDashPathEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreateDashPathEffect(float* intervals, int count, float phase)
```

**Description**

Creates a path effect object with a dashed effect. The dashed effect is determined by a set of dash on interval and dash off interval data. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the value of the error code.<br>If intervals is nullptr or count is less than or equal to 0, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| float* intervals | Pointer to the dash interval array. The value of an even-indexed item indicates the length of the visible segment (on) of the dash, and the value of an odd-indexed item indicates the length of the gap segment (off) of the dash. The unit is physical pixel (px). |
| int count | Number of elements in the dash interval array. The value range is greater than 0 and must be an even number. |
| float phase | Offset in the dash interval array, used to control the starting position of dash drawing. The unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | Returns a pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md). |

### OH_Drawing_CreateDiscretePathEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreateDiscretePathEffect(float segLength, float deviation)
```

**Description**

Creates a path effect object that breaks a path into segments and produces irregular distribution on the path. This path effect divides the path into multiple line segments according to segLength, and randomly offsets the end point of each line segment within the deviation range, thereby producing an irregularly distributed visual effect. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| float segLength | Length of each discrete operation along the path. The value range is greater than 0, and the unit is physical pixel (px). |
| float deviation | Maximum deviation of the endpoint during drawing. The unit is physical pixel (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | Returns a pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md). |

### OH_Drawing_CreatePathDashEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreatePathDashEffect(const OH_Drawing_Path* path, float advance, float phase, OH_Drawing_PathDashStyle type)
```

**Description**

Creates a path effect object with a dashed effect, using a specified path as the dash segment style and repeatedly arranging it along the target path at the step specified by advance. Unlike [OH_Drawing_CreateDashPathEffect](#oh_drawing_createdashpatheffect), which uses a dash interval array to control the on/off state, this API uses a specified path as the dash segment shape. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float advance | Step length of the dash segment. The value range is greater than 0, and the unit is physical pixel px. |
| float phase | Initial offset of the dash style, used to control the start position of dash segment drawing. The unit is physical pixel px. |
| [OH_Drawing_PathDashStyle](#oh_drawing_pathdashstyle) type | Style of the dashed path effect. For details about the values, see the [OH_Drawing_PathDashStyle](#oh_drawing_pathdashstyle) enum. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | return a pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md).<br> If it returns nullptr, creation failure occurs. The reason is that path is nullptr or advance is less than or equal to 0. |

### OH_Drawing_CreateSumPathEffect()

```c
OH_Drawing_PathEffect* OH_Drawing_CreateSumPathEffect(OH_Drawing_PathEffect* firstPathEffect, OH_Drawing_PathEffect* secondPathEffect)
```

**Description**

Creates a path effect object that sums two path effects. Unlike [OH_Drawing_CreateComposePathEffect](#oh_drawing_createcomposepatheffect), which applies the two path effects in sequence, this API applies the two path effects independently and then sums the results. After use, you must call [OH_Drawing_PathEffectDestroy](#oh_drawing_patheffectdestroy) to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* firstPathEffect | Pointer to the first path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) that participates in the sum. |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* secondPathEffect | Pointer to the second path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) that participates in the sum. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* | Returns a pointer to the created path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md).<br> If it returns nullptr, creation fails. The reason is that firstPathEffect or secondPathEffect is nullptr. |

### OH_Drawing_PathEffectDestroy()

```c
void OH_Drawing_PathEffectDestroy(OH_Drawing_PathEffect* pathEffect)
```

**Description**

Destroys a path effect object and reclaims the memory occupied by the object. After use, you must call this method to destroy the path effect; otherwise, memory leak will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md)* pathEffect | Pointer to the path effect object [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) to be destroyed. |