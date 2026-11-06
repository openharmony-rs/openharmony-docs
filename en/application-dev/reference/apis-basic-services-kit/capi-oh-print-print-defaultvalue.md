# Print_DefaultValue
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T03:03:03.512Z pushedAt=2026-09-03T08:36:24.578Z -->

```cpp
typedef struct {...} Print_DefaultValue
```

## Overview

Enumerates default attributes of a printer, including the color mode, duplex mode, media type, paper size, margin, paper source, print quality, copies, resolution, and orientation.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) defaultColorMode | Default color mode, which indicates the color mode of the print output. The value is determined by the color modes supported by the printer. |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) defaultDuplexMode | Default duplex mode, which indicates whether printing is single-sided or double-sided. The value is determined by the duplex modes supported by the printer. |
| char *defaultMediaType | Default media type, which indicates the type of media (such as ordinary paper or glossy paper) used for printing. The value is determined by the media types supported by the printer. |
| char *defaultPageSizeId | Default paper size ID, which indicates the paper size ID (such as **A4** or **Letter**) used for printing. The value is determined by the paper sizes supported by the printer. |
| [Print_Margin](capi-oh-print-print-margin.md) defaultMargin | Default margin, which indicates the margin settings of the printed page. The value is determined by the margins supported by the printer. |
| char *defaultPaperSource | Default paper source, which indicates the paper source (such as automatic paper feeder or manual feeding) used for printing. The value is determined by the paper sources supported by the printer. |
| [Print_Quality](capi-ohprint-h.md#print_quality) defaultPrintQuality | Default print quality, which indicates the quality level of the print. The value is determined by the print quality supported by the printer. |
| uint32_t defaultCopies | Default number of copies. The value must be greater than or equal to 1. |
| [Print_Resolution](capi-oh-print-print-resolution.md) defaultResolution | Default resolution, which indicates the resolution of the print. The value is determined by the resolutions supported by the printer. |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) defaultOrientation | Default print orientation, which indicates the orientation (such as portrait or landscape) of the print. The value is determined by the print orientations supported by the printer. |
| char *otherDefaultValues | Other default values in JSON format, which indicate additional default print attributes that are not listed in the preceding member variables. The key-value pairs that can be set are determined by the extended capabilities supported by the printer. |


