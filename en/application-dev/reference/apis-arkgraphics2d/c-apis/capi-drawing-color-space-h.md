# drawing_color_space.h

## Overview

This file declares the functions related to the color space in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

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

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorSpace* | Returns a pointer to the {@link OH_Drawing_ColorSpace} object created. |

### OH_Drawing_ColorSpaceCreateSrgbLinear()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)
```

**Description**

Creates an sRGB linear (Gamma 1.0) color space.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ColorSpace* | Returns a pointer to the {@link OH_Drawing_ColorSpace} object created. |

### OH_Drawing_ColorSpaceDestroy()

```c
void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)
```

**Description**

Destroys an **OH_Drawing_ColorSpace** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ColorSpace* colorSpace | Pointer to an {@link OH_Drawing_ColorSpace} object. |


