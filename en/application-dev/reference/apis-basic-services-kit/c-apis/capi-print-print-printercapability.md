# Print_PrinterCapability

```c
typedef struct Print_PrinterCapability {...} Print_PrinterCapability
```

## Overview

Describes the printer capabilities, including the supported colors, duplex modes, paper sizes, media types, print quality, paper sources, copies, resolution, print orientations, and advanced capabilities. This API can be used to query or match printer capabilities, helping developers configure and adapt print tasks based on printer capabilities.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-others-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Print_ColorMode *supportedColorModes | Array of supported color modes. The array length is determined by **supportedColorModesCount**. |
| uint32_t supportedColorModesCount | Number of supported color modes, which is the same as the actual number of elements in the **supportedColorModes** array. |
| Print_DuplexMode *supportedDuplexModes | Array of supported duplex modes. The array length is determined by **supportedDuplexModesCount**. |
| uint32_t supportedDuplexModesCount | Number of supported duplex modes, which is the same as the actual number of elements in the **supportedDuplexModes** array. |
| Print_PageSize *supportedPageSizes | Array of supported paper sizes. The array length is determined by **supportedPageSizesCount**. |
| uint32_t supportedPageSizesCount | Number of supported paper sizes, which is the same as the actual number of elements in the **supportedPageSizes**<br>array. |
| char *supportedMediaTypes | Supported print media types. The value is a string in JSON format and determined by the printer. |
| Print_Quality *supportedQualities | Array of supported print quality options. The array length is determined by **supportedQualitiesCount**. |
| uint32_t supportedQualitiesCount | Number of supported print quality options, which is the same as the actual number of elements in the **supportedQualities** array. |
| char *supportedPaperSources | Supported paper sources. The value is a string in JSON array format and determined by the printer. |
| uint32_t supportedCopies | Number of supported copies. The value is determined by the printer capability. |
| Print_Resolution *supportedResolutions | Array of supported printer resolutions. The array length is determined by **supportedResolutionsCount**. |
| uint32_t supportedResolutionsCount | Number of supported printer resolutions, which is the same as the actual number of elements in the **supportedResolutions** array. |
| Print_OrientationMode *supportedOrientations | Array of supported print orientation modes. The array length is determined by **supportedOrientationsCount**. |
| uint32_t supportedOrientationsCount | Number of supported print orientation modes, which is the same as the actual number of elements in the **supportedOrientations** array. |
| char *advancedCapability | Advanced capability. The value is a string in JSON format. This parameter is used to describe printer features other than those described above. The specific field names and values of the JSON object are determined by the printer. You need to parse the JSON object based on the actual returned content. |


