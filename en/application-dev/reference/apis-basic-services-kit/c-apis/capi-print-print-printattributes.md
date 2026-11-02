# Print_PrintAttributes

```c
typedef struct Print_PrintAttributes {...} Print_PrintAttributes
```

## Overview

Represents the print attributes to be configured in a print task, including the print range, paper size, margin, number of copies, duplex mode, color mode, print orientation, and print options. This API can be used to perform refined control over the print output.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 13

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_Range](capi-print-print-range.md) pageRange | Print range. |
| [Print_PageSize](capi-print-print-pagesize.md) pageSize | Page size. |
| [Print_Margin](capi-print-print-margin.md) pageMargin | Print margin, in millimeters. You are advised to set the margin based on the document type and the minimum margin supported by the printer. If the margin is too small, the printed content may be cropped. |
| uint32_t copyNumber | Number of copies to print. The value must be greater than or equal to 1. |
| uint32_t duplexMode | Duplex mode. The single-sided mode is suitable for single-sided printing. The long-edge flip mode is suitable for documents that are turned vertically (such as books). The short-edge flip mode is suitable for documents that are turned horizontally (such as calendars). |
| uint32_t colorMode | Color mode. The color mode is suitable for documents (such as images) that require color display. The monochrome mode is suitable for printing plain text or drafts to save consumables. The automatic mode allows the system to automatically select the color mode. |
| bool isSequential | Whether pages are printed in sequential order.<br>The value **true** indicates that pages are printed in sequential order, and **false** indicates that pages are printed in reverse order. |
| bool isLandscape | Whether pages are printed in landscape mode.<br>The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode. |
| bool hasOption | Whether the printing has an option flag.<br>The value **true** indicates that the printing has an option flag ( the **options** field is valid), and **false** indicates the opposite (the **options** field is invalid). |
| char options[256] | Printing options, which are used to pass additional printing configuration parameters. This parameter is valid only when **hasOption** is set to **true**. The value can contain a maximum of 255 characters. |


