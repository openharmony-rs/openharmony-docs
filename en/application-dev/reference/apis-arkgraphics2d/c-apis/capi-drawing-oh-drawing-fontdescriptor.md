# OH_Drawing_FontDescriptor

```c
typedef struct OH_Drawing_FontDescriptor {...} OH_Drawing_FontDescriptor
```

## Overview

This struct describes the detailed information about a system font.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* path | File path of the system font. |
| char* postScriptName | PostScript name that uniquely identifies the system font. |
| char* fullName | Full name of the system font. |
| char* fontFamily | Family of the system font. |
| char* fontSubfamily | Subfamily of the system font. |
| int weight | Weight of the system font. |
| int width | Width of the system font. |
| int italic | Slope of the system font. |
| bool monoSpace | Whether the system font is monospace. The value true means the font is monospace, and false means the opposite. |
| bool symbolic | Whether the system font supports symbols. **true** means yes; **false** otherwise. |


