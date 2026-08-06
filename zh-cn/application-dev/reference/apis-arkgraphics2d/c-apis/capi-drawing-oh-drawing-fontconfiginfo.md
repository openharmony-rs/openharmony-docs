# OH_Drawing_FontConfigInfo

```c
typedef struct OH_Drawing_FontConfigInfo {...} OH_Drawing_FontConfigInfo
```

## 概述

This struct describes the information about a system font configuration.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t fontDirSize | Number of system font file paths. |
| size_t fontGenericInfoSize | Number of generic fonts. |
| size_t fallbackGroupSize | Number of font fallbacks. |
| char** fontDirSet | Double pointer to the system font file paths. |
| [OH_Drawing_FontGenericInfo*](capi-drawing-oh-drawing-fontgenericinfo.md) fontGenericInfoSet | Pointer to a set of generic fonts. |
| [OH_Drawing_FontFallbackGroup*](capi-drawing-oh-drawing-fontfallbackgroup.md) fallbackGroupSet | Pointer to a set of font fallbacks. |


