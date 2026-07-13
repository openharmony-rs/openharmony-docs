# OH_Drawing_FontFallbackInfo

```c
typedef struct OH_Drawing_FontFallbackInfo {...} OH_Drawing_FontFallbackInfo
```

## 概述

This struct describes the information about a font fallback.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* language | Pointer to the language supported by the font fallback. The language format is bcp47. |
| char* familyName | Pointer to the name of a font family. |


