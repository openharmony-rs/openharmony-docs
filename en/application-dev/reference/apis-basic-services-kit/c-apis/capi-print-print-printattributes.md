# Print_PrintAttributes

```c
typedef struct Print_PrintAttributes {...} Print_PrintAttributes
```

## Overview

Defines a struct for the print attributes.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 13

**Related module**: [Print](capi-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_Range](capi-print-print-range.md) pageRange | Page range. |
| [Print_PageSize](capi-print-print-pagesize.md) pageSize | Page size. |
| [Print_Margin](capi-print-print-margin.md) pageMargin | Page margin. |
| uint32_t copyNumber | Number of copies to print. |
| uint32_t duplexMode | Duplex mode. |
| uint32_t colorMode | Color mode. |
| bool isSequential | Whether pages are printed in sequential order.<br>The value **true** indicates that pages are printed in sequential order, and **false** indicates the opposite. |
| bool isLandscape | Whether pages are printed in landscape mode.<br>The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode. |
| bool hasOption | Whether the printing has an option flag.<br>The value **true** indicates that the printing has an option flag, and **false** indicates the opposite. |
| char options[256] | Print options. |


