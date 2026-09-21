# OH_Drawing_FontAliasInfo

```c
typedef struct OH_Drawing_FontAliasInfo {...} OH_Drawing_FontAliasInfo
```

## Overview

This struct describes the information about a font alias.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* familyName | Pointer to the name of a font family. |
| int weight | Font weight value. If the value is greater than 0, the font family contains only the font with the specified weight. If the value is 0, the font family contains all fonts. |


