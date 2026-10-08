# drawing_region.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8ed03ffe90bb2522b0df0e44ac852e6dea1907ea translatedAt=2026-08-24T08:54:52.253Z pushedAt=2026-08-31T09:19:03.424Z -->

## Overview

Defines the functions related to regions, including region creation, boundary setting, and destruction.<br>This module uses a single-thread model, and the caller must manage thread safety and context state switching.

**File to include**: <native_drawing/drawing_region.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_RegionOpMode](#oh_drawing_regionopmode) | OH_Drawing_RegionOpMode | Defines an enum for the operation modes available for a region.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Region* OH_Drawing_RegionCreate(void)](#oh_drawing_regioncreate) | Creates an **OH_Drawing_Region** object for more accurate graphical control.|
| [OH_Drawing_Region* OH_Drawing_RegionCopy(const OH_Drawing_Region* region)](#oh_drawing_regioncopy) | Creates a copy of a region object.|
| [bool OH_Drawing_RegionContains(OH_Drawing_Region* region, int32_t x, int32_t y)](#oh_drawing_regioncontains) | Checks whether a region contains the specified point.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **region** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_RegionOp(OH_Drawing_Region* region, const OH_Drawing_Region* other, OH_Drawing_RegionOpMode op)](#oh_drawing_regionop) | Merges two regions based on the specified region operation type.<br>This API may generate an error code. You can use [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either region or other is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if op is out of the enum range. |
| [bool OH_Drawing_RegionSetRect(OH_Drawing_Region* region, const OH_Drawing_Rect* rect)](#oh_drawing_regionsetrect) | Sets the boundary for an **OH_Drawing_Region** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **region** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_RegionSetPath(OH_Drawing_Region* region, const OH_Drawing_Path* path, const OH_Drawing_Region* clip)](#oh_drawing_regionsetpath) | Sets the region object to the range represented by the path within the specified region.<br>This API may generate an error code. You can use [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of region, path, or clip is NULL. |
| [void OH_Drawing_RegionDestroy(OH_Drawing_Region* region)](#oh_drawing_regiondestroy) | Destroys a region object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_RegionEmpty(OH_Drawing_Region* region)](#oh_drawing_regionempty) | Sets the existing region to empty.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionGetBoundaryPath(const OH_Drawing_Region* region, OH_Drawing_Path* path)](#oh_drawing_regiongetboundarypath) | Sets the path as the boundary of the region. If the region is empty, the path is also empty.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionGetBounds(const OH_Drawing_Region* region, OH_Drawing_Rect* rect)](#oh_drawing_regiongetbounds) | Obtains the smallest bounding rectangle that contains the region.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionIsComplex(const OH_Drawing_Region* region, bool* isComplex)](#oh_drawing_regioniscomplex) | Checks whether the region contains two or more rectangles.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionIsEmpty(const OH_Drawing_Region* region, bool* isEmpty)](#oh_drawing_regionisempty) | Checks whether the region is empty.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionIsRect(const OH_Drawing_Region* region, bool* isRect)](#oh_drawing_regionisrect) | Checks whether the region the same as a rectangle.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionQuickContains(const OH_Drawing_Region* region, int32_t left, int32_t top, int32_t right, int32_t bottom, bool* isContained)](#oh_drawing_regionquickcontains) | Checks whether the region is the same as a single rectangle and contains the specified rectangle.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionQuickReject(const OH_Drawing_Region* region, int32_t left, int32_t top, int32_t right, int32_t bottom, bool* isReject)](#oh_drawing_regionquickreject) | Checks whether the region is empty or does not intersect the specified rectangle.|
| [OH_Drawing_ErrorCode OH_Drawing_RegionTranslate(OH_Drawing_Region* region, int32_t dx, int32_t dy)](#oh_drawing_regiontranslate) | Translates the region by a specified distance on the X and Y axes. If the region is empty, no operation is performed.|

## Enum Description

### OH_Drawing_RegionOpMode

```c
enum OH_Drawing_RegionOpMode
```

**Description**

Enumerates the operation modes available for a region.

**Since**: 12

| Value| Description|
| -- | -- |
| REGION_OP_MODE_DIFFERENCE | Difference operation.|
| REGION_OP_MODE_INTERSECT | Intersection operation.|
| REGION_OP_MODE_UNION | Union operation.|
| REGION_OP_MODE_XOR | XOR operation.|
| REGION_OP_MODE_REVERSE_DIFFERENCE | Reverse difference operation.|
| REGION_OP_MODE_REPLACE | Replacement operation.|

## Function Description

### OH_Drawing_RegionCreate()

```c
OH_Drawing_Region* OH_Drawing_RegionCreate(void)
```

**Description**

Creates an **OH_Drawing_Region** object for more accurate graphical control.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* | The function returns a pointer to the created region object OH_Drawing_Region. |

### OH_Drawing_RegionCopy()

```c
OH_Drawing_Region* OH_Drawing_RegionCopy(const OH_Drawing_Region* region)
```

**Description**

Creates a copy of a region object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* | Returns the pointer to the **OH_Drawing_Region** object created.|

### OH_Drawing_RegionContains()

```c
bool OH_Drawing_RegionContains(OH_Drawing_Region* region, int32_t x, int32_t y)
```

**Description**

Checks whether a region contains the specified point.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **region** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| int32_t x | X-coordinate of the specified coordinate point, in physical pixels (px). |
| int32_t y | Y-coordinate of the specified coordinate point, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the region contains the specified point; returns **false** otherwise.|

### OH_Drawing_RegionOp()

```c
bool OH_Drawing_RegionOp(OH_Drawing_Region* region, const OH_Drawing_Region* other, OH_Drawing_RegionOpMode op)
```

**Description**

Merges two regions based on the specified region operation type.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either region or other is NULL.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if op is not within the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. The region result after the operation is stored in this region object. |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* other | Pointer to another region object OH_Drawing_Region that participates in the merge operation. It is merged with the region specified by the region parameter according to the operation type op. |
| [OH_Drawing_RegionOpMode](#oh_drawing_regionopmode) op | Region operation enum type. For the supported modes, see the OH_Drawing_RegionOpMode enum. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the resulting region is not empty; returns false otherwise.|

### OH_Drawing_RegionSetRect()

```c
bool OH_Drawing_RegionSetRect(OH_Drawing_Region* region, const OH_Drawing_Rect* rect)
```

**Description**

Sets the boundary for an **OH_Drawing_Region** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **region** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the setting is successful; returns **false** otherwise.|

### OH_Drawing_RegionSetPath()

```c
bool OH_Drawing_RegionSetPath(OH_Drawing_Region* region, const OH_Drawing_Path* path, const OH_Drawing_Region* clip)
```

**Description**

Sets the region object to the range represented by the path within the specified region.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of region, path, or clip is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the path object OH_Drawing_Path. |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* clip | Pointer to the region object OH_Drawing_Region used as the clip region. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the resulting region is not empty; returns false otherwise.|

### OH_Drawing_RegionDestroy()

```c
void OH_Drawing_RegionDestroy(OH_Drawing_Region* region)
```

**Description**

Destroys the region object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |

### OH_Drawing_RegionEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionEmpty(OH_Drawing_Region* region)
```

**Description**

Sets the existing region to empty.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if region is a null pointer. |

### OH_Drawing_RegionGetBoundaryPath()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionGetBoundaryPath(const OH_Drawing_Region* region, OH_Drawing_Path* path)
```

**Description**

Sets the path as the boundary of the region. If the region is empty, the path is also empty.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the path object OH_Drawing_Path. Used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **path** is a null pointer.|

### OH_Drawing_RegionGetBounds()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionGetBounds(const OH_Drawing_Region* region, OH_Drawing_Rect* rect)
```

**Description**

Obtains the smallest bounding rectangle that contains the region.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. Used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **rect** is a null pointer.|

### OH_Drawing_RegionIsComplex()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionIsComplex(const OH_Drawing_Region* region, bool* isComplex)
```

**Description**

Checks whether the region contains two or more rectangles.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| bool* isComplex | Whether this region contains multiple rectangles. It is used as an output parameter. **true** means yes; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **isComplex** is a null pointer.|

### OH_Drawing_RegionIsEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionIsEmpty(const OH_Drawing_Region* region, bool* isEmpty)
```

**Description**

Checks whether the region is empty.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| bool* isEmpty | Whether the region is empty. It is used as an output parameter. **true** means yes; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **isEmpty** is a null pointer.|

### OH_Drawing_RegionIsRect()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionIsRect(const OH_Drawing_Region* region, bool* isRect)
```

**Description**

Checks whether the region the same as a rectangle.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| bool* isRect | Whether the region the same as a rectangle. It is used as an output parameter. **true** means yes; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **isRect** is a null pointer.|

### OH_Drawing_RegionQuickContains()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionQuickContains(const OH_Drawing_Region* region, int32_t left, int32_t top, int32_t right, int32_t bottom, bool* isContained)
```

**Description**

Checks whether the region is the same as a single rectangle and contains the specified rectangle.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| int32_t left | X-axis coordinate of the upper-left corner of the specified rectangle, in physical pixels (px). |
| int32_t top | Y-axis coordinate of the upper-left corner of the specified rectangle, in physical pixels (px). |
| int32_t right | X-axis coordinate of the lower-right corner of the specified rectangle, in physical pixels (px). |
| int32_t bottom | Y-axis coordinate of the lower-right corner of the specified rectangle, in physical pixels (px). |
| bool* isContained | Whether the region is the same as a single rectangle and contains the specified rectangle. It is used as an output parameter.<br>**true** if the current region is the same as a single rectangle and contains the specified rectangle; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **isContained** is a null pointer.|

### OH_Drawing_RegionQuickReject()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionQuickReject(const OH_Drawing_Region* region, int32_t left, int32_t top, int32_t right, int32_t bottom, bool* isReject)
```

**Description**

Checks whether the region is empty or does not intersect the specified rectangle.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| int32_t left | X-coordinate of the upper-left corner of the specified rectangle, in physical pixels (px). |
| int32_t top | Y-coordinate of the upper-left corner of the specified rectangle, in physical pixels (px). |
| int32_t right | X-coordinate of the lower-right corner of the specified rectangle, in physical pixels (px). |
| int32_t bottom | Y-coordinate of the lower-right corner of the specified rectangle, in physical pixels (px). |
| bool* isReject | Whether the region is empty or whether the specified rectangle does not intersect with the region. It is used as an output parameter.<br>**true** means yes; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** or **isReject** is a null pointer.|

### OH_Drawing_RegionTranslate()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionTranslate(OH_Drawing_Region* region, int32_t dx, int32_t dy)
```

**Description**

Translates the region by a specified distance on the X and Y axes. If the region is empty, no operation is performed.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the region object OH_Drawing_Region. |
| int32_t dx | Distance to translate along the x-axis, in physical pixels (px). |
| int32_t dy | Distance to translate along the y-axis, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** is a null pointer.|