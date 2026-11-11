# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:57:42.834Z pushedAt=2026-11-10T06:00:22.092Z nl=1 -->

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
