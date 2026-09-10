# drawing_record_cmd.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b022504f1a03836c7b154941dafd426a749a94fb translatedAt=2026-08-24T08:50:49.369Z pushedAt=2026-08-31T09:15:00.651Z -->

## Overview

The file defines the functions related to record command objects. It is used to record and replay drawing command sequences, and supports creating a recording canvas, recording drawing operations, and generating replayable command objects.<br>This module adopts a single-thread model policy, and the caller needs to manage thread safety and context state switching.

**File to include**: <native_drawing/drawing_record_cmd.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_RecordCmdUtils* OH_Drawing_RecordCmdUtilsCreate(void)](#oh_drawing_recordcmdutilscreate) | Creates a command recording tool object. |
| [OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsDestroy(OH_Drawing_RecordCmdUtils* recordCmdUtils)](#oh_drawing_recordcmdutilsdestroy) | Destroys a command recording tool object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsBeginRecording(OH_Drawing_RecordCmdUtils* recordCmdUtils,int32_t width, int32_t height, OH_Drawing_Canvas** canvas)](#oh_drawing_recordcmdutilsbeginrecording) | Starts recording. This interface must be used in pair with [OH_Drawing_RecordCmdUtilsFinishRecording](#oh_drawing_recordcmdutilsfinishrecording).<br>The command recording tool generates a recording-type canvas object, on which the drawing APIs can be called to record all subsequent drawing commands. |
| [OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsFinishRecording(OH_Drawing_RecordCmdUtils* recordCmdUtils,OH_Drawing_RecordCmd** recordCmd)](#oh_drawing_recordcmdutilsfinishrecording) | Ends recording. Before calling this interface, [OH_Drawing_RecordCmdUtilsBeginRecording](#oh_drawing_recordcmdutilsbeginrecording) must be called first.<br>The command recording tool ends command recording and stores the drawing commands recorded by the recording-type canvas object into the generated record command object. |
| [OH_Drawing_ErrorCode OH_Drawing_RecordCmdDestroy(OH_Drawing_RecordCmd* recordCmd)](#oh_drawing_recordcmddestroy) | Destroys an **OH_Drawing_RecordCmd** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_RecordCmdUtilsCreate()

```c
OH_Drawing_RecordCmdUtils* OH_Drawing_RecordCmdUtilsCreate(void)
```

**Description**

Creates a record command utility object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md)* | Returns the pointer to the **OH_Drawing_RecordCmdUtils** object created.|

### OH_Drawing_RecordCmdUtilsDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsDestroy(OH_Drawing_RecordCmdUtils* recordCmdUtils)
```

**Description**

Destroys a record command utility object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md)* recordCmdUtils | Pointer to the record command utility object [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **recordCmdUtils** is NULL.|

### OH_Drawing_RecordCmdUtilsBeginRecording()

```c
OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsBeginRecording(OH_Drawing_RecordCmdUtils* recordCmdUtils, int32_t width, int32_t height, OH_Drawing_Canvas** canvas)
```

**Description**

Starts recording. This interface must be used in pair with the [OH_Drawing_RecordCmdUtilsFinishRecording](#oh_drawing_recordcmdutilsfinishrecording) interface.<br>The record command utility generates a recording-type canvas object, on which the drawing interfaces can be called to record all subsequent drawing commands.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md)* recordCmdUtils | Pointer to the record command utility object [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md). |
| int32_t width | Width of the canvas, which must be greater than 0. |
| int32_t height | Height of the canvas, which must be greater than 0. |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)** canvas | Double pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. You do not need to release this pointer.<br>This object does not support nested calling of [OH_Drawing_CanvasDrawRecordCmd](capi-drawing-canvas-h.md#oh_drawing_canvasdrawrecordcmd).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns OH_DRAWING_SUCCESS if the operation is successful.<br> Returns OH_DRAWING_ERROR_INVALID_PARAMETER if recordCmdUtils or canvas is null.<br> Returns OH_DRAWING_ERROR_INVALID_PARAMETER if width or height is less than or equal to 0.<br> Returns OH_DRAWING_ERROR_ALLOCATION_FAILED if the system memory is insufficient. |

### OH_Drawing_RecordCmdUtilsFinishRecording()

```c
OH_Drawing_ErrorCode OH_Drawing_RecordCmdUtilsFinishRecording(OH_Drawing_RecordCmdUtils* recordCmdUtils, OH_Drawing_RecordCmd** recordCmd)
```

**Description**

Finishes recording. Before calling this interface, call the [OH_Drawing_RecordCmdUtilsBeginRecording](#oh_drawing_recordcmdutilsbeginrecording) interface first.<br>The record command utility finishes recording commands and stores the drawing commands recorded by the recording-type canvas object into the generated record command object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md)* recordCmdUtils | Pointer to the record command utility object [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md). It cannot be null. |
| [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md)** recordCmd | Double pointer to the [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md) object. You need to call [OH_Drawing_CanvasDrawRecordCmd](capi-drawing-canvas-h.md#oh_drawing_canvasdrawrecordcmd) to draw the object, and call [OH_Drawing_RecordCmdDestroy](capi-drawing-record-cmd-h.md#oh_drawing_recordcmddestroy) to release it.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **recordCmdUtils** or **recordCmd** is NULL.<br> **OH_DRAWING_ERROR_ALLOCATION_FAILED** if the system memory is insufficient.|

### OH_Drawing_RecordCmdDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_RecordCmdDestroy(OH_Drawing_RecordCmd* recordCmd)
```

**Description**

Destroys an **OH_Drawing_RecordCmd** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md)* recordCmd | Pointer to the [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md) recording command object. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **recordCmd** is NULL.|