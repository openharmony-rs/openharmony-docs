# OH_Drawing_FontFallbackGroup
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=0876b7ba2fa1777332890da7f5059310feded633 translatedAt=2026-11-04T10:27:35.858Z pushedAt=2026-11-04T10:31:14.658Z nl=2 -->

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
| char* groupName                              | Name of the font group corresponding to the fallback font group. If the value is empty, all fonts in the fallback font group list can be used. |
| size_t fallbackInfoSize                      | Number of font fallbacks.                                            |
| [OH_Drawing_FontFallbackInfo](capi-drawing-oh-drawing-fontfallbackinfo.md)* fallbackInfoSet | List of fallback font groups.                                         |

