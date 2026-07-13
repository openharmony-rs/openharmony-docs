# OH_Drawing_FontDescriptor

```c
typedef struct OH_Drawing_FontDescriptor {...} OH_Drawing_FontDescriptor
```

## 概述

This struct describes the detailed information about a system font.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* path | File path of the system font. |
| char* postScriptName | PostScript name that uniquely identifies the system font. |
| char* fullName | Full name of the system font. |
| char* fontFamily | Family of the system font. |
| char* fontSubfamily | Subfamily of the system font. |
| int weight | Weight of the system font. |
| int width | Width of the system font. |
| int italic | Slope of the system font. |
| bool monoSpace | Whether the system font is monospaced. **true** means yes; **false** otherwise. |
| bool symbolic | Whether the system font supports symbols. **true** means yes; **false** otherwise. |


