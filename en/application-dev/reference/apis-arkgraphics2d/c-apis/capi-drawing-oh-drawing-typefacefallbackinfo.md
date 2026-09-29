# OH_Drawing_TypefaceFallbackInfo

```c
typedef struct OH_Drawing_TypefaceFallbackInfo {...} OH_Drawing_TypefaceFallbackInfo
```

## Overview

Defines the typeface fallback info structure for a run of glyphs that share the same fallback typeface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.0.1

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_font.h](capi-drawing-font-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_Drawing_Typeface *typeface | Pointer to the matched typeface.<br>**Since**: 26.0.1 |
| uint16_t *glyphIds | Pointer to the glyph ID array.<br>**Since**: 26.0.1 |
| uint32_t glyphCount | Number of glyph IDs in the glyphIds array.<br>**Since**: 26.0.1 |


