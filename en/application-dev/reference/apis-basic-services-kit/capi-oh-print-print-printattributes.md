# Print_PrintAttributes
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrintAttributes
```

## Overview

Defines a struct for the print attributes.

**Since**: 13

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name                                                      | Description                  |
| ---------------------------------------------------------- | ---------------------- |
| [Print_Range](capi-oh-print-print-range.md) pageRange      | Page range.            |
| [Print_PageSize](capi-oh-print-print-pagesize.md) pageSize | Page size.        |
| [Print_Margin](capi-oh-print-print-margin.md) pageMargin   | Page margin.            |
| uint32_t copyNumber                                        | Number of copies to print.                |
| uint32_t duplexMode                                        | Duplex mode.            |
| uint32_t colorMode                                         | Color mode.            |
| bool isSequential                                          | Whether pages are printed in sequential order.<br>The value **true** indicates that pages are printed in sequential order, and **false** indicates the opposite.|
| bool isLandscape                                           | Whether pages are printed in landscape mode.<br>The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode.|
| bool hasOption                                             | Whether the printing has an option flag.<br>The value **true** indicates that the printing has an option flag, and **false** indicates the opposite.|
| char options[256]                                          | Print options.            |
