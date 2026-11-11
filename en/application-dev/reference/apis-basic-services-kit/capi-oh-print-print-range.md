# Print_Range
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:57:43.167Z pushedAt=2026-11-10T06:00:15.436Z nl=1 -->

```cpp
typedef struct {...} Print_Range
```

## Overview

Represents the print range, which is used to specify the page range in a print task. You can use startPage and endPage to specify consecutive pages, or use pagesArray and pagesArrayLen to specify an array of non-consecutive pages to be printed.

**Since**: 13

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name                  | Description            |
| ---------------------- | ---------------- |
| uint32_t startPage     | Start page number for printing. The page number starts from 1. The value must be a valid page number in the document and must be less than or equal to the value of **endPage**.     |
| uint32_t endPage       | End page number for printing. The page number starts from 1. The value must be a valid page number in the document and must be greater than or equal to the value of **startPage**.     |
| uint32_t pagesArrayLen | Length of the page array. The value must be the same as the actual number of elements in **pagesArray**. This parameter is valid only when **pagesArray** is not null. |
| uint32_t* pagesArray   | Page array. Each element in the array indicates a page to be printed. The page number starts from 1. The value must be a valid page number in the document. The array length is determined by **pagesArrayLen**. |

