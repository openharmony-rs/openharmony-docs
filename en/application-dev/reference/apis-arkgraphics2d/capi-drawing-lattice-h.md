# drawing_lattice.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:32:52.403Z pushedAt=2026-08-31T07:46:13.366Z -->

## Overview

Declares the functions related to the lattice object. A lattice is used to divide an image into fixed regions and scalable regions, solving the problem of key region distortion during image scaling. It keeps the key regions clear and undistorted while allowing flexible scaling of the remaining regions. When the target lattice is large enough, the fixed regions are drawn at their original size; when the target lattice is too small, they are scaled down proportionally to fit the target lattice, and the remaining regions are scaled to fit the remaining space.<br>This module adopts a single-thread model policy, and the caller is responsible for managing thread safety and context state switching.

**File to include:** \<native_drawing/drawing_lattice.h\>

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
| [OH_Drawing_ErrorCode OH_Drawing_LatticeDestroy(OH_Drawing_Lattice* lattice)](#oh_drawing_latticedestroy) | Destroys the rectangle lattice object created by [OH_Drawing_LatticeCreate()](#oh_drawing_latticecreate) and reclaims the memory occupied by the object. Used in pair with [OH_Drawing_LatticeCreate()](#oh_drawing_latticecreate). |
| [OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)](#oh_drawing_latticecreate) | Creates a rectangle lattice object. Divides an image into a rectangle lattice. The lattices that are simultaneously in even columns (the column index is an even number, that is, the 0th, 2nd, 4th... columns) and even rows (the row index is an even number, that is, the 0th, 2nd, 4th... rows) are fixed. If the target lattice is large enough, these fixed lattices are drawn at their original size. If the target lattice is too small to accommodate these fixed lattices, all fixed lattices are scaled down proportionally to fit the target lattice. The remaining lattices are scaled to fit the remaining space. |

## Enum Description

### OH_Drawing_LatticeRectType

```c
enum OH_Drawing_LatticeRectType
```

**Description**

Enumerates the rectangle types for filling the lattice, which determine how the corresponding lattice cells are rendered.

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

Destroys the rectangular lattice object created by [OH_Drawing_LatticeCreate()](#oh_drawing_latticecreate) and reclaims the memory occupied by the object. It is used in pair with [OH_Drawing_LatticeCreate()](#oh_drawing_latticecreate).

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)* lattice | Pointer to the rectangle lattice object [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md) created by [OH_Drawing_LatticeCreate()](#oh_drawing_latticecreate). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if lattice is a null pointer. |

### OH_Drawing_LatticeCreate()

```c
OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)
```

**Description**

Creates a rectangular lattice object. The image is divided into a rectangular lattice. The cells that are simultaneously in even columns (column indexes are even numbers, that is, the 0th, 2nd, 4th... columns) and even rows (row indexes are even numbers, that is, the 0th, 2nd, 4th... rows) are fixed. If the target lattice is large enough, these fixed cells are drawn at their original size. If the target lattice is too small to accommodate these fixed cells, all fixed cells are scaled down proportionally to fit the target lattice. The remaining cells are scaled to fit the remaining space.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| const int* xDivs | Array of X coordinate values used to divide the image. The array elements must be integers, the unit is physical pixels (px), and the array must not be a null pointer. |
| const int* yDivs | Array of Y coordinate values used to divide the image. The array elements must be integers, the unit is physical pixels (px), and the array must not be a null pointer. |
| uint32_t xCount | Size of the array that holds the X coordinates. The value range is [0, 5].|
| uint32_t yCount | Size of the array that holds the Y coordinates. The value range is [0, 5].|
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* bounds | Original bounding rectangle to be drawn. Pass this parameter when a drawing boundary different from the original image is required. If it is not passed (null pointer), the original image rectangle size is used by default. The rectangle coordinate values must be integers, the unit is physical pixels (px), and non-integer values are rounded down. |
| [const OH_Drawing_LatticeRectType](#oh_drawing_latticerecttype)* rectTypes | Array of rectangle types used to fill the lattice. The enumeration values must be within the valid range. If rectTypes is a null pointer, no fill type is specified, all lattice regions draw the image in the DEFAULT mode by default, and rectTypeCount must be 0. |
| uint32_t rectTypeCount | Size of the **rectTypes** array. If **rectTypes** is not a null pointer, the array size must be **(xCount + 1)*(yCount + 1)**.<br>If **rectTypes** is a null pointer, the array size must be **0**.|
| const uint32_t* colors | Array of colors used to fill the lattice. The color values are in ARGB format (0xAARRGGBB). When rectTypes contains FIXED_COLOR, the color at the corresponding position in colors is drawn into the corresponding rectangle lattice, and colors must not be a null pointer. When rectTypes does not contain FIXED_COLOR and colors is a null pointer, no custom color is used to fill the lattice by default. |
| uint32_t colorCount | Size of the colors array. If colors is not a null pointer, the array size must be equal to `(xCount + 1)*(yCount + 1)`.<br>If colors is a null pointer, the array size must be equal to 0. |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)** lattice | Secondary pointer to the rectangle lattice object [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md). It is used as an output parameter to return the result to the caller, and must not be a null pointer. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER for any of the following reasons:<br>- xDivs or yDivs is a null pointer (nullptr);<br>- rectTypes is not a null pointer, and rectTypeCount is not equal to `(xCount + 1)*(yCount + 1)`.<br>- colors is not a null pointer, and colorCount is not equal to `(xCount + 1)*(yCount + 1)`.<br>- rectTypes is a null pointer, and rectTypeCount is not equal to 0.<br>- colors is a null pointer, and colorCount is not equal to 0.<br>- lattice is a null pointer.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if an enum value in rectTypes exceeds the enumeration range. |