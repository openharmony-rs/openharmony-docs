# OH_Drawing_LineMetrics

```c
typedef struct OH_Drawing_LineMetrics {...} OH_Drawing_LineMetrics
```

## Overview

This struct describes the measurement information about a line of text.

<!--Device-struct OH_Drawing_LineMetrics {...}--><!--Device-struct OH_Drawing_LineMetrics {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double ascender | Height of a character above the baseline, after taking the absolute value.<br><!--Device-double ascender--><!--Device-double ascender-End--> |
| double descender | Height of a character below the baseline, after taking the absolute value.<br><!--Device-double descender--><!--Device-double descender-End--> |
| double capHeight | Height of an uppercase letter above the baseline.<br><!--Device-double capHeight--><!--Device-double capHeight-End--> |
| double xHeight | Height of a lowercase letter, specifically the lowercase x, not including ascenders and descenders.<br><!--Device-double xHeight--><!--Device-double xHeight-End--> |
| double width | Horizontal space taken up by a character.<br><!--Device-double width--><!--Device-double width-End--> |
| double height | Line height.<br><!--Device-double height--><!--Device-double height-End--> |
| double x | Distance from the left edge of the leftmost character to the left edge of the container. For left alignment, the value is 0. For right alignment, the value is the container width minus the text width.<br><!--Device-double x--><!--Device-double x-End--> |
| double y | Height from the top edge of the character to the top of the container. The first line is 0, and the second line is the height of the first line.<br><!--Device-double y--><!--Device-double y-End--> |
| size_t startIndex | Index of the first character in the line.<br><!--Device-size_t startIndex--><!--Device-size_t startIndex-End--> |
| size_t endIndex | Index of the last character in the line.<br><!--Device-size_t endIndex--><!--Device-size_t endIndex-End--> |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md) firstCharMetrics | Measurement information of the first character.<br><!--Device-OH_Drawing_Font_Metrics firstCharMetrics--><!--Device-OH_Drawing_Font_Metrics firstCharMetrics-End--> |


