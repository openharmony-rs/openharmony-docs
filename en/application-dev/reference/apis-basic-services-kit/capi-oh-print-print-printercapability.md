# Print_PrinterCapability
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrinterCapability
```

## Overview

Defines a struct for the printer capabilities.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) *supportedColorModes | Array of supported color modes.|
| uint32_t supportedColorModesCount | Number of supported color modes.|
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) *supportedDuplexModes | Array of supported duplex modes.|
| uint32_t supportedDuplexModesCount | Number of supported duplex modes.|
| [Print_PageSize](capi-oh-print-print-pagesize.md) *supportedPageSizes | Array of supported page sizes.|
| uint32_t supportedPageSizesCount | Number of supported page sizes.|
| char *supportedMediaTypes | Array of supported print media types in JSON string format.|
| [Print_Quality](capi-ohprint-h.md#print_quality) *supportedQualities | Array of supported print qualities.|
| uint32_t supportedQualitiesCount | Number of supported print qualities.|
| char *supportedPaperSources | Array of supported paper sources in JSON string format.|
| uint32_t supportedCopies | Supported number of copies.|
| [Print_Resolution](capi-oh-print-print-resolution.md) *supportedResolutions | Array of supported printer resolutions.|
| uint32_t supportedResolutionsCount | Supported number of printer resolutions.|
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) *supportedOrientations | Array of supported orientations.|
| uint32_t supportedOrientationsCount | Supported number of orientations.|
| char *advancedCapability | Advanced capabilities in JSON format.|
