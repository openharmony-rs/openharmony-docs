# drawing_font_collection.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the functions related to the font collection in the drawing module.

**File to include**: <native_drawing/drawing_font_collection.h>

**Library**: libnative_drawing.so

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection* OH_Drawing_CreateFontCollection(void)](#oh_drawing_createfontcollection) | Creates an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| [void OH_Drawing_DestroyFontCollection(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_destroyfontcollection) | Destroys an **OH_Drawing_FontCollection** object and reclaims the memory occupied by the object.|
| [void OH_Drawing_DisableFontCollectionFallback(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_disablefontcollectionfallback) | Disables the system fonts.|
| [void OH_Drawing_DisableFontCollectionSystemFont(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_disablefontcollectionsystemfont) | Disables the system fonts.|
| [OH_Drawing_FontCollection* OH_Drawing_CreateSharedFontCollection(void)](#oh_drawing_createsharedfontcollection) | Creates a shareable [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| [void OH_Drawing_ClearFontCaches(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_clearfontcaches) | Clears the font cache. (The font cache has a memory limit and a clearing mechanism. It occupies limited memory. You are not advised to clear it unless otherwise required.)|
| [OH_Drawing_FontCollection* OH_Drawing_GetFontCollectionGlobalInstance(void)](#oh_drawing_getfontcollectionglobalinstance) | Obtains the global [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object, which can be used to sense the theme font information. Do not release the object.|

## Function Description

### OH_Drawing_CreateFontCollection()

```
OH_Drawing_FontCollection* OH_Drawing_CreateFontCollection(void)
```

**Description**

Creates an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Returns the pointer to the **OH_Drawing_FontCollection** object created. The **OH_Drawing_FontCollection** object created by this function cannot be shared by multiple [OH_Drawing_TypographyCreate](capi-drawing-oh-drawing-typographycreate.md) objects. You need to use the [OH_Drawing_CreateSharedFontCollection](capi-drawing-font-collection-h.md#oh_drawing_createsharedfontcollection) function to create an **OH_Drawing_FontCollection** object for sharing.|

### OH_Drawing_DestroyFontCollection()

```
void OH_Drawing_DestroyFontCollection(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Destroys an **OH_Drawing_FontCollection** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an **OH_Drawing_FontCollection** object.|

### OH_Drawing_DisableFontCollectionFallback()

```
void OH_Drawing_DisableFontCollectionFallback(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Disables the system fonts.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|

### OH_Drawing_DisableFontCollectionSystemFont()

```
void OH_Drawing_DisableFontCollectionSystemFont(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Disables the system fonts.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|

### OH_Drawing_CreateSharedFontCollection()

```
OH_Drawing_FontCollection* OH_Drawing_CreateSharedFontCollection(void)
```

**Description**

Creates a shareable [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Returns the pointer to the **OH_Drawing_FontCollection** object created.|

### OH_Drawing_ClearFontCaches()

```
void OH_Drawing_ClearFontCaches(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Clears the font cache. (The font cache has a memory limit and a clearing mechanism. It occupies limited memory. You are not advised to clear it unless otherwise required.)

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|

### OH_Drawing_GetFontCollectionGlobalInstance()

```
OH_Drawing_FontCollection* OH_Drawing_GetFontCollectionGlobalInstance(void)
```

**Description**

Obtains the global [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object, which can be used to sense the theme font information. Do not release the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Returns the pointer to the global {@link OH_Drawing_FontCollection} object obtained.|
