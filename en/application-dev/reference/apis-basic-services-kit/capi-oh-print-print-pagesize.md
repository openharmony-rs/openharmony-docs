# Print_PageSize
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:09:30.443Z pushedAt=2026-11-23T10:55:45.063Z nl=1 -->

```cpp
typedef struct {...} Print_PageSize
```

## Overview

Represents the paper size in a print task, including key attributes such as the page ID, name, width, and height. This API can be used to specify or query paper specifications during printing configuration.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name           | Description      |
| --------------- | ---------- |
| char *id        | Unique ID of the paper size, which is used to distinguish different paper specifications. |
| char *name      | Name of the paper size, for example, **A4** or **Letter**. |
| uint32_t width  | Paper width, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |
| uint32_t height | Paper height, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |

