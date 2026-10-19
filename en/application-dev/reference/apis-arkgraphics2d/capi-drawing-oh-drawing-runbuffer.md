# OH_Drawing_RunBuffer

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=e8888f7e3ce1e37673dc5a840869f0dbe280bd6a translatedAt=2026-08-24T08:41:07.169Z pushedAt=2026-08-25T07:14:28.544Z -->

```c
typedef struct {...} OH_Drawing_RunBuffer
```

## Overview

This struct describes a run, which provides storage for glyphs and positions.

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_blob.h](capi-drawing-text-blob-h.md)

## Summary

### Member Variables

| Name              | Description                                 |
| ------------------ | ------------------------------------- |
| uint16_t* glyphs   | Stores glyph indices.                        |
| float* pos         | Stores the position of the text. The unit is physical pixels (px).                      |
| char* utf8text     | Storage for UTF-8 encoded text units in the run.                  |
| uint32_t* clusters | Storage for glyph clusters (index of the UTF-8 encoded text unit) in the run.|