# drawing_color_space.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T08:25:28.549Z pushedAt=2026-08-31T03:35:57.336Z -->

## Overview

Declares the functions related to color space objects in the drawing module. A color space defines how colors are interpreted and mapped, ensuring consistent presentation of images on different display devices. This file provides functions for creating a standard color space (sRGB) and a linear color space (sRGB Linear), as well as a function for destroying a color space object and reclaiming its memory, for use in scenarios such as image rendering and color management.<br>This module adopts a single-thread model policy, and the caller is responsible for managing thread safety and context state switching.

**File to include:** <native_drawing/drawing_color_space.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)](#oh_drawing_colorspacecreatesrgb) | Creates a standard sRGB color space. It is suitable for scenarios where color values need to be interpreted and rendered according to the sRGB standard. After the created color space object is used, you must call [OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy) to destroy it and release the memory; otherwise, a memory leak occurs. |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)](#oh_drawing_colorspacecreatesrgblinear) | Creates a linear color space with a Gamma value of 1.0. Unlike the standard sRGB color space created by OH_Drawing_ColorSpaceCreateSrgb, the linear color space is suitable for scenarios that require linear color computation (such as blending and lighting). After the created color space object is used, you must call [OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy) to destroy it and release the memory; otherwise, a memory leak occurs. |
| [void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)](#oh_drawing_colorspacedestroy) | Destroys a color space object and reclaims the memory occupied by the object. |

## Function Description

### OH_Drawing_ColorSpaceCreateSrgb()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)
```

**Description**

Creates a standard sRGB color space. It applies to scenarios where color values need to be interpreted and rendered according to the sRGB standard. After use, the created color space object must be destroyed and its memory released by calling [OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy); otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | Pointer to the created color space object [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md). |

### OH_Drawing_ColorSpaceCreateSrgbLinear()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)
```

**Description**

Creates a linear color space with a Gamma value of 1.0. Unlike the standard sRGB color space created by OH_Drawing_ColorSpaceCreateSrgb, the linear color space applies to scenarios that require linear color calculations (such as blending and lighting). After use, the created color space object must be destroyed and its memory released by calling [OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy); otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | Pointer to the created color space object [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md). |

### OH_Drawing_ColorSpaceDestroy()

```c
void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)
```

**Description**

Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* colorSpace | Pointer to the color space object [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) to be destroyed. |