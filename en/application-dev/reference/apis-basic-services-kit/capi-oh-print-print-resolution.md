# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:45:30.448Z pushedAt=2026-10-10T03:46:48.357Z -->

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
