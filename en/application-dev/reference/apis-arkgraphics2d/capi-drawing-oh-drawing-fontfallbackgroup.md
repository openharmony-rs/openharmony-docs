# OH_Drawing_FontFallbackGroup

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=26f1a11070a0259938fa2e9b40098b1fb904b6e8 translatedAt=2026-07-25T01:58:26.227Z pushedAt=2026-07-25T03:16:19.443Z -->

```
typedef struct {...} OH_Drawing_FontFallbackGroup
```

## Overview

This struct describes the information about a font fallback group.

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Total

### Member Variables

| Name                                        | Description                                                        |
| -------------------------------------------- | ------------------------------------------------------------ |
| char* groupName                              | Name of the font set corresponding to the fallback font group. If the value is empty, all fonts in the fallback font set list can be used. |
| size_t fallbackInfoSize                      | Number of font fallbacks.                                            |
| [OH_Drawing_FontFallbackInfo](capi-drawing-oh-drawing-fontfallbackinfo.md)* fallbackInfoSet | List of fallback font sets.                                         |