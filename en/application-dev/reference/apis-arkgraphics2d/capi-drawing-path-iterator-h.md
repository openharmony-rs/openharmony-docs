# drawing_path_iterator.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the path operation iterator object.

**File to include**: <native_drawing/drawing_path_iterator.h>

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
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorCreate(const OH_Drawing_Path* path, OH_Drawing_PathIterator** pathIterator)](#oh_drawing_pathiteratorcreate) | Creates an **OH_Drawing_PathIterator** object.|
| [OH_Drawing_ErrorCode OH_Drawing_PathIteratorDestroy(OH_Drawing_PathIterator* pathIterator)](#oh_drawing_pathiteratordestroy) | Destroys an **OH_Drawing_PathIterator** object and reclaims the memory occupied by the object.|
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
| QUAD = 2 | Adds a quadratic Bezier curve for smooth transitions.|
| CONIC = 3 | Adds a conic curve.|
| CUBIC = 4 | Adds a cubic Bezier curve for smooth transitions.|
| CLOSE = 5 | Closes the path.|
| DONE = CLOSE + 1 | Completes the path configuration.|


## Function Description

### OH_Drawing_PathIteratorCreate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIteratorCreate(const OH_Drawing_Path* path, OH_Drawing_PathIterator** pathIterator)
```

**Description**

Creates an **OH_Drawing_PathIterator** object.

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

Destroys an **OH_Drawing_PathIterator** object and reclaims the memory occupied by the object.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to an [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) object.|

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
| [const OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to an [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) object.|
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
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md)* pathIterator | Pointer to an [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) object.|
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* points | Array of coordinate points.|
| uint32_t count | Size of the coordinate point array.|
| uint32_t offset | Offset of the write position relative to the start point in the array. The value range is [0, count – 4].|
| [OH_Drawing_PathIteratorVerb](capi-drawing-path-iterator-h.md#oh_drawing_pathiteratorverb)* verb | Next operation of the current path, which serves as an output parameter.|

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
| [OH_Drawing_PathIteratorVerb](capi-drawing-path-iterator-h.md#oh_drawing_pathiteratorverb)* verb | Next operation of the current path, which serves as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **pathIterator** or **verb** is a null pointer.|
