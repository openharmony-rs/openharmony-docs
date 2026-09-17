# Print_Range

```c
typedef struct Print_Range {...} Print_Range
```

## Overview

Defines a struct for the page range to print.

**Since**: 13

**Related module**: [Print](capi-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t startPage | Start page. |
| uint32_t endPage | End page. |
| uint32_t pagesArrayLen | Length of the page array. |
| uint32_t *pagesArray | Page array. |


