# OH_Drawing_FontConfigInfo

```c
typedef struct OH_Drawing_FontConfigInfo {...} OH_Drawing_FontConfigInfo
```

## 概述

系统字体配置信息结构体。

<!--Device-struct OH_Drawing_FontConfigInfo {...}--><!--Device-struct OH_Drawing_FontConfigInfo {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-arkgraphics2d-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t fontDirSize | 系统字体文件路径数量。<br><!--Device-size_t fontDirSize--><!--Device-size_t fontDirSize-End--> |
| size_t fontGenericInfoSize | 通用字体集列表数量。<br><!--Device-size_t fontGenericInfoSize--><!--Device-size_t fontGenericInfoSize-End--> |
| size_t fallbackGroupSize | 备用字体集数量。<br><!--Device-size_t fallbackGroupSize--><!--Device-size_t fallbackGroupSize-End--> |
| char** fontDirSet | 系统字体文件路径列表。<br><!--Device-char** fontDirSet--><!--Device-char** fontDirSet-End--> |
| [OH_Drawing_FontGenericInfo*](capi-drawing-oh-drawing-fontgenericinfo.md) fontGenericInfoSet | 通用字体集列表。<br><!--Device-OH_Drawing_FontGenericInfo* fontGenericInfoSet--><!--Device-OH_Drawing_FontGenericInfo* fontGenericInfoSet-End--> |
| [OH_Drawing_FontFallbackGroup*](capi-drawing-oh-drawing-fontfallbackgroup.md) fallbackGroupSet | 备用字体集列表。<br><!--Device-OH_Drawing_FontFallbackGroup* fallbackGroupSet--><!--Device-OH_Drawing_FontFallbackGroup* fallbackGroupSet-End--> |


