# drawing_pixel_map.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the pixel map in the drawing module.

**File to include**: <native_drawing/drawing_pixel_map.h>

**Library**: libnative_drawing.so

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
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)](#oh_drawing_pixelmapgetfromnativepixelmap) | Obtains the pixel map defined by this module from a pixel map defined by the image framework.|
| [OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)](#oh_drawing_pixelmapgetfromohpixelmapnative) | Obtains the pixel map defined by this module from a pixel map defined by the image framework.|
| [void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)](#oh_drawing_pixelmapdissolve) | Removes the relationship between a pixel map defined by this module and a pixel map defined by the image framework. The relationship is established by calling [OH_Drawing_PixelMapGetFromNativePixelMap](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromohpixelmapnative).|

## Function Description

### OH_Drawing_PixelMapGetFromNativePixelMap()

```
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromNativePixelMap(NativePixelMap_* nativePixelMap)
```

**Description**

Obtains the pixel map defined by this module from a pixel map defined by the image framework.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [NativePixelMap_](capi-drawing-nativepixelmap-.md)* nativePixelMap | Pointer to a [NativePixelMap_](capi-drawing-nativepixelmap-.md) object, which is the pixel map defined by the image framework.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* | Returns the pointer to an [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object, which is the pixel map defined by this module. If NULL is returned, the creation fails. The possible failure cause is that **NativePixelMap_** is NULL.|

### OH_Drawing_PixelMapGetFromOhPixelMapNative()

```
OH_Drawing_PixelMap* OH_Drawing_PixelMapGetFromOhPixelMapNative(OH_PixelmapNative* pixelmapNative)
```

**Description**

Obtains the pixel map defined by this module from a pixel map defined by the image framework.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md)* pixelmapNative | Pointer to a [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) object, which is the pixel map defined by the image framework.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* | Returns the pointer to an [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object, which is the pixel map defined by this module. If NULL is returned, the creation fails. The possible failure cause is that **OH_PixelmapNative** is NULL.|

### OH_Drawing_PixelMapDissolve()

```
void OH_Drawing_PixelMapDissolve(OH_Drawing_PixelMap* pixelMap)
```

**Description**

Removes the relationship between a pixel map defined by this module and a pixel map defined by the image framework. The relationship is established by calling [OH_Drawing_PixelMapGetFromNativePixelMap](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromnativepixelmap) or [OH_Drawing_PixelMapGetFromOhPixelMapNative](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapgetfromohpixelmapnative).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to an [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|
