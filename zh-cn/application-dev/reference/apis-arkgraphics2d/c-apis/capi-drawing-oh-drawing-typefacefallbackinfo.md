# OH_Drawing_TypefaceFallbackInfo

```c
typedef struct OH_Drawing_TypefaceFallbackInfo {...} OH_Drawing_TypefaceFallbackInfo
```

## 概述

定义字体回退信息结构体，包含一组使用相同回退字体的字形数组。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 26.0.1

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_font.h](capi-drawing-font-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_Drawing_Typeface *typeface | 指向匹配到的字体对象的指针。<br>**起始版本：** 26.0.1 |
| uint16_t *glyphIds | 指向字形ID数组的指针。<br>**起始版本：** 26.0.1 |
| uint32_t glyphCount | 字形ID数组glyphIds的大小。<br>**起始版本：** 26.0.1 |


