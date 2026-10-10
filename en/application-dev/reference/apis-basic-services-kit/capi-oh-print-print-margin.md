# Print_Margin
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:41:06.076Z pushedAt=2026-10-10T03:41:48.346Z -->

```cpp
typedef struct {...} Print_Margin
```

## Overview

Represents the margin information of a printed page. You can set the margins in the left, top, right, and bottom directions to control the print content area. This API can be used to precisely control the distance between the content and the paper edge during printing. Proper margin settings can prevent content overflow or clipping.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name                 | Description    |
| --------------------- | -------- |
| uint32_t leftMargin   | Left margin, in millimeters. The value must be greater than **0**. |
| uint32_t topMargin    | Top margin, in millimeters. The value must be greater than **0**. |
| uint32_t rightMargin  | Right margin, in millimeters. The value must be greater than **0**. |
| uint32_t bottomMargin | Bottom margin, in millimeters. The value must be greater than **0**. |

