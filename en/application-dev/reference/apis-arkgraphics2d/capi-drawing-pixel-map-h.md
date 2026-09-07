# drawing_pixel_map.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:47:50.117Z pushedAt=2026-08-31T09:11:56.943Z -->

## Overview

Declares the functions related to the pixel map in the drawing module. It supports obtaining the pixel map defined in this module from the pixel map defined in the image frame, and unlinking the relationship between them.<br>This module uses a single-thread model, and the caller must manage thread safety and context state switching.

**File to include**: \<native_drawing/drawing_pixel_map.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [NativePixelMap_](capi-drawing-nativepixelmap-.md) | NativePixelMap_ | Defines a pixel map defined by the image framework.|
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) | OH_PixelmapNative | Defines a pixel map defined by the image framework.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)](#oh_drawing_pixelmapgetfromnativepixelmap) | Obtains the pixel map object defined by this module from the pixel map object defined by the image frame. After the object is used, call [OH_Drawing_PixelMapDissolve](#oh_drawing_pixelmapdissolve) to unlink it; otherwise, a memory leak may occur. |
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)](#oh_drawing_pixelmapgetfromohpixelmapnative) | Obtains the pixel map object defined by this module from the pixel map object defined by the image frame. After the object is used, call [OH_Drawing_PixelMapDissolve](#oh_drawing_pixelmapdissolve) to unlink it; otherwise, a memory leak may occur. |
| [void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)](#oh_drawing_pixelmapdissolve) | Unlinks the pixel map object defined by this module from the pixel map object defined by the image frame. You must first call [OH_Drawing_PixelMapGetFromNativePixelMap](#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](#oh_drawing_pixelmapgetfromohpixelmapnative) to obtain the pixel map object and establish the association before calling this method to unlink it. |

## Function Description

### OH_Drawing_PixelMapGetFromNativePixelMap()

```c
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)
```

**Description**

Obtains the pixel map defined in this module from the pixel map defined in the image frame. After the object is used, call [OH_Drawing_PixelMapDissolve](#oh_drawing_pixelmapdissolve) to unlink the relationship; otherwise, a memory leak may occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [NativePixelMap_](capi-drawing-nativepixelmap-.md)* nativePixelMap | Pointer to a [NativePixelMap_](capi-drawing-nativepixelmap-.md) object, which is the pixel map defined by the image framework.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* | Returns a pointer to the pixel map object [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) defined by this module. If NULL is returned, the acquisition fails because the parameter nativePixelMap is NULL. |

### OH_Drawing_PixelMapGetFromOhPixelMapNative()

```c
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)
```

**Description**

Obtains the pixel map defined in this module from the pixel map defined in the image frame. After the object is used, call [OH_Drawing_PixelMapDissolve](#oh_drawing_pixelmapdissolve) to unlink the relationship; otherwise, a memory leak may occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md)* pixelmapNative | Pointer to a [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) object, which is the pixel map defined by the image framework.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* | Returns a pointer to the pixel map object [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) defined by this module. If NULL is returned, the acquisition fails because the parameter pixelmapNative is NULL. |

### OH_Drawing_PixelMapDissolve()

```c
void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)
```

**Description**

Unlinks the relationship between the pixel map defined in this module and the pixel map defined in the image frame. You must first call [OH_Drawing_PixelMapGetFromNativePixelMap](#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](#oh_drawing_pixelmapgetfromohpixelmapnative) to obtain the pixel map and establish the relationship before calling this method to unlink it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to an [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|