# Print_PrinterCapability

```c
typedef struct Print_PrinterCapability {...} Print_PrinterCapability
```

## Overview

Describes the printer capabilities, including the supported colors, duplex modes, paper sizes, media types, print quality, paper sources, copies, resolution, print orientations, and advanced capabilities. This API can be used to query or match printer capabilities, helping developers configure and adapt print tasks based on printer capabilities.

<!--Device-typedef struct Print_PrinterCapability {...} Print_PrinterCapability--><!--Device-typedef struct Print_PrinterCapability {...} Print_PrinterCapability-End-->

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-basic-services-kit-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) *supportedColorModes | Array of supported color modes. The array length is determined by **supportedColorModesCount**.<br><!--Device-Print_ColorMode *supportedColorModes--><!--Device-Print_ColorMode *supportedColorModes-End--> |
| uint32_t supportedColorModesCount | Number of supported color modes, which is the same as the actual number of elements in the **supportedColorModes** array.<br><!--Device-uint32_t supportedColorModesCount--><!--Device-uint32_t supportedColorModesCount-End--> |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) *supportedDuplexModes | Array of supported duplex modes. The array length is determined by **supportedDuplexModesCount**.<br><!--Device-Print_DuplexMode *supportedDuplexModes--><!--Device-Print_DuplexMode *supportedDuplexModes-End--> |
| uint32_t supportedDuplexModesCount | Number of supported duplex modes, which is the same as the actual number of elements in the **supportedDuplexModes** array.<br><!--Device-uint32_t supportedDuplexModesCount--><!--Device-uint32_t supportedDuplexModesCount-End--> |
| [Print_PageSize](capi-print-print-pagesize.md) *supportedPageSizes | Array of supported paper sizes. The array length is determined by **supportedPageSizesCount**.<br><!--Device-Print_PageSize *supportedPageSizes--><!--Device-Print_PageSize *supportedPageSizes-End--> |
| uint32_t supportedPageSizesCount | Number of supported paper sizes, which is the same as the actual number of elements in the **supportedPageSizes** array.<br><!--Device-uint32_t supportedPageSizesCount--><!--Device-uint32_t supportedPageSizesCount-End--> |
| char *supportedMediaTypes | Supported print media types. The value is a string in JSON format and determined by the printer.<br><!--Device-char *supportedMediaTypes--><!--Device-char *supportedMediaTypes-End--> |
| [Print_Quality](capi-ohprint-h.md#print_quality) *supportedQualities | Array of supported print quality options. The array length is determined by **supportedQualitiesCount**.<br><!--Device-Print_Quality *supportedQualities--><!--Device-Print_Quality *supportedQualities-End--> |
| uint32_t supportedQualitiesCount | Number of supported print quality options, which is the same as the actual number of elements in the **supportedQualities** array.<br><!--Device-uint32_t supportedQualitiesCount--><!--Device-uint32_t supportedQualitiesCount-End--> |
| char *supportedPaperSources | Supported paper sources. The value is a string in JSON array format and determined by the printer.<br><!--Device-char *supportedPaperSources--><!--Device-char *supportedPaperSources-End--> |
| uint32_t supportedCopies | Number of supported copies. The value is determined by the printer capability.<br><!--Device-uint32_t supportedCopies--><!--Device-uint32_t supportedCopies-End--> |
| [Print_Resolution](capi-print-print-resolution.md) *supportedResolutions | Array of supported printer resolutions. The array length is determined by **supportedResolutionsCount**.<br><!--Device-Print_Resolution *supportedResolutions--><!--Device-Print_Resolution *supportedResolutions-End--> |
| uint32_t supportedResolutionsCount | Number of supported printer resolutions, which is the same as the actual number of elements in the **supportedResolutions** array.<br><!--Device-uint32_t supportedResolutionsCount--><!--Device-uint32_t supportedResolutionsCount-End--> |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) *supportedOrientations | Array of supported print orientation modes. The array length is determined by **supportedOrientationsCount**.<br><!--Device-Print_OrientationMode *supportedOrientations--><!--Device-Print_OrientationMode *supportedOrientations-End--> |
| uint32_t supportedOrientationsCount | Number of supported print orientation modes, which is the same as the actual number of elements in the **supportedOrientations** array.<br><!--Device-uint32_t supportedOrientationsCount--><!--Device-uint32_t supportedOrientationsCount-End--> |
| char *advancedCapability | Advanced capability. The value is a string in JSON format. This parameter is used to describe printer features other than those described above. The specific field names and values of the JSON object are determined by the printer. You need to parse the JSON object based on the actual returned content.<br><!--Device-char *advancedCapability--><!--Device-char *advancedCapability-End--> |


