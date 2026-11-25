# Print_StringList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=cfbd32eaf8f6889081f1f689234b5a5bcadff8c8 translatedAt=2026-11-23T01:15:11.633Z pushedAt=2026-11-23T10:58:23.246Z nl=1 -->

```cpp
typedef struct {...} Print_StringList
```

## Overview

Represents a string list, which is used to transfer multiple strings in the print module. This struct uses the **count** field to record the number of strings and the **list** field to point to the string array. It can be used to transfer multiple strings in batches. For details about related APIs, see [OH_Print](capi-oh-print.md).

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t count | String count, which indicates the number of elements in the **list** array. |
| `char **list` | Pointer to the string array. The number of elements in the array must be the same as the value of **count**. |


