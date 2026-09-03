# drawing_color.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=e334bbf1b8b1bb6c81821f8596b59cf488b76ebd translatedAt=2026-08-24T08:25:04.641Z pushedAt=2026-08-31T03:34:36.984Z -->

## Overview

This module defines the functions related to colors.<br>This module adopts a single-thread model. The caller must manage thread safety and context state switching.

**File to include**: <native_drawing/drawing_color.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [uint32_t OH_Drawing_ColorSetArgb(uint32_t alpha, uint32_t red, uint32_t green, uint32_t blue)](#oh_drawing_colorsetargb) | Converts four variables (alpha, red, green, and blue) into a 32-bit (ARGB) variable that describes a color.|

## Function Description

### OH_Drawing_ColorSetArgb()

```c
uint32_t OH_Drawing_ColorSetArgb(uint32_t alpha, uint32_t red, uint32_t green, uint32_t blue)
```

**Description**

Converts four variables (alpha, red, green, and blue) into a 32-bit (ARGB) variable that describes a color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| uint32_t alpha | Variable that describes the alpha (transparency), with a variable range of 0x00 to 0xFF. When out of range, take the lower 8 significant bits. |
| uint32_t red | Variable that describes the red, with a variable range of 0x00 to 0xFF. When out of range, take the lower 8 significant bits. |
| uint32_t green | Variable that describes the green, with a variable range of 0x00 to 0xFF. When out of range, take the lower 8 significant bits. |
| uint32_t blue | Variable that describes the blue, with a variable range of 0x00 to 0xFF. When out of range, take the lower 8 significant bits. |

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | A 32-bit (ARGB) variable that describes a color. |