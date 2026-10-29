# Print_PrintAttributes
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f172f47675a58f89bb693013f28ad2465486c311 translatedAt=2026-10-09T11:41:55.186Z pushedAt=2026-10-10T03:42:10.723Z -->

```cpp
typedef struct {...} Print_PrintAttributes
```

## Overview

Represents the print attributes to be configured in a print task, including the print range, paper size, margin, number of copies, duplex mode, color mode, print orientation, and print options. This API can be used to perform refined control over the print output.

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
| uint32_t copyNumber                                        | Number of copies. The value must be greater than or equal to 1.                 |
| uint32_t duplexMode                                        | Duplex mode. For details about the valid values, see [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode).             |
| uint32_t colorMode                                         | Color mode. For details about the valid values, see [Print_ColorMode](capi-ohprint-h.md#print_colormode).             |
| bool isSequential                                          | Whether pages are printed in sequential order.<br>The value **true** indicates that pages are printed in sequential order, and **false** indicates that pages are printed in reverse order. |
| bool isLandscape                                           | Whether pages are printed in landscape mode.<br>The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode. |
| bool hasOption                                             | Whether the printing has an option flag.<br>The value **true** indicates that the printing has an option flag (the **options** field is valid), and **false** indicates the opposite (the **options** field is invalid). |
| char options[256]                                          | Printing options, which are used to pass additional printing configuration parameters. This parameter is valid only when **hasOption** is set to **true**. The value can contain a maximum of 255 characters.             |

