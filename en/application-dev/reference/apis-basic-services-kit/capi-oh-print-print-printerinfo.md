# Print_PrinterInfo
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T03:09:35.716Z pushedAt=2026-09-03T11:08:19.089Z -->

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
| char *printerId | Printer ID.|
| char *printerName | Printer name.|
| char *description | Printer description.|
| char *location | Printer location.|
| char *makeAndModel | Brand and model of the printer.|
| char *printerUri | Printer URI, which is used to locate and access the printer. The value is in the format of **scheme://[user@]host[:port]/resource**. |
| char *detailInfo | Details in JSON format.<br>The supported keys are as follows:<br>- **printerAlias**: printer alias, the value is of the string type. This key is supported since API version 24.<br>- **vendorId**: USB printer VID, the value is of the int type and within the range of [0, 65535]. This key is supported since API version 12.<br>- **productId**: USB printer PID, the value is of the int type and within the range of [0, 65535]. This key is supported since API version 12.<br>- **protocol**: array of protocols supported by the printer. The value is of the string type, and the options include **ipp**, **ipps**, **lpd**, and **socket**. This key is supported since API version 24.<br>- **ipp**: printer URI of the IPP protocol, the value is of the string type. This key is supported since API version 24.<br>- **ipps**: printer URI of the IPPS protocol, the value is of the string type. This key is supported since API version 24.<br>- **lpd**: printer URI of the LPD protocol, the value is of the string type. This key is supported since API version 24.<br>- **socket**: printer URI of the Socket protocol, the value is of the string type. This key is supported since API version 24. |



