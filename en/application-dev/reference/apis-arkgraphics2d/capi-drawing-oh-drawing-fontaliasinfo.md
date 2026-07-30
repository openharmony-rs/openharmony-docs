# OH_Drawing_FontAliasInfo

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=26f1a11070a0259938fa2e9b40098b1fb904b6e8 translatedAt=2026-07-25T01:58:25.973Z pushedAt=2026-07-25T03:06:24.838Z -->

```
typedef struct {...} OH_Drawing_FontAliasInfo
```

## Overview

This struct describes the information about a font alias.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* familyName | Pointer to the name of a font family.|
| int weight | Font weight value. If the value is greater than 0, the font family contains only the font with the specified weight. If the value is 0, the font family contains all fonts. |