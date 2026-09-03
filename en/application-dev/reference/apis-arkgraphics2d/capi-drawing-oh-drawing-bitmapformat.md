# OH_Drawing_BitmapFormat

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3b75f30d038321e59d140485862ef0f48205e17e translatedAt=2026-08-24T08:36:42.590Z pushedAt=2026-08-25T06:58:13.720Z -->

```c
typedef struct {...} OH_Drawing_BitmapFormat
```

## Overview

This struct describes the pixel format of a bitmap, including the color type and alpha type.

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_bitmap.h](capi-drawing-bitmap-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| OH_Drawing_ColorFormat colorFormat | Storage format of bitmap pixels.|
| OH_Drawing_AlphaFormat alphaFormat | Alpha format of bitmap pixels.|