# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=aba42e15abed86996b578549f00ed4ce1a370af8 translatedAt=2026-09-01T03:11:06.228Z pushedAt=2026-09-03T11:52:18.368Z -->

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
