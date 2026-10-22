# drawing_mask_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T08:32:33.868Z pushedAt=2026-08-31T07:46:34.360Z -->

## Overview

Declares the functions related to the objects in the drawing module.<br>This module uses a single-threaded model strategy, and the caller must manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_mask_filter.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_BlurType](#oh_drawing_blurtype) | OH_Drawing_BlurType | Defines an enum for the blur types.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_MaskFilter* OH_Drawing_MaskFilterCreateBlur(OH_Drawing_BlurType blurType, float sigma, bool respectCTM)](#oh_drawing_maskfiltercreateblur) | Creates a mask filter with a blur effect. It is commonly used to add a blur visual effect to drawn content such as graphics and text. After the created mask filter object is used, you must call [OH_Drawing_MaskFilterDestroy](#oh_drawing_maskfilterdestroy) to destroy it and release the memory. |
| [void OH_Drawing_MaskFilterDestroy(OH_Drawing_MaskFilter* maskFilter)](#oh_drawing_maskfilterdestroy) | Destroys an **OH_Drawing_MaskFilter** object and reclaims the memory occupied by the object.|

## Enum Description

### OH_Drawing_BlurType

```c
enum OH_Drawing_BlurType
```

**Description**

Defines an enum for the blur types.

**Since**: 11

| Value| Description|
| -- | -- |
| NORMAL | Blurs both inside and outside the original border.|
| SOLID | Solid inside, blurred outside. |
| OUTER | Draws nothing inside the border, and blurs outside.|
| INNER | Blurs inside the border, and draws nothing outside.|

## Function Description

### OH_Drawing_MaskFilterCreateBlur()

```c
OH_Drawing_MaskFilter* OH_Drawing_MaskFilterCreateBlur(OH_Drawing_BlurType blurType, float sigma, bool respectCTM)
```

**Description**

Creates a mask filter with a blur effect. It is commonly used to add a blur visual effect to drawn content such as graphics and text. After the created mask filter object is used, you must call [OH_Drawing_MaskFilterDestroy](#oh_drawing_maskfilterdestroy) to destroy it and release the memory.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_BlurType](#oh_drawing_blurtype) blurType | Blur type, which specifies the blur operation mode of the mask filter. |
| float sigma | Standard deviation of the Gaussian blur to apply, in pixels. The value must be greater than 0. |
| bool respectCTM | Whether the blur standard deviation is affected by the CTM (current transformation matrix). The value true means the standard deviation is affected by the CTM, and false means it is not affected and remains fixed. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_MaskFilter](capi-drawing-oh-drawing-maskfilter.md)* | Returns the pointer to the **OH_Drawing_MaskFilter** object created.|

### OH_Drawing_MaskFilterDestroy()

```c
void OH_Drawing_MaskFilterDestroy(OH_Drawing_MaskFilter* maskFilter)
```

**Description**

Destroys an **OH_Drawing_MaskFilter** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_MaskFilter](capi-drawing-oh-drawing-maskfilter.md)* maskFilter | Pointer to an **OH_Drawing_MaskFilter** object.|