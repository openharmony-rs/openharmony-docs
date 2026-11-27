# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:15:01.621Z pushedAt=2026-11-23T10:58:19.247Z nl=1 -->

```cpp
typedef struct {...} Print_Resolution
```

## Overview

Represents the printing resolution, in dpi. This API can be used to control the fineness and quality of the print output.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t horizontalDpi | Horizontal print resolution, in dpi. |
| uint32_t verticalDpi | Vertical print resolution, in dpi. |
