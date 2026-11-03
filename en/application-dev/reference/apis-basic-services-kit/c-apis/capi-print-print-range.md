# Print_Range

```c
typedef struct Print_Range {...} Print_Range
```

## Overview

Represents the print range, which is used to specify the page range in a print task. You can use **startPage**<br>and **endPage** to specify consecutive pages, or use **pagesArray** and **pagesArrayLen** to specify an array of non-consecutive pages to be printed.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 13

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t startPage | Start page number for printing. The page number starts from 1. The value must be a valid page number in the document and must be less than or equal to the value of **endPage**. |
| uint32_t endPage | End page number for printing. The page number starts from 1. The value must be a valid page number in the document and must be greater than or equal to the value of **startPage**. |
| uint32_t pagesArrayLen | Length of the page array. The value must be the same as the actual number of elements in the **pagesArray**<br>array. This parameter is valid only when **pagesArray** is not **NULL**. |
| uint32_t *pagesArray | Page array. Each element in the array indicates a page to be printed. The page number starts from 1. The value must be a valid page number in the document. The array length is determined by **pagesArrayLen**. |


