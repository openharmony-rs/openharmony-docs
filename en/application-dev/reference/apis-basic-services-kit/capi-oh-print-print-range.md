# Print_Range
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_Range
```

## Overview

Defines a struct for the range to print.

**Since**: 13

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t startPage | Start page.|
| uint32_t endPage | End page.|
| uint32_t pagesArrayLen | Length of the page array.|
| uint32_t* pagesArray | Pointer to the page array.|
