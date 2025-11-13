# drawing_register_font.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the functions related to the font manager in the drawing module.

**File to include**: <native_drawing/drawing_register_font.h>

**Library**: libnative_drawing.so

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [uint32_t OH_Drawing_RegisterFont(OH_Drawing_FontCollection*, const char* fontFamily, const char* familySrc)](#oh_drawing_registerfont) | Registers a custom font with the font manager. The supported font file formats are .ttf and .otf.|
| [uint32_t OH_Drawing_RegisterFontBuffer(OH_Drawing_FontCollection*, const char* fontFamily, uint8_t* fontBuffer,size_t length)](#oh_drawing_registerfontbuffer) | Registers a font buffer with the font manager.|
| [uint32_t OH_Drawing_UnregisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily)](#oh_drawing_unregisterfont) | Unregisters a custom font by font family name.<br> Unregistering a font that is currently in use may lead to text rendering exceptions (such as garbled characters or missing glyphs).<br> All typography objects using the unregistered font family should be destroyed and re-created.|

## Function Description

### OH_Drawing_RegisterFont()

```
uint32_t OH_Drawing_RegisterFont(OH_Drawing_FontCollection*, const char* fontFamily, const char* familySrc)
```

**Description**

Registers a custom font with the font manager. The supported font file formats are .ttf and .otf.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Pointer to the family name of the font to register.|
| const char* familySrc | Pointer to the path of the font file.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns **0** if the font is registered; returns **1** if the file does not exist; returns **2** if opening the file fails; returns **3** if reading the file fails; returns **4** if the file is not found; returns **5** if the file size is not obtained; returns **9** if the file is damaged.|

### OH_Drawing_RegisterFontBuffer()

```
uint32_t OH_Drawing_RegisterFontBuffer(OH_Drawing_FontCollection*, const char* fontFamily, uint8_t* fontBuffer,size_t length)
```

**Description**

Registers a font buffer with the font manager.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* |  Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Pointer to the family name of the font to register.|
| uint8_t* fontBuffer | Pointer to the buffer of the font file.|
| size_t length | Length of the font file.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns **0** if the font is registered; returns **6** if the buffer size is zero; returns **7** if the font set is empty; returns **9** if the file is damaged.|

### OH_Drawing_UnregisterFont()

```
uint32_t OH_Drawing_UnregisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily)
```

**Description**

Unregisters a custom font by font family name.

- Unregistering a font that is currently in use may lead to text rendering exceptions (such as garbled characters or missing glyphs).

All typography objects using the unregistered font family should be destroyed and re-created.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Name of the font family to be unregistered.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns the result code. **0**: success; **8**: invalid input parameter; **1**: failure.|
