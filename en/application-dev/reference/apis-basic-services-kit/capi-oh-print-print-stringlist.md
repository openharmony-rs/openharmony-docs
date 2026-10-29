# Print_StringList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:46:07.892Z pushedAt=2026-10-10T03:47:34.039Z -->

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


