# OH_Drawing_RectStyle_Info

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3b75f30d038321e59d140485862ef0f48205e17e translatedAt=2026-08-24T08:40:41.347Z pushedAt=2026-08-25T07:05:17.871Z -->

```c
typedef struct {...} OH_Drawing_RectStyle_Info
```

## Overview

This struct describes the style of a rectangle.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_types.h](capi-drawing-types-h.md)

## Summary

### Member Variables

| Name                    | Description              |
| ------------------------ | ------------------ |
| uint32_t color           | Color of the rectangle.    |
| double leftTopRadius     | Left top radius of the rectangle.|
| double rightTopRadius    | Right top radius of the rectangle.|
| double rightBottomRadius | Right bottom radius of the rectangle.|
| double leftBottomRadius  | Left bottom radius of the rectangle.|