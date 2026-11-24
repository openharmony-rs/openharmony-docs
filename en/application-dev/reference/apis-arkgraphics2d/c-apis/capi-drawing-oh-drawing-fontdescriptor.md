# OH_Drawing_FontDescriptor

```c
typedef struct OH_Drawing_FontDescriptor {...} OH_Drawing_FontDescriptor
```

## Overview

This struct describes the detailed information about a system font.

<!--Device-struct OH_Drawing_FontDescriptor {...}--><!--Device-struct OH_Drawing_FontDescriptor {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

**Header file**: [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* path | File path of the system font.<br><!--Device-char* path--><!--Device-char* path-End--> |
| char* postScriptName | PostScript name that uniquely identifies the system font.<br><!--Device-char* postScriptName--><!--Device-char* postScriptName-End--> |
| char* fullName | Full name of the system font.<br><!--Device-char* fullName--><!--Device-char* fullName-End--> |
| char* fontFamily | Family of the system font.<br><!--Device-char* fontFamily--><!--Device-char* fontFamily-End--> |
| char* fontSubfamily | Subfamily of the system font.<br><!--Device-char* fontSubfamily--><!--Device-char* fontSubfamily-End--> |
| int weight | Weight of the system font.<br><!--Device-int weight--><!--Device-int weight-End--> |
| int width | Width of the system font.<br><!--Device-int width--><!--Device-int width-End--> |
| int italic | Slope of the system font.<br><!--Device-int italic--><!--Device-int italic-End--> |
| bool monoSpace | Whether the system font is monospace. The value true means the font is monospace, and false means the opposite.<br><!--Device-bool monoSpace--><!--Device-bool monoSpace-End--> |
| bool symbolic | Whether the system font supports symbols. **true** means yes; **false** otherwise.<br><!--Device-bool symbolic--><!--Device-bool symbolic-End--> |


