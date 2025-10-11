# drawing_text_global.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the functions related to global text information, for example, setting the high contrast mode for text rendering.

**File to include**: <native_drawing/drawing_text_global.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_TextHighContrast](#oh_drawing_texthighcontrast) | OH_Drawing_TextHighContrast | Enum of the high contrast modes for text rendering.|
| [OH_Drawing_TextUndefinedGlyphDisplay](#oh_drawing_textundefinedglyphdisplay) | OH_Drawing_TextUndefinedGlyphDisplay | Enum of the modes for displaying undefined glyphs.|

### Functions

| Name| Description|
| -- | -- |
| [void OH_Drawing_SetTextHighContrast(OH_Drawing_TextHighContrast action)](#oh_drawing_settexthighcontrast) | Sets the high contrast mode for text rendering.|
| [void OH_Drawing_SetTextUndefinedGlyphDisplay(OH_Drawing_TextUndefinedGlyphDisplay undefinedGlyphDisplay)](#oh_drawing_settextundefinedglyphdisplay) | Sets how undefined glyphs are displayed. The setting affects all subsequent text rendering.|

## Enum Description

### OH_Drawing_TextHighContrast

```
enum OH_Drawing_TextHighContrast
```

**Description**

Defines an enum of the high contrast modes for text rendering.

**Since**: 20

| Value| Description|
| -- | -- |
| TEXT_FOLLOW_SYSTEM_HIGH_CONTRAST | Follows the high contrast mode for text rendering in the system settings.|
| TEXT_APP_DISABLE_HIGH_CONTRAST | Disables the high contrast mode for text rendering in the application. This mode takes precedence over the one based on system settings.|
| TEXT_APP_ENABLE_HIGH_CONTRAST | Enables the high contrast mode for text rendering in the application. The priority of this mode is higher than the mode following the system settings.|

### OH_Drawing_TextUndefinedGlyphDisplay

```
enum OH_Drawing_TextUndefinedGlyphDisplay
```

**Description**

Defines an enum of the modes for displaying undefined glyphs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

| Value| Description|
| -- | -- |
| TEXT_NO_GLYPH_USE_DEFAULT = 0 | Uses the default glyph (which may be a blank box, space, or custom symbol) defined in the font file.|
| TEXT_NO_GLYPH_USE_TOFU = 1 | Always uses tofu blocks to represent absent glyphs.|

## Function Description

### OH_Drawing_SetTextHighContrast()

```
void OH_Drawing_SetTextHighContrast(OH_Drawing_TextHighContrast action)
```

**Description**

Sets the high contrast mode for text rendering.

The setting of this API takes effect for the entire process, and all pages in the process share the same mode.

You can call this API to set the high contrast mode, or enable or disable the high contrast mode by toggling the switch on the system settings screen. This API is used to set the high contrast mode for text rendering. The setting of this API takes precedence over the one based on system settings.

This API does not take effect for the text drawing scenario.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextHighContrast](#oh_drawing_texthighcontrast) action | High contrast mode for text rendering. The value is an enumerated value of the [OH_Drawing_TextHighContrast](#oh_drawing_texthighcontrast) type.|

### OH_Drawing_SetTextUndefinedGlyphDisplay()

```
void OH_Drawing_SetTextUndefinedGlyphDisplay(OH_Drawing_TextUndefinedGlyphDisplay undefinedGlyphDisplay)
```

**Description**

Sets how undefined glyphs are displayed. The setting affects all subsequent text rendering.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_TextUndefinedGlyphDisplay](#oh_drawing_textundefinedglyphdisplay) undefinedGlyphDisplay | Mode of displaying undefined glyphs. The value is an enumerated value of the [OH_Drawing_TextUndefinedGlyphDisplay](#oh_drawing_textundefinedglyphdisplay) type.|
