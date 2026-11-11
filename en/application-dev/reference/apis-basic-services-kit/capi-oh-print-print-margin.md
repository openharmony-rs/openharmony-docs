# Print_Margin
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:55:46.671Z pushedAt=2026-11-10T05:58:36.222Z nl=1 -->

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

