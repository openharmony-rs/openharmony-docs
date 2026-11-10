# Print_PageSize
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:56:12.604Z pushedAt=2026-11-10T05:58:44.149Z nl=1 -->

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
| char *id | Unique ID of the paper size, which is used to distinguish different paper specifications. |
| char *name      | Name of the paper size, for example, **A4** or **Letter**. |
| uint32_t width  | Paper width, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |
| uint32_t height | Paper height, in mils (1 mil = 1/1000 inch). The value must be greater than **0**. |

