# OH_Drawing_FontFallbackGroup

```c
typedef struct OH_Drawing_FontFallbackGroup {...} OH_Drawing_FontFallbackGroup
```

## 概述

备用字体集信息结构体。

<!--Device-struct OH_Drawing_FontFallbackGroup {...}--><!--Device-struct OH_Drawing_FontFallbackGroup {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-arkgraphics2d-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* groupName | 备用字体集所对应的字体集名称，如果值为空，表示可以使用备用字体集列表中所有的字体。<br><!--Device-char* groupName--><!--Device-char* groupName-End--> |
| size_t fallbackInfoSize | 备用字体集数量。<br><!--Device-size_t fallbackInfoSize--><!--Device-size_t fallbackInfoSize-End--> |
| [OH_Drawing_FontFallbackInfo*](capi-drawing-oh-drawing-fontfallbackinfo.md) fallbackInfoSet | 备用字体集列表。<br><!--Device-OH_Drawing_FontFallbackInfo* fallbackInfoSet--><!--Device-OH_Drawing_FontFallbackInfo* fallbackInfoSet-End--> |


