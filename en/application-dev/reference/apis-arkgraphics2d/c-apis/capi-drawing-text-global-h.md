# drawing_text_global.h

## Overview

Provides APIs for global text information, such as setting the text rendering high contrast mode and the presentation mode of undefined glyphs.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_TextHighContrast](#oh_drawing_texthighcontrast) | OH_Drawing_TextHighContrast | Defines an enum of the high contrast modes for text rendering. |
| [OH_Drawing_TextUndefinedGlyphDisplay](#oh_drawing_textundefinedglyphdisplay) | OH_Drawing_TextUndefinedGlyphDisplay | Defines an enum of the modes for displaying undefined glyphs. |

### Function

| Name | Description |
| -- | -- |
| [void OH_Drawing_SetTextHighContrast(OH_Drawing_TextHighContrast action)](#oh_drawing_settexthighcontrast) | Sets the high contrast mode for text rendering. <br>The setting of this API takes effect for the entire process, and all pages in the process share the same mode. <br>The text rendering high contrast mode can be set by calling this API, or enabled/disabled through the high contrast text configuration switch in the system settings screen. The text rendering high contrast mode set by this API takes precedence over the system settings. <br>This API does not take effect for the text drawing scenario. |
| [void OH_Drawing_SetTextUndefinedGlyphDisplay(OH_Drawing_TextUndefinedGlyphDisplay undefinedGlyphDisplay)](#oh_drawing_settextundefinedglyphdisplay) | Sets the presentation mode of undefined glyphs. After this API is called, it affects all subsequently rendered text in the current process. |

## Enum type description

### OH_Drawing_TextHighContrast

```c
enum OH_Drawing_TextHighContrast
```

**Description**

Defines an enum of the high contrast modes for text rendering.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEXT_FOLLOW_SYSTEM_HIGH_CONTRAST | Follows the high contrast mode for text rendering in the system settings. |
| TEXT_APP_DISABLE_HIGH_CONTRAST | Disables the app's text rendering high contrast configuration. The priority of this mode is higher than the high contrast text configuration in system settings. |
| TEXT_APP_ENABLE_HIGH_CONTRAST | Enables the app's text rendering high contrast configuration. The priority of this mode is higher than the high contrast text configuration in system settings. |

### OH_Drawing_TextUndefinedGlyphDisplay

```c
enum OH_Drawing_TextUndefinedGlyphDisplay
```

**Description**

Defines an enum of the modes for displaying undefined glyphs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEXT_NO_GLYPH_USE_DEFAULT = 0 | Uses the default glyph (which may be a blank box, space, or custom symbol) defined in the font file. |
| TEXT_NO_GLYPH_USE_TOFU = 1 | Always uses tofu blocks to represent absent glyphs. |


## Function description

### OH_Drawing_SetTextHighContrast()

```c
void OH_Drawing_SetTextHighContrast(OH_Drawing_TextHighContrast action)
```

**Description**

Sets the high contrast mode for text rendering. <br>The setting of this API takes effect for the entire process, and all pages in the process share the same mode. <br>The text rendering high contrast mode can be set by calling this API, or enabled/disabled through the high contrast text configuration switch in the system settings screen. The text rendering high contrast mode set by this API takes precedence over the system settings. <br>This API does not take effect for the text drawing scenario.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextHighContrast](capi-drawing-text-global-h.md#oh_drawing_texthighcontrast) action | High contrast mode for text rendering. The value is an enumerated value of the [OH_Drawing_TextHighContrast](capi-drawing-text-global-h.md#oh_drawing_texthighcontrast) type. |

### OH_Drawing_SetTextUndefinedGlyphDisplay()

```c
void OH_Drawing_SetTextUndefinedGlyphDisplay(OH_Drawing_TextUndefinedGlyphDisplay undefinedGlyphDisplay)
```

**Description**

Sets the presentation mode of undefined glyphs. After this API is called, it affects all subsequently rendered text in the current process.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_TextUndefinedGlyphDisplay](capi-drawing-text-global-h.md#oh_drawing_textundefinedglyphdisplay) undefinedGlyphDisplay | Mode of displaying undefined glyphs. The value is an enumerated value of the [OH_Drawing_TextUndefinedGlyphDisplay](capi-drawing-text-global-h.md#oh_drawing_textundefinedglyphdisplay) type. |


