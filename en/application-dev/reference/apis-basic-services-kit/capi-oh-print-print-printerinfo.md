# Print_PrinterInfo
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:57:09.345Z pushedAt=2026-11-10T05:59:11.730Z nl=1 -->

```cpp
typedef struct {...} Print_PrinterInfo
```

## Overview

Represents the printer information, including the printer status, capabilities, default attributes, and identification information (such as the printer ID, name, description, location, brand, model, and URI). This API can be used by apps to obtain and display detailed printer information in printing scenarios, helping developers select appropriate printers based on their capabilities and attributes. You can obtain the value by calling [OH_Print_StartPrinterDiscovery](capi-ohprint-h.md#oh_print_startprinterdiscovery) or [OH_Print_QueryPrinterInfo](capi-ohprint-h.md#oh_print_queryprinterinfo).

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Print_PrinterState](capi-ohprint-h.md#print_printerstate) printerState | Current running state of the printer. |
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) capability | Capabilities supported by the printer, such as the paper sizes and color modes. |
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md) defaultValue | Default attributes of the printer, such as the default paper size and color mode. |
| bool isDefaultPrinter | Whether the printer is the default one. The value **true** indicates that the printer is the default one, and the value **false** indicates the opposite. |
| char *printerId | Printer ID. |
| char *printerName | Printer name.|
| char *description | Printer description.|
| char *location | Printer location.|
| char *makeAndModel | Brand and model of the printer.|
| char *printerUri | Printer URI, which is used to locate and access the printer. The value is in the format of **scheme://[user@]host[:port]/resource**. |
| char *detailInfo | Detailed information in JSON format.<br>Supported keys include:<br>- **printerAlias**: string type, indicating the printer alias. **Since:** 24.<br>- **vendorId**: int type, indicating the VID of the USB printer, in the range [0, 65535]. **Since:** 12.<br>- **productId**: int type, indicating the PID of the USB printer, in the range [0, 65535]. **Since:** 12.<br>- **protocol**: string array, indicating the list of protocols supported by the detected printer. The values include ipp, ipps, lpd, and socket. **Since:** 24.<br>- **ipp**: string type, indicating the printer URI corresponding to the detected IPP protocol. **Since:** 24.<br>- **ipps**: string type, indicating the printer URI corresponding to the detected IPPS protocol. **Since:** 24.<br>- **lpd**: string type, indicating the printer URI corresponding to the detected LPD protocol. **Since:** 24.<br>- **socket**: string type, indicating the printer URI corresponding to the detected Socket protocol. **Since:** 24. |



