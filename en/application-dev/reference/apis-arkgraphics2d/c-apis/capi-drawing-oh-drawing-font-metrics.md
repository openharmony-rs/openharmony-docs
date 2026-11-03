# OH_Drawing_Font_Metrics

```c
struct OH_Drawing_Font_Metrics {...}
```

## Overview

This struct describes the measurement information about a font.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-others-drawing.md)

**Header file**: [drawing_font.h](capi-drawing-font-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t flags | Measurement information that is valid.<br>**Since**: 12 |
| float top | Maximum distance from the baseline to the highest coordinate of a character.<br>**Since**: 12 |
| float ascent | Recommended distance from the baseline to the highest coordinate of a character.<br>**Since**: 12 |
| float descent | Recommended distance from the baseline to the lowest coordinate of a character.<br>**Since**: 12 |
| float bottom | Maximum distance from the baseline to the lowest coordinate of a character.<br>**Since**: 12 |
| float leading | Gap between rows.<br>**Since**: 12 |
| float avgCharWidth | Average character width, or zero if unknown.<br>**Since**: 12 |
| float maxCharWidth | Maximum character width, or zero if unknown.<br>**Since**: 12 |
| float xMin | Maximum distance to the leftmost of the font bounding box. Generally, the value is a negative value. Variable fonts are not recommended.<br>**Since**: 12 |
| float xMax | Maximum distance to the rightmost of the font bounding box. Generally, the value is a negative value. Variable fonts are not recommended.<br>**Since**: 12 |
| float xHeight | Height of a lowercase letter, or zero if unknown. Generally, the value is a negative value.<br>**Since**: 12 |
| float capHeight | Height of an uppercase letter, or zero if unknown. Generally, the value is a negative value.<br>**Since**: 12 |
| float underlineThickness | Thickness of the underline.<br>**Since**: 12 |
| float underlinePosition | Position of the underline, that is, vertical distance from the baseline to the top of the underline. Generally, the value is a positive value.<br>**Since**: 12 |
| float strikeoutThickness | Thickness of the strikethrough.<br>**Since**: 12 |
| float strikeoutPosition | Position of the strikethrough, that is, vertical distance from the baseline to the bottom of the strikethrough. Generally, the value is a negative value.<br>**Since**: 12 |


