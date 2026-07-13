# OH_Drawing_LineMetrics

```c
typedef struct OH_Drawing_LineMetrics {...} OH_Drawing_LineMetrics
```

## 概述

This struct describes the measurement information about a line of text.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double ascender | Height of a character above the baseline, after taking the absolute value. |
| double descender | Height of a character below the baseline, after taking the absolute value. |
| double capHeight | Height of an uppercase letter above the baseline. |
| double xHeight | Height of a lowercase letter, specifically the lowercase x, not including ascenders and descenders. |
| double width | Horizontal space taken up by a character. |
| double height | Line height. |
| double x | Distance from the left edge of the leftmost character to the left edge of the container. For left alignment, thevalue is 0. For right alignment, the value is the container width minus the text width. |
| double y | Height from the top edge of the character to the top of the container. The first line is 0, and the second lineis the height of the first line. |
| size_t startIndex | Index of the first character in the line. |
| size_t endIndex | Index of the last character in the line. |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md) firstCharMetrics | Measurement information of the first character. |


