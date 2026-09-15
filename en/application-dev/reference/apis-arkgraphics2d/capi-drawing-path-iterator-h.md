# drawing_path_iterator.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:43:39.781Z pushedAt=2026-08-31T08:56:24.603Z -->

## Overview

Declares the functions related to the path operation iterator object. The path operation iterator is used to traverse the operation commands in a path (such as move, line, Bezier curve, and close). The iterator traverses each operation command in sequence from the start position of the path and internally maintains the current traversal position. It supports creating and destroying the iterator, checking whether there is a next operation, reading the next operation and advancing the iterator, and peeking at the next operation without moving the iterator. Through the iterator, you can read the path operation information one by one without modifying the original path.<br>This module adopts a single-thread model strategy. The caller needs to manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_path_iterator.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_PathIteratorVerb](#oh_drawing_pathiteratorverb) | OH_Drawing_PathIteratorVerb | Enumerates the path operation types contained in an iterator. It is used to read path operation instructions.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorCreate(const OH_Drawing_Path* path, OH_Drawing_PathIterator** pathIterator)](#oh_drawing_pathiteratorcreate) | Creates a path operation iterator object. After use, you must call [OH_Drawing_PathIteratorDestroy](#oh_drawing_pathiteratordestroy) to destroy the iterator object and release memory; otherwise, memory leaks may occur. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorDestroy(OH_Drawing_PathIterator* pathIterator)](#oh_drawing_pathiteratordestroy) | Destroys a path operation iterator object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorHasNext(const OH_Drawing_PathIterator* pathIterator, bool* hasNext)](#oh_drawing_pathiteratorhasnext) | Checks whether there is any next operation in the path operation iterator.|
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorNext(OH_Drawing_PathIterator* pathIterator, OH_Drawing_Point2D* points, uint32_t count, uint32_t offset, OH_Drawing_PathIteratorVerb* verb)](#oh_drawing_pathiteratornext) | Retrieves the next operation in this path and moves the iterator to that operation.|
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorPeek(const OH_Drawing_PathIterator* pathIterator, OH_Drawing_PathIteratorVerb* verb)](#oh_drawing_pathiteratorpeek) | Retrieves the next operation in this path, without moving the iterator.|

## Enum Description

### OH_Drawing_PathIteratorVerb

```c
enum OH_Drawing_PathIteratorVerb
```

**Description**

Enumerates the path operation types contained in an iterator. It is used to read path operation instructions.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| MOVE = 0 | Sets the start point of the path.|
| LINE = 1 | Adds a line segment.|
| QUAD = 2 | Add a quadratic Bezier curve. |
| CONIC = 3 | Adds a conic curve.|
| CUBIC = 4 | Add a cubic Bezier curve. |
| CLOSE = 5 | Closes the path.|
| DONE = CLOSE + 1  | Indicates the end of path operation iteration. |

## Function Description

### OH_Drawing_PathIteratorCreate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorCreate(const OH_Drawing_Path* path, OH_Drawing_PathIterator** pathIterator)
```

**Description**

Creates a path operation iterator object. After use, you must call [OH_Drawing_PathIteratorDestroy](#oh_drawing_pathiteratordestroy) to destroy the iterator object and release memory; otherwise, memory leaks may occur.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)** pathIterator | Double pointer to an [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) object, which serves as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **path** or **pathIterator** is a null pointer.|

### OH_Drawing_PathIteratorDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorDestroy(OH_Drawing_PathIterator* pathIterator)
```

**Description**

Destroys a path operation iterator object and reclaims the memory occupied by the object.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to the path operation iterator object [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) to be destroyed. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **pathIterator** is a null pointer.|

### OH_Drawing_PathIteratorHasNext()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorHasNext(const OH_Drawing_PathIterator* pathIterator, bool* hasNext)
```

**Description**

Checks whether there is any next operation in the path operation iterator.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to the path operation iterator object [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md), used to determine whether there is a next operation. |
| bool* hasNext | Whether there is a next operation in the path operation iterator, which serves as an output parameter. A value of **true** means there is a next operation; **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **pathIterator** or **hasNext** is a null pointer.|

### OH_Drawing_PathIteratorNext()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorNext(OH_Drawing_PathIterator* pathIterator, OH_Drawing_Point2D* points, uint32_t count, uint32_t offset, OH_Drawing_PathIteratorVerb* verb)
```

**Description**

Retrieves the next operation in this path and moves the iterator to that operation.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to the path operation iterator object [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md). After the call, the iterator moves forward to the position of this operation. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* points | Coordinate point array, used as an output parameter to receive the coordinate points corresponding to the next operation. The coordinate points are written starting from the offset position of the array. The caller must pre-allocate memory of a size not less than count; otherwise, out-of-bounds memory writes may occur. |
| uint32_t count | Number of elements in the coordinate point array. |
| uint32_t offset | Offset of the start position for writing coordinate points in the array relative to the start position (index 0) of the array. The value ranges from 0 to count-4. |
| [OH_Drawing_PathIteratorVerb](#oh_drawing_pathiteratorverb)* verb | Next operation of the current path. Used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **pathIterator**, **points**, or **verb** is a null pointer.<br>**OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** if **count** is less than offset + 4.|

### OH_Drawing_PathIteratorPeek()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorPeek(const OH_Drawing_PathIterator* pathIterator, OH_Drawing_PathIteratorVerb* verb)
```

**Description**

Retrieves the next operation in this path, without moving the iterator.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to an [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) object.|
| [OH_Drawing_PathIteratorVerb](#oh_drawing_pathiteratorverb)* verb | Indicates the next operation of the current path. Used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **pathIterator** or **verb** is a null pointer.|