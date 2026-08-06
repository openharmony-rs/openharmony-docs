# OH_Drawing_FontFallbackGroup

```c
typedef struct OH_Drawing_FontFallbackGroup {...} OH_Drawing_FontFallbackGroup
```

## 概述

This struct describes the information about a font fallback group.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* groupName | Pointer to the name of the group corresponding to the font fallback group. If null is passed in, all fonts inthe font fallback group can be used. |
| size_t fallbackInfoSize | Number of font fallbacks. |
| [OH_Drawing_FontFallbackInfo*](capi-drawing-oh-drawing-fontfallbackinfo.md) fallbackInfoSet | Pointer to the set of font fallbacks. |


