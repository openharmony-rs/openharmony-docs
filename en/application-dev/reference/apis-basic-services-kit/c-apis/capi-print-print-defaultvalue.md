# Print_DefaultValue

```c
typedef struct Print_DefaultValue {...} Print_DefaultValue
```

## Overview

Defines a struct for the default property value.

**Since**: 12

**Related module**: [Print](capi-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_ColorMode](capi-ohprint-h.md#print_colormode) defaultColorMode | Default color mode. |
| [Print_DuplexMode](capi-ohprint-h.md#print_duplexmode) defaultDuplexMode | Default duplex mode. |
| char *defaultMediaType | Default media type. |
| char *defaultPageSizeId | Default page size ID. |
| [Print_Margin](capi-print-print-margin.md) defaultMargin | Default margin. |
| char *defaultPaperSource | Default paper source. |
| [Print_Quality](capi-ohprint-h.md#print_quality) defaultPrintQuality | Default print quality. |
| uint32_t defaultCopies | Default number of copies. |
| [Print_Resolution](capi-print-print-resolution.md) defaultResolution | Default printer resolution. |
| [Print_OrientationMode](capi-ohprint-h.md#print_orientationmode) defaultOrientation | Default orientation. |
| char *otherDefaultValues | Other default values in JSON format. |


