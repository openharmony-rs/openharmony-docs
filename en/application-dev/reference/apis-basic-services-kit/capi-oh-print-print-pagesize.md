# Print_PageSize
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=8ee0eefda2c8f7c51afc8d61427d4e7289d6c89f translatedAt=2026-11-12T03:55:27.706Z pushedAt=2026-11-12T12:09:25.671Z nl=1 -->

```cpp
typedef struct {...} Print_PageSize
```

## Overview

Represents the paper size in a print task, including key attributes such as the page ID, name, width, and height. This API can be used to specify or query paper specifications during printing configuration.

**Since**: 12

**Related module**: [Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name           | Description      |
| --------------- | ---------- |
| char *id        | Unique ID of the paper size, which is used to distinguish different paper specifications. |
| char *name      | Name of the paper size, for example, **A4** or **Letter**. |
| uint32_t width  | Paper width, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |
| uint32_t height | Paper height, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |

