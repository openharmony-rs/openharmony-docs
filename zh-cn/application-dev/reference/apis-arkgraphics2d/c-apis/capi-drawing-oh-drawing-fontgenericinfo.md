# OH_Drawing_FontGenericInfo

```c
typedef struct OH_Drawing_FontGenericInfo {...} OH_Drawing_FontGenericInfo
```

## 概述

This struct describes the information about generic fonts supported by the system.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* familyName | Pointer to the name of a font family. |
| size_t aliasInfoSize | Number of font aliases. |
| size_t adjustInfoSize | Number of font weight mappings. |
| [OH_Drawing_FontAliasInfo*](capi-drawing-oh-drawing-fontaliasinfo.md) aliasInfoSet | Pointer to a set of font aliases. |
| [OH_Drawing_FontAdjustInfo*](capi-drawing-oh-drawing-fontadjustinfo.md) adjustInfoSet | Pointer to a set of font weight mappings. |


