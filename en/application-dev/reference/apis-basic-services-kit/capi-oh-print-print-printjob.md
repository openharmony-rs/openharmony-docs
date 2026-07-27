# Print_PrintJob
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrintJob
```

## Overview

Defines a struct for the print job.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *jobName | Job name.|
| uint32_t *fdList | Array of file descriptors to be printed.|
| uint32_t fdListCount | Number of file descriptors to be printed.|
| char *printerId | Printer ID.|
| uint32_t copyNumber | Number of copies to print.|
| char *paperSource | Paper source.|
| char *mediaType | Media type.|
| char *pageSizeId | Page size ID.|
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) colorMode | Color mode.|
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) duplexMode | Duplex mode.|
| [Print_Resolution](capi-oh-print-print-resolution.md) resolution | Print resolution, in dpi.|
| [Print_Margin](capi-oh-print-print-margin.md) printMargin | Page margin.|
| bool borderless | Whether to print without margins.|
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) orientationMode | Orientation mode.|
| [Print_Quality](capi-ohprint-h.md#print_quality) printQuality | Print quality.|
| [Print_DocumentFormat](capi-ohprint-h.md#print_documentformat) documentFormat | Document format.|
| char *advancedOptions | Advanced options in JSON format.<br>The supported keys are as follows:<br>- **isReverse**: Boolean type, indicating whether to print in reverse order.<br>- **isCollate**: Boolean type, indicating whether to print copies one by one.|
