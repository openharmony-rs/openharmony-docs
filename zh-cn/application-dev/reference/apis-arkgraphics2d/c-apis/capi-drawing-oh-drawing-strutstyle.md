# OH_Drawing_StrutStyle

```c
typedef struct OH_Drawing_StrutStyle {...} OH_Drawing_StrutStyle
```

## 概述

This struct describes a strut style. The strut style determines the line spacing, baseline alignment mode,and other properties related to the line height when drawing text.

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_FontWeight](capi-drawing-text-typography-h.md#oh_drawing_fontweight) weight | Font weight used for calculating the strut. |
| [OH_Drawing_FontStyle](capi-drawing-text-typography-h.md#oh_drawing_fontstyle) style | Font style used for calculating the strut. |
| double size | Size of the ascent plus descent in the logical pixels. |
| double heightScale | Scale factor of the line height. |
| bool heightOverride | Whether to enable height override. **true**: enabled; **false**: disabled. |
| bool halfLeading | Whether to enable half leading. **true**: enabled; **false**: disabled. |
| double leading | Custom leading to be applied to the strut. |
| bool forceStrutHeight | Whether to forcibly use the strut height for all rows. **true** means yes; **false** otherwise. |
| size_t familiesSize | Number of font families. |
| char** families | Double pointer to the font families used for calculating the strut. |


