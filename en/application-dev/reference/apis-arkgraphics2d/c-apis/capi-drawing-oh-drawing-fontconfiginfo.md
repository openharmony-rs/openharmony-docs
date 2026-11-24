# OH_Drawing_FontConfigInfo

```c
typedef struct OH_Drawing_FontConfigInfo {...} OH_Drawing_FontConfigInfo
```

## Overview

This struct describes the information about a system font configuration.

<!--Device-struct OH_Drawing_FontConfigInfo {...}--><!--Device-struct OH_Drawing_FontConfigInfo {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t fontDirSize | Number of system font file paths.<br><!--Device-size_t fontDirSize--><!--Device-size_t fontDirSize-End--> |
| size_t fontGenericInfoSize | Number of generic fonts.<br><!--Device-size_t fontGenericInfoSize--><!--Device-size_t fontGenericInfoSize-End--> |
| size_t fallbackGroupSize | Number of font fallbacks.<br><!--Device-size_t fallbackGroupSize--><!--Device-size_t fallbackGroupSize-End--> |
| char** fontDirSet | Double pointer to the system font file paths.<br><!--Device-char** fontDirSet--><!--Device-char** fontDirSet-End--> |
| [OH_Drawing_FontGenericInfo*](capi-drawing-oh-drawing-fontgenericinfo.md) fontGenericInfoSet | Pointer to a set of generic fonts.<br><!--Device-OH_Drawing_FontGenericInfo* fontGenericInfoSet--><!--Device-OH_Drawing_FontGenericInfo* fontGenericInfoSet-End--> |
| [OH_Drawing_FontFallbackGroup*](capi-drawing-oh-drawing-fontfallbackgroup.md) fallbackGroupSet | Pointer to a set of font fallbacks.<br><!--Device-OH_Drawing_FontFallbackGroup* fallbackGroupSet--><!--Device-OH_Drawing_FontFallbackGroup* fallbackGroupSet-End--> |


