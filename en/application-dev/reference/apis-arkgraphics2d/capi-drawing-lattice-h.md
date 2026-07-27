# drawing_lattice.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the rectangular lattice object.

**File to include**: <native_drawing/drawing_lattice.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_LatticeRectType](#oh_drawing_latticerecttype) | OH_Drawing_LatticeRectType | Enumerates the types of rectangles used to fill the lattices. It is applicable only to rectangular lattice objects.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ErrorCode OH_Drawing_LatticeDestroy(OH_Drawing_Lattice* lattice)](#oh_drawing_latticedestroy) | Destroys an **OH_Drawing_Lattice** object and reclaims the memory occupied by the object.|
| [OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)](#oh_drawing_latticecreate) | Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they are drawn at their original size if the target is large enough.<br>If the target is too small to hold the fixed lattices, all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and even rows are scaled to accommodate the remaining space.|

## Enum Description

### OH_Drawing_LatticeRectType

```c
enum OH_Drawing_LatticeRectType
```

**Description**

Enumerates the types of rectangles used to fill the lattices. It is applicable only to rectangular lattice objects.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| DEFAULT | Draws an image into the rectangular lattice.|
| TRANSPARENT | Sets the rectangular lattice to be transparent.|
| FIXED_COLOR | Draws the colors from the **fColors** array of the rectangular lattice object into the lattice.|


## Function Description

### OH_Drawing_LatticeDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_LatticeDestroy(OH_Drawing_Lattice* lattice)
```

**Description**

Destroys an **OH_Drawing_Lattice** object and reclaims the memory occupied by the object.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)* lattice | Pointer to an [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **OHDrawingLattice* lattice** is a null pointer.|

### OH_Drawing_LatticeCreate()

```c
OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)
```

**Description**

Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they are drawn at their original size if the target is large enough. If the target is too small to hold the fixed lattices, all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and even rows are scaled to accommodate the remaining space.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| const int* xDivs | Array of X coordinates used to divide the image. The value is an integer.|
| const int* yDivs | Array of Y coordinates used to divide the image. The value is an integer.|
| uint32_t xCount | Size of the array that holds the X coordinates. The value range is [0, 5].|
| uint32_t yCount | Size of the array that holds the Y coordinates. The value range is [0, 5].|
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* bounds | The original bounding rectangle to be drawn, which defaults to the size of the original image rectangle. The value must be an integer and is rounded down.|
| [const OH_Drawing_LatticeRectType](capi-drawing-lattice-h.md#oh_drawing_latticerecttype)* rectTypes | Array of rectangle types used to fill the lattice.|
| uint32_t rectTypeCount | Size of the **rectTypes** array. If **rectTypes** is not a null pointer, the array size must be **(xCount + 1)*(yCount + 1)**.<br>If **rectTypes** is a null pointer, the array size must be **0**.|
| const uint32_t* colors | Array of colors used to fill the lattice.|
| uint32_t colorCount | Size of the **colors** array. If **colors** is not a null pointer, the array size must be **(xCount + 1)*(yCount + 1)**.<br>If **colors** is a null pointer, the array size must be **0**.|
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)** lattice | Double pointer to an [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md) object, which serves as an output parameter returned to the caller.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>Returns **OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INCORRECT_PARAMETER** for any of the following reasons:<br>- **xDivs** or **yDivs** is a null pointer.<br>- **rectTypes** is not a null pointer, and **rectTypeCount** is not equal to **(xCount + 1)*(yCount + 1)**.<br>- **colors** is not a null pointer, and **colorCount** is not equal to **(xCount + 1)*(yCount + 1)**.<br>- **rectTypes** is a null pointer, and **rectTypeCount** is not equal to **0**.<br>- **colors** is a null pointer, and **colorCount** is not equal to **0**.<br>Returns **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE**, indicating that the enumeration value in **rectTypes** exceeds the valid enumeration range.|
