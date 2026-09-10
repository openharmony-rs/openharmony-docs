# Print_PrintJob
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PrintJob
```

## Overview

Represents a print job, which is used to configure the attributes of a print job, including the number of copies, paper source, color mode, duplex mode, resolution, margin, orientation mode, print quality, document format, and advanced options. You can initiate a print job by populating this struct and submitting it to the print module API.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *jobName | Task name, which identifies the print task and distinguishes it from other tasks.|
| uint32_t *fdList | Array of file descriptors to be printed. This parameter must be used together with **fdListCount**. The value of **fdListCount** must be equal to the number of elements in this array.|
| uint32_t fdListCount | Number of file descriptors to be printed. The value must be greater than or equal to 1, and must be the same as the length of the **fdList** array.|
| char *printerId | Printer ID, which specifies the target printer. You can obtain a valid printer ID by calling the related query API, for example, [OH_Print_QueryPrinterList](capi-ohprint-h.md#oh_print_queryprinterlist).|
| uint32_t copyNumber | Number of copies to print. The value must be greater than or equal to 1.|
| char *paperSource | Paper source, which specifies the paper feeding mode. The available values depend on the paper source options supported by the printer.|
| char *mediaType | Media type, which specifies the type of the printing media, such as ordinary paper, glossy paper, and photo paper. The available values depend on the media type options supported by the printer.|
| char *pageSizeId | Paper size ID, which specifies the size of the paper to be printed, such as **ISO A4**, **Letter**, and **A3**. The available values depend on the size options supported by the printer.|
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) colorMode | Color mode. The color mode is suitable for documents (such as images) that require color display. The monochrome mode is suitable for printing plain text or drafts to save consumables. The automatic mode allows the system to automatically select the color mode.|
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) duplexMode | Duplex mode. The single-sided mode is suitable for single-sided printing. The long-edge flip mode is suitable for documents that are turned vertically (such as books). The short-edge flip mode is suitable for documents that are turned horizontally (such as calendars).|
| [Print_Resolution](capi-oh-print-print-resolution.md) resolution | Print resolution, in dpi. A high resolution is suitable for printing fine content such as images, while a low resolution is suitable for printing plain text or drafts to save on consumables and printing time.|
| [Print_Margin](capi-oh-print-print-margin.md) printMargin | Print margin, in millimeters. You are advised to set the margin based on the document type and the minimum margin supported by the printer. If the margin is too small, the printed content may be cropped.|
| bool borderless | Whether to print without margins. The value **true** means to print without margins, and **false** means the opposite.|
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) orientationMode | Orientation mode. The portrait mode is suitable for printing regular documents. The landscape mode is suitable for printing wide content such as tables and charts. The reverse landscape mode is suitable for printing horizontal content that requires mirroring. The reverse portrait mode is suitable for printing vertical content that requires mirroring. If no mode is specified, the system automatically selects an orientation.|
| [Print_Quality](capi-ohprint-h.md#print_quality) printQuality | Print quality. The high-quality mode is suitable for final output or formal documents. The normal mode is suitable for daily printing. The draft mode is suitable for quick preview to save consumables.|
| [Print_DocumentFormat](capi-ohprint-h.md#print_documentformat) documentFormat | MIME media type of the document, for example, PDF (application/pdf) or JPEG (image/jpeg).|
| char *advancedOptions | Advanced options in JSON format.<br>The following keys are supported:<br>- **isReverse**: Boolean type, indicating whether to print in reverse order.<br>- **isCollate**: Boolean type, indicating whether to print copies one by one.|
