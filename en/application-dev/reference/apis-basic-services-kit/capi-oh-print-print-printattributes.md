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

| Name| Description|
| -- | -- |
| [Print_Range](capi-oh-print-print-range.md) pageRange | Page range.|
| [Print_PageSize](capi-oh-print-print-pagesize.md) pageSize | Page size.|
| [Print_Margin](capi-oh-print-print-margin.md) pageMargin | Page margin.|
| uint32_t copyNumber | Number of copies to print.|
| uint32_t duplexMode | Duplex mode.|
| uint32_t colorMode | Color mode.|
| bool isSequential | Whether to print in a sequential manner. The value **true** indicates that the printing is in a sequential manner, and **false** indicates the opposite.|
| bool isLandscape | Whether to print in the landscape mode. The value **true** indicates that the printing is in the landscape mode, and **false** indicates the opposite.|
| bool hasOption | Whether the printing has an option flag. The value **true** indicates that the printing has an option flag, and **false** indicates the opposite.|
| char options[256] | Print options.|
