# drawing_color.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=357665bbb6caa6d8123e7eb4a2cbf8a969d1a249 translatedAt=2026-11-04T10:26:14.054Z pushedAt=2026-11-04T10:29:22.691Z nl=1 -->

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
| uint32_t alpha | Alpha, which is a variable ranging from 0x00 to 0xFF.|
| uint32_t red | Read, which is a variable ranging from 0x00 to 0xFF.|
| uint32_t green | Green, which is a variable ranging from 0x00 to 0xFF.|
| uint32_t blue | Blue, which is a variable ranging from 0x00 to 0xFF.|

**Return value**

| Type| Description|
| -- | -- |
| uint32_t | Returns a 32-bit (ARGB) variable that describes the color.|


