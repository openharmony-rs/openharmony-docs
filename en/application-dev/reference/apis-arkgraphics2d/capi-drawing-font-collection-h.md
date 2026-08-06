# drawing_font_collection.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=505cdcc08414815d97fac7e5929d482f30ac5700 translatedAt=2026-07-25T01:59:38.232Z pushedAt=2026-07-25T02:25:47.435Z -->

## Overview

Defines functions related to font collections in the drawing module, which are used to manage font resources required for text typography. It supports creating independent or shareable font collection objects to meet text typography requirements in different scenarios. Through font collection objects, you can implement custom font loading, system font management, font cache cleanup, and other functions.

**File to include**: <native_drawing/drawing_font_collection.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection* OH_Drawing_CreateFontCollection(void)](#oh_drawing_createfontcollection) | Creates an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| [void OH_Drawing_DestroyFontCollection(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_destroyfontcollection) | Destroys an **OH_Drawing_FontCollection** object and reclaims the memory occupied by the object.|
| [void OH_Drawing_DisableFontCollectionFallback(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_disablefontcollectionfallback) | Disables the system fonts.|
| [void OH_Drawing_DisableFontCollectionSystemFont(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_disablefontcollectionsystemfont) | Disables the system font. After being disabled, the font collection object can only use registered custom fonts for text rendering. |
| [OH_Drawing_FontCollection* OH_Drawing_CreateSharedFontCollection(void)](#oh_drawing_createsharedfontcollection) | Creates a shareable [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| [void OH_Drawing_ClearFontCaches(OH_Drawing_FontCollection* fontCollection)](#oh_drawing_clearfontcaches) | Clears the font cache. (The font cache has a memory limit and a clearing mechanism. It occupies limited memory. You are not advised to clear it unless otherwise required.)|
| [OH_Drawing_FontCollection* OH_Drawing_GetFontCollectionGlobalInstance(void)](#oh_drawing_getfontcollectionglobalinstance) | Obtains the global font collection object [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md), which can be used to obtain theme font information. This object is prohibited from being released. |

## Function Description

### OH_Drawing_CreateFontCollection()

```c
OH_Drawing_FontCollection* OH_Drawing_CreateFontCollection(void)
```

**Description**

Creates an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Pointer to the created font collection object. The font collection pointer object created by this function can only be used by one [OH_Drawing_TypographyCreate](capi-drawing-oh-drawing-typographycreate.md) object and does not support shared use among multiple OH_Drawing_TypographyCreate objects. To share the same OH_Drawing_FontCollection among multiple OH_Drawing_TypographyCreate objects, use the [OH_Drawing_CreateSharedFontCollection](capi-drawing-font-collection-h.md#oh_drawing_createsharedfontcollection) function to create the OH_Drawing_FontCollection object. |

### OH_Drawing_DestroyFontCollection()

```c
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

```c
void OH_Drawing_DisableFontCollectionFallback(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Disables the system fonts.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Deprecated from**: 18

**Replaced by**: [OH_Drawing_DisableFontCollectionSystemFont()](#oh_drawing_disablefontcollectionsystemfont)

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|

### OH_Drawing_DisableFontCollectionSystemFont()

```c
void OH_Drawing_DisableFontCollectionSystemFont(OH_Drawing_FontCollection* fontCollection)
```

**Description**

Disables system fonts. After disabling, the font collection object can only use registered custom fonts for text rendering.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to the font collection object [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) for which system fonts are to be disabled. |

### OH_Drawing_CreateSharedFontCollection()

```c
OH_Drawing_FontCollection* OH_Drawing_CreateSharedFontCollection(void)
```

**Description**

Creates a shareable [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Pointer to the created font collection object, which can be used by multiple [OH_Drawing_TypographyCreate](capi-drawing-oh-drawing-typographycreate.md) objects. |

### OH_Drawing_ClearFontCaches()

```c
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

```c
OH_Drawing_FontCollection* OH_Drawing_GetFontCollectionGlobalInstance(void)
```

**Description**

Obtains the global font collection object [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md), which can be used to obtain theme font information. This object is prohibited from being released.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* | Pointer to the global font collection object, which can be used by multiple [OH_Drawing_TypographyCreate](capi-drawing-oh-drawing-typographycreate.md) objects and is prohibited from being released. |