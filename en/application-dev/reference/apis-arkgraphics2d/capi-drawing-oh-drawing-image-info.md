# OH_Drawing_Image_Info

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3b75f30d038321e59d140485862ef0f48205e17e translatedAt=2026-08-24T08:38:37.930Z pushedAt=2026-08-25T07:01:57.899Z -->

```c
typedef struct {...} OH_Drawing_Image_Info
```

## Overview

This struct describes the image information.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_types.h](capi-drawing-types-h.md)

## Summary

### Member Variables

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| int32_t width                                                | Width, in pixels.                                          |
| int32_t height                                               | Height, in pixels.                                          |
| [OH_Drawing_ColorFormat](capi-drawing-types-h.md#oh_drawing_colorformat) colorType | Color type.|
| [OH_Drawing_AlphaFormat](capi-drawing-types-h.md#oh_drawing_alphaformat) alphaType | Alpha type.|