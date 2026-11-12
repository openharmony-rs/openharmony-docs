# drawing_color_space.h

## Overview

This file declares the functions related to the color space in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)](#oh_drawing_colorspacecreatesrgb) | Creates an sRGB color space. |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)](#oh_drawing_colorspacecreatesrgblinear) | Creates an sRGB linear (Gamma 1.0) color space. |
| [void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)](#oh_drawing_colorspacedestroy) | Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_ColorSpaceCreateSrgb()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)
```

**Description**

Creates an sRGB color space.

<!--Device-OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)--><!--Device-OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ColorSpace*](capi-drawing-oh-drawing-colorspace.md) | Returns a pointer to the [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object created. |

### OH_Drawing_ColorSpaceCreateSrgbLinear()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)
```

**Description**

Creates an sRGB linear (Gamma 1.0) color space.

<!--Device-OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)--><!--Device-OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_ColorSpace*](capi-drawing-oh-drawing-colorspace.md) | Returns a pointer to the [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object created. |

### OH_Drawing_ColorSpaceDestroy()

```c
void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)
```

**Description**

Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object.

<!--Device-void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)--><!--Device-void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* colorSpace | Pointer to an [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) object. |


