# OH_Drawing_LineMetrics
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

文字行位置信息。

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| double ascender                                              | 文字相对于基线以上的高度。                                   |
| double descender                                             | 文字相对于基线以下的高度。                                   |
| double capHeight                                             | 大写字母的高度。                                             |
| double xHeight                                               | 小写字母的高度。                                             |
| double width                                                 | 文字宽度。                                                   |
| double height                                                | 行高。                                                       |
| double x                                                     | 文字左端到容器左端距离，左对齐为0，右对齐为容器宽度减去行文字宽度。 |
| double y                                                     | 文字上端到容器上端高度，第一行为0，第二行为第一行高度。      |
| size_t startIndex                                            | 行起始位置字符索引。                                         |
| size_t endIndex                                              | 行结束位置字符索引。                                         |
| [OH_Drawing_Font_Metrics](capi-drawing-oh-drawing-font-metrics.md) firstCharMetrics | 第一个字的度量信息。                                         |

