# drawing_pixel_map.h

## Overview

This file declares the functions related to the pixel map in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NativePixelMap_](capi-drawing-nativepixelmap-.md) | NativePixelMap_ | Defines a pixel map defined by the image framework. |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) | OH_PixelmapNative | Defines a pixel map defined by the image framework. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)](#oh_drawing_pixelmapgetfromnativepixelmap) | Obtains the pixel map defined by this module from a pixel map defined by the image framework. |
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)](#oh_drawing_pixelmapgetfromohpixelmapnative) | Obtains the pixel map defined by this module from a pixel map defined by the image framework. |
| [void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)](#oh_drawing_pixelmapdissolve) | Removes the relationship between a pixel map defined by this module and a pixel map defined by the image framework. The relationship is established by calling [OH_Drawing_PixelMapGetFromNativePixelMap](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromohpixelmapnative) . |

## Function description

### OH_Drawing_PixelMapGetFromNativePixelMap()

```c
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)
```

**Description**

Obtains the pixel map defined by this module from a pixel map defined by the image framework.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [NativePixelMap_](capi-drawing-nativepixelmap-.md)* nativePixelMap | Pointer to a [NativePixelMap_](capi-drawing-nativepixelmap-.md) object, which is the pixel map defined by the image framework. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_PixelMap* | Returns the pointer to an {@link OH_Drawing_PixelMap} object, which is the pixel map defined by this module.  If NULL is returned, the creation fails. The possible failure cause is that NativePixelMap_ is NULL. |

### OH_Drawing_PixelMapGetFromOhPixelMapNative()

```c
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)
```

**Description**

Obtains the pixel map defined by this module from a pixel map defined by the image framework.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md)* pixelmapNative | Pointer to a [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) object, which is the pixel map defined by the image framework. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_PixelMap* | Returns the pointer to an {@link OH_Drawing_PixelMap} object, which is the pixel map defined by this module.  If NULL is returned, the creation fails. The possible failure cause is that OH_PixelmapNative is NULL. |

### OH_Drawing_PixelMapDissolve()

```c
void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)
```

**Description**

Removes the relationship between a pixel map defined by this module and a pixel map defined by the image framework. The relationship is established by calling [OH_Drawing_PixelMapGetFromNativePixelMap](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromohpixelmapnative) .

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_PixelMap* pixelMap | Pointer to an {@link OH_Drawing_PixelMap} object. |


