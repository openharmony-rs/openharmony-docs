# OH_Drawing_RunBuffer

```c
typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer
```

## Overview

This struct describes a run, which provides storage for glyphs and positions.

<!--Device-typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer--><!--Device-typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_blob.h](capi-drawing-text-blob-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint16_t* glyphs | Storage for glyph indexes in the run.<br><!--Device-uint16_t* glyphs--><!--Device-uint16_t* glyphs-End--> |
| float* pos | Storage for glyph positions in the run.<br><!--Device-float* pos--><!--Device-float* pos-End--> |
| char* utf8text | Storage for UTF-8 encoded text units in the run.<br><!--Device-char* utf8text--><!--Device-char* utf8text-End--> |
| uint32_t* clusters | Storage for glyph clusters (index of the UTF-8 encoded text unit) in the run.<br><!--Device-uint32_t* clusters--><!--Device-uint32_t* clusters-End--> |


