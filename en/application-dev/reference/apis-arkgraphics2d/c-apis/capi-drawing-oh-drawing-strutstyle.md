# OH_Drawing_StrutStyle

```c
typedef struct OH_Drawing_StrutStyle {...} OH_Drawing_StrutStyle
```

## Overview

This struct describes a strut style. The strut style determines the line spacing, baseline alignment mode, and other properties related to the line height when drawing text.

<!--Device-typedef struct OH_Drawing_StrutStyle {...} OH_Drawing_StrutStyle--><!--Device-typedef struct OH_Drawing_StrutStyle {...} OH_Drawing_StrutStyle-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Drawing_FontWeight](capi-drawing-text-typography-h.md#oh_drawing_fontweight) weight | Font weight used for calculating the strut.<br><!--Device-OH_Drawing_FontWeight weight--><!--Device-OH_Drawing_FontWeight weight-End--> |
| [OH_Drawing_FontStyle](capi-drawing-text-typography-h.md#oh_drawing_fontstyle) style | Font style used when calculating the strut.<br><!--Device-OH_Drawing_FontStyle style--><!--Device-OH_Drawing_FontStyle style-End--> |
| double size | Size of the ascent plus descent in the logical pixels.<br><!--Device-double size--><!--Device-double size-End--> |
| double heightScale | Scale factor of the line height.<br><!--Device-double heightScale--><!--Device-double heightScale-End--> |
| bool heightOverride | Whether to enable height override. **true**: enabled; **false**: disabled.<br><!--Device-bool heightOverride--><!--Device-bool heightOverride-End--> |
| bool halfLeading | Whether to enable half leading. **true**: enabled; **false**: disabled.<br><!--Device-bool halfLeading--><!--Device-bool halfLeading-End--> |
| double leading | Custom leading to be applied to the strut.<br><!--Device-double leading--><!--Device-double leading-End--> |
| bool forceStrutHeight | Whether to forcibly use the strut height for all rows. **true** means yes; **false** otherwise.<br><!--Device-bool forceStrutHeight--><!--Device-bool forceStrutHeight-End--> |
| size_t familiesSize | Number of font families.<br><!--Device-size_t familiesSize--><!--Device-size_t familiesSize-End--> |
| char** families | Double pointer to the font families used for calculating the strut.<br><!--Device-char** families--><!--Device-char** families-End--> |


