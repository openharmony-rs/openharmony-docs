# OH_Drawing_RunBuffer

```c
typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer
```

## 概述

结构体用于描述一块内存，该内存用于存储文字和位置信息。

<!--Device-typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer--><!--Device-typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**相关模块：** [Drawing](capi-arkgraphics2d-drawing.md)

**所在头文件：** [drawing_text_blob.h](capi-drawing-text-blob-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t* glyphs | 存储字形索引。<br><!--Device-uint16_t* glyphs--><!--Device-uint16_t* glyphs-End--> |
| float* pos | 存储文字的位置。单位为物理像素px。<br><!--Device-float* pos--><!--Device-float* pos-End--> |
| char* utf8text | 存储文字UTF-8编码。<br><!--Device-char* utf8text--><!--Device-char* utf8text-End--> |
| uint32_t* clusters | 存储文字簇UTF-8编码（簇指的是集合）。<br><!--Device-uint32_t* clusters--><!--Device-uint32_t* clusters-End--> |


