# OH_Drawing_TypefaceFallbackInfo
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=29d41186dac135b3ba0b2c25ccc33837bb3c597b translatedAt=2026-11-03T13:35:03.568Z pushedAt=2026-11-04T06:31:54.225Z nl=1 -->

```c
typedef struct {...} OH_Drawing_TypefaceFallbackInfo
```

## Overview

Defines the structure for font fallback information, which contains an array of glyphs that use the same fallback font.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since:** 26.0.1

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_font.h](capi-drawing-font-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) *typeface | Pointer to the matched font object.<br>**Since:** 26.0.1 |
| uint16_t *glyphIds | Pointer to the glyph ID array.<br>**Since:** 26.0.1 |
| uint32_t glyphCount | Size of the glyph ID array glyphIds.<br>**Since:** 26.0.1 |


