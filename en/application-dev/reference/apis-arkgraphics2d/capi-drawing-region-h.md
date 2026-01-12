# drawing_region.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the region in the drawing module, including creating a region, setting the boundary, and destroying a region.

**File to include**: <native_drawing/drawing_region.h>

**Library**: libnative_drawing.so

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
| [bool OH_Drawing_RegionOp(OH_Drawing_Region* region, const OH_Drawing_Region* other, OH_Drawing_RegionOpMode op)](#oh_drawing_regionop) | Combines two regions based on the specified operation mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **region** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **op** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [bool OH_Drawing_RegionSetRect(OH_Drawing_Region* region, const OH_Drawing_Rect* rect)](#oh_drawing_regionsetrect) | Sets the boundary for an **OH_Drawing_Region** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **region** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_RegionSetPath(OH_Drawing_Region* region, const OH_Drawing_Path* path, const OH_Drawing_Region* clip)](#oh_drawing_regionsetpath) | Sets a region to the area described by the path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **region**, **path**, or **clip** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RegionDestroy(OH_Drawing_Region* region)](#oh_drawing_regiondestroy) | Destroys an **OH_Drawing_Region** object and reclaims the memory occupied by the object.|
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
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* | Returns the pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object created.|

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
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object to be copied.|

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
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| int32_t x | X coordinate of the point.|
| int32_t y | Y coordinate of the point.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the region contains the specified point; returns **false** otherwise.|

### OH_Drawing_RegionOp()

```c
bool OH_Drawing_RegionOp(OH_Drawing_Region* region, const OH_Drawing_Region* other, OH_Drawing_RegionOpMode op)
```

**Description**

Combines two regions based on the specified operation mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **region** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **op** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to an [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object, in which the resulting region is saved.|
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* other | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| [OH_Drawing_RegionOpMode](#oh_drawing_regionopmode) op | Operation mode of the region. For details about the available options, see [OH_Drawing_RegionOpMode](capi-drawing-region-h.md#oh_drawing_regionopmode).|

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
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the setting is successful; returns **false** otherwise.|

### OH_Drawing_RegionSetPath()

```c
bool OH_Drawing_RegionSetPath(OH_Drawing_Region* region, const OH_Drawing_Path* path, const OH_Drawing_Region* clip)
```

**Description**

Sets a region to the area described by the path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **region**, **path**, or **clip** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* clip | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the resulting region is not empty; returns false otherwise.|

### OH_Drawing_RegionDestroy()

```c
void OH_Drawing_RegionDestroy(OH_Drawing_Region* region)
```

**Description**

Destroys an **OH_Drawing_Region** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|


### OH_Drawing_RegionEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RegionEmpty(OH_Drawing_Region* region)
```

**Description**

Sets the existing region to empty.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the **region** parameter is empty.|

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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. It is used as an output parameter.|

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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object. It is used as an output parameter.|

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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| int32_t left | X coordinate of the upper left corner of the specified rectangle.|
| int32_t top | Y coordinate of the upper left corner of the specified rectangle.|
| int32_t right | X coordinate of the lower right corner of the specified rectangle.|
| int32_t bottom | Y coordinate of the lower right corner of the specified rectangle.|
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
| [const OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| int32_t left | X coordinate of the upper left corner of the specified rectangle.|
| int32_t top | Y coordinate of the upper left corner of the specified rectangle.|
| int32_t right | X coordinate of the lower right corner of the specified rectangle.|
| int32_t bottom | Y coordinate of the lower right corner of the specified rectangle.|
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
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| int32_t dx | Distance to be translated on the X axis, in pixels.|
| int32_t dy | Distance to be translated on the Y axis, in pixels.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **region** is a null pointer.|
