# Print_PageSize
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:41:50.083Z pushedAt=2026-10-10T03:42:02.966Z -->

```cpp
typedef struct {...} Print_PageSize
```

## Overview

Represents the paper size information in a print task, including key attributes such as the paper ID, name, width, and height. This API can be used to specify or query paper specifications during printing configuration.

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

