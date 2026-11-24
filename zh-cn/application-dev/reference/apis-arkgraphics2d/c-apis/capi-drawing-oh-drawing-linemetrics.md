# OH_Drawing_LineMetrics

```c
typedef struct OH_Drawing_LineMetrics {...} OH_Drawing_LineMetrics
```

## 概述

文字行位置信息。

<!--Device-struct OH_Drawing_LineMetrics {...}--><!--Device-struct OH_Drawing_LineMetrics {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-arkgraphics2d-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double ascender | 文字相对于基线以上取绝对值后的高度。<br><!--Device-double ascender--><!--Device-double ascender-End--> |
| double descender | 文字相对于基线以下取绝对值后的高度。<br><!--Device-double descender--><!--Device-double descender-End--> |
| double capHeight | 大写字母的高度。<br><!--Device-double capHeight--><!--Device-double capHeight-End--> |
| double xHeight | 小写字母的高度。<br><!--Device-double xHeight--><!--Device-double xHeight-End--> |
| double width | 文字宽度。<br><!--Device-double width--><!--Device-double width-End--> |
| double height | 行高。<br><!--Device-double height--><!--Device-double height-End--> |
| double x | 文字左端到容器左端距离，左对齐为0，右对齐为容器宽度减去行文字宽度。<br><!--Device-double x--><!--Device-double x-End--> |
| double y | 文字上端到容器上端高度，第一行为0，第二行为第一行高度。<br><!--Device-double y--><!--Device-double y-End--> |
| size_t startIndex | 行起始位置字符索引。<br><!--Device-size_t startIndex--><!--Device-size_t startIndex-End--> |
| size_t endIndex | 行结束位置字符索引。<br><!--Device-size_t endIndex--><!--Device-size_t endIndex-End--> |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md) firstCharMetrics | 第一个字的度量信息。<br><!--Device-OH_Drawing_Font_Metrics firstCharMetrics--><!--Device-OH_Drawing_Font_Metrics firstCharMetrics-End--> |


