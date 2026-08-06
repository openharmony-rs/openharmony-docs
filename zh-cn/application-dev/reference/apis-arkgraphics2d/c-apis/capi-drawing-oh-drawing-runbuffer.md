# OH_Drawing_RunBuffer

```c
typedef struct OH_Drawing_RunBuffer {...} OH_Drawing_RunBuffer
```

## 概述

This struct describes a run, which provides storage for glyphs and positions.

**起始版本：** 11

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_blob.h](capi-drawing-text-blob-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint16_t* glyphs | Storage for glyph indexes in the run. |
| float* pos | Storage for glyph positions in the run. |
| char* utf8text | Storage for UTF-8 encoded text units in the run. |
| uint32_t* clusters | Storage for glyph clusters (index of the UTF-8 encoded text unit) in the run. |


