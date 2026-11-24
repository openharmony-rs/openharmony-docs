# OH_Drawing_Font_Metrics

```c
typedef struct OH_Drawing_Font_Metrics {...} OH_Drawing_Font_Metrics
```

## Overview

This struct describes the measurement information about a font.

<!--Device-struct OH_Drawing_Font_Metrics {...}--><!--Device-struct OH_Drawing_Font_Metrics {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_font.h](capi-drawing-font-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t flags | Measurement information that is valid.<br>**Since**: 12<br><!--Device-uint32_t flags--><!--Device-uint32_t flags-End--> |
| float top | Maximum distance from the baseline to the highest coordinate of a character.<br>**Since**: 12<br><!--Device-float top--><!--Device-float top-End--> |
| float ascent | Recommended distance from the baseline to the highest coordinate of a character.<br>**Since**: 12<br><!--Device-float ascent--><!--Device-float ascent-End--> |
| float descent | Recommended distance from the baseline to the lowest coordinate of a character.<br>**Since**: 12<br><!--Device-float descent--><!--Device-float descent-End--> |
| float bottom | Maximum distance from the baseline to the lowest coordinate of a character.<br>**Since**: 12<br><!--Device-float bottom--><!--Device-float bottom-End--> |
| float leading | Gap between rows.<br>**Since**: 12<br><!--Device-float leading--><!--Device-float leading-End--> |
| float avgCharWidth | Average character width, or zero if unknown.<br>**Since**: 12<br><!--Device-float avgCharWidth--><!--Device-float avgCharWidth-End--> |
| float maxCharWidth | Maximum character width, or zero if unknown.<br>**Since**: 12<br><!--Device-float maxCharWidth--><!--Device-float maxCharWidth-End--> |
| float xMin | Maximum distance to the leftmost of the font bounding box. Generally, the value is a negative value. Variable fonts are not recommended.<br>**Since**: 12<br><!--Device-float xMin--><!--Device-float xMin-End--> |
| float xMax | Maximum distance to the rightmost of the font bounding box. Generally, the value is a negative value. Variable fonts are not recommended.<br>**Since**: 12<br><!--Device-float xMax--><!--Device-float xMax-End--> |
| float xHeight | Height of a lowercase letter, or zero if unknown. Generally, the value is a negative value.<br>**Since**: 12<br><!--Device-float xHeight--><!--Device-float xHeight-End--> |
| float capHeight | Height of an uppercase letter, or zero if unknown. Generally, the value is a negative value.<br>**Since**: 12<br><!--Device-float capHeight--><!--Device-float capHeight-End--> |
| float underlineThickness | Thickness of the underline.<br>**Since**: 12<br><!--Device-float underlineThickness--><!--Device-float underlineThickness-End--> |
| float underlinePosition | Position of the underline, that is, vertical distance from the baseline to the top of the underline. Generally, the value is a positive value.<br>**Since**: 12<br><!--Device-float underlinePosition--><!--Device-float underlinePosition-End--> |
| float strikeoutThickness | Thickness of the strikethrough.<br>**Since**: 12<br><!--Device-float strikeoutThickness--><!--Device-float strikeoutThickness-End--> |
| float strikeoutPosition | Position of the strikethrough, that is, vertical distance from the baseline to the bottom of the strikethrough. Generally, the value is a negative value.<br>**Since**: 12<br><!--Device-float strikeoutPosition--><!--Device-float strikeoutPosition-End--> |


