# OH_Drawing_FontAliasInfo

```c
typedef struct OH_Drawing_FontAliasInfo {...} OH_Drawing_FontAliasInfo
```

## 概述

This struct describes the information about a font alias.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* familyName | Pointer to the name of a font family. |
| int weight | Font weight. If the value is greater than 0, only the fonts with the specified weight in the font family arecontained. If the value is 0, all the fonts in the font family are contained. |


