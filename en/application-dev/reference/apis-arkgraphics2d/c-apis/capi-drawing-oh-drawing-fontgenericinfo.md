# OH_Drawing_FontGenericInfo

```c
typedef struct OH_Drawing_FontGenericInfo {...} OH_Drawing_FontGenericInfo
```

## Overview

This struct describes the information about generic fonts supported by the system.

<!--Device-struct OH_Drawing_FontGenericInfo {...}--><!--Device-struct OH_Drawing_FontGenericInfo {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* familyName | Pointer to the name of a font family.<br><!--Device-char* familyName--><!--Device-char* familyName-End--> |
| size_t aliasInfoSize | Number of font aliases.<br><!--Device-size_t aliasInfoSize--><!--Device-size_t aliasInfoSize-End--> |
| size_t adjustInfoSize | Number of font weight mappings.<br><!--Device-size_t adjustInfoSize--><!--Device-size_t adjustInfoSize-End--> |
| [OH_Drawing_FontAliasInfo*](capi-drawing-oh-drawing-fontaliasinfo.md) aliasInfoSet | Pointer to a set of font aliases.<br><!--Device-OH_Drawing_FontAliasInfo* aliasInfoSet--><!--Device-OH_Drawing_FontAliasInfo* aliasInfoSet-End--> |
| [OH_Drawing_FontAdjustInfo*](capi-drawing-oh-drawing-fontadjustinfo.md) adjustInfoSet | Pointer to a set of font weight mappings.<br><!--Device-OH_Drawing_FontAdjustInfo* adjustInfoSet--><!--Device-OH_Drawing_FontAdjustInfo* adjustInfoSet-End--> |


