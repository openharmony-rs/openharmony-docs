# Print_PrintJob

```c
typedef struct Print_PrintJob {...} Print_PrintJob
```

## Overview

Represents a print job, which is used to configure the attributes of a print job, including the number of copies, paper source, color mode, duplex mode, resolution, margin, orientation mode, print quality, document format, and advanced options. You can initiate a print job by populating this struct and submitting it to the print module API.

<!--Device-typedef struct Print_PrintJob {...} Print_PrintJob--><!--Device-typedef struct Print_PrintJob {...} Print_PrintJob-End-->

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-basic-services-kit-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *jobName | Task name, which identifies the print task and distinguishes it from other tasks.<br><!--Device-char *jobName--><!--Device-char *jobName-End--> |
| uint32_t *fdList | Array of file descriptors to be printed. This parameter must be used together with **fdListCount**. The value of **fdListCount** must be equal to the number of elements in this array.<br><!--Device-uint32_t *fdList--><!--Device-uint32_t *fdList-End--> |
| uint32_t fdListCount | Number of file descriptors to be printed. The value must be greater than or equal to 1, and must be the same as the length of the **fdList** array.<br><!--Device-uint32_t fdListCount--><!--Device-uint32_t fdListCount-End--> |
| char *printerId | Printer ID, which specifies the target printer. You can obtain a valid printer ID by calling the related query API, for example, [OH_Print_QueryPrinterList](capi-ohprint-h.md#oh_print_queryprinterlist).<br><!--Device-char *printerId--><!--Device-char *printerId-End--> |
| uint32_t copyNumber | Number of copies to print. The value must be greater than or equal to 1.<br><!--Device-uint32_t copyNumber--><!--Device-uint32_t copyNumber-End--> |
| char *paperSource | Paper source, which specifies the paper feeding mode. The available values depend on the paper source options supported by the printer.<br><!--Device-char *paperSource--><!--Device-char *paperSource-End--> |
| char *mediaType | Media type, which specifies the type of the printing media, such as ordinary paper, glossy paper, and photo paper. The available values depend on the media type options supported by the printer.<br><!--Device-char *mediaType--><!--Device-char *mediaType-End--> |
| char *pageSizeId | Paper size ID, which specifies the size of the paper to be printed, such as **ISO A4**, **Letter**, and **A3**. The available values depend on the size options supported by the printer.<br><!--Device-char *pageSizeId--><!--Device-char *pageSizeId-End--> |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) colorMode | Color mode. The color mode is suitable for documents (such as images) that require color display. The monochrome mode is suitable for printing plain text or drafts to save consumables. The automatic mode allows the system to automatically select the color mode.<br><!--Device-Print_ColorMode colorMode--><!--Device-Print_ColorMode colorMode-End--> |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) duplexMode | Duplex mode. The single-sided mode is suitable for single-sided printing. The long-edge flip mode is suitable for documents that are turned vertically (such as books). The short-edge flip mode is suitable for documents that are turned horizontally (such as calendars).<br><!--Device-Print_DuplexMode duplexMode--><!--Device-Print_DuplexMode duplexMode-End--> |
| [Print_Resolution](capi-print-print-resolution.md) resolution | Print resolution, in dpi. A high resolution is suitable for printing fine content such as images, while a low resolution is suitable for printing plain text or drafts to save on consumables and printing time.<br><!--Device-Print_Resolution resolution--><!--Device-Print_Resolution resolution-End--> |
| [Print_Margin](capi-print-print-margin.md) printMargin | Print margin, in millimeters. You are advised to set the margin based on the document type and the minimum margin supported by the printer. If the margin is too small, the printed content may be cropped.<br><!--Device-Print_Margin printMargin--><!--Device-Print_Margin printMargin-End--> |
| bool borderless | Whether to print without margins. The value **true** means to print without margins, and **false** means the opposite.<br><!--Device-bool borderless--><!--Device-bool borderless-End--> |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) orientationMode | Orientation mode. The portrait mode is suitable for printing regular documents. The landscape mode is suitable for printing wide content such as tables and charts. The reverse landscape mode is suitable for printing horizontal content that requires mirroring. The reverse portrait mode is suitable for printing vertical content that requires mirroring. If no mode is specified, the system automatically selects an orientation.<br><!--Device-Print_OrientationMode orientationMode--><!--Device-Print_OrientationMode orientationMode-End--> |
| [Print_Quality](capi-ohprint-h.md#print_quality) printQuality | Print quality. The high-quality mode is suitable for final output or formal documents. The normal mode is suitable for daily printing. The draft mode is suitable for quick preview to save consumables.<br><!--Device-Print_Quality printQuality--><!--Device-Print_Quality printQuality-End--> |
| [Print_DocumentFormat](capi-ohprint-h.md#print_documentformat) documentFormat | MIME media type of the document, for example, PDF (application/pdf) or JPEG (image/jpeg).<br><!--Device-Print_DocumentFormat documentFormat--><!--Device-Print_DocumentFormat documentFormat-End--> |
| char *advancedOptions | Advanced options in JSON format. <br>The following keys are supported: <br>- **isReverse**: Boolean type, indicating whether to print in reverse order. <br>- **isCollate**: Boolean type, indicating whether to print copies one by one. <br>- **printPages**: Integer type, indicating the actual number of pages to print. The value must be greater than or equal to 1. Default value is 1.<br><!--Device-char *advancedOptions--><!--Device-char *advancedOptions-End--> |


