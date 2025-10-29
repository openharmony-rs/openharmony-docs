# drawing_color_space.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the color space in the drawing module.

**File to include:** <native_drawing/drawing_color_space.h>

**Library**: libnative_drawing.so

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)](#oh_drawing_colorspacecreatesrgb) | Creates an sRGB color space.|
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)](#oh_drawing_colorspacecreatesrgblinear) | Creates an sRGB linear (Gamma 1.0) color space.|
| [void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)](#oh_drawing_colorspacedestroy) | Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_ColorSpaceCreateSrgb()

```
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)
```

**Description**

Creates an sRGB color space.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | Returns a pointer to the [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object created.|

### OH_Drawing_ColorSpaceCreateSrgbLinear()

```
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)
```

**Description**

Creates an sRGB linear (Gamma 1.0) color space.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | Returns a pointer to the [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object created.|

### OH_Drawing_ColorSpaceDestroy()

```
void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)
```

**Description**

Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* colorSpace | Pointer to an [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object.|
