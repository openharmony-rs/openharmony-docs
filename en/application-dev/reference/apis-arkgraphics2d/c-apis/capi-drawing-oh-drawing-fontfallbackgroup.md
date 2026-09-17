# OH_Drawing_FontFallbackGroup

```c
typedef struct OH_Drawing_FontFallbackGroup {...} OH_Drawing_FontFallbackGroup
```

## Overview

This struct describes the information about a font fallback group.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* groupName | Name of the font set corresponding to the fallback font group. If the value is empty, all fonts in the fallback font set list can be used. |
| size_t fallbackInfoSize | Number of font fallbacks. |
| [OH_Drawing_FontFallbackInfo*](capi-drawing-oh-drawing-fontfallbackinfo.md) fallbackInfoSet | List of fallback font sets. |


