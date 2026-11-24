# Print_PrinterInfo

```c
typedef struct Print_PrinterInfo {...} Print_PrinterInfo
```

## Overview

Represents the printer information, including the printer status, capabilities, default attributes, and identification information (such as the printer ID, name, description, location, brand, model, and URI). This API can be used by apps to obtain and display detailed printer information in printing scenarios, helping developers select appropriate printers based on their capabilities and attributes. You can obtain the value by calling [OH_Print_StartPrinterDiscovery](capi-ohprint-h.md#oh_print_startprinterdiscovery) or [OH_Print_QueryPrinterInfo](capi-ohprint-h.md#oh_print_queryprinterinfo).

<!--Device-typedef struct Print_PrinterInfo {...} Print_PrinterInfo--><!--Device-typedef struct Print_PrinterInfo {...} Print_PrinterInfo-End-->

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [Print](capi-basic-services-kit-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Print_PrinterState](capi-ohprint-h.md#print_printerstate) printerState | Current running state of the printer.<br><!--Device-Print_PrinterState printerState--><!--Device-Print_PrinterState printerState-End--> |
| [Print_PrinterCapability](capi-print-print-printercapability.md) capability | Capabilities supported by the printer, such as the paper sizes and color modes.<br><!--Device-Print_PrinterCapability capability--><!--Device-Print_PrinterCapability capability-End--> |
| [Print_DefaultValue](capi-print-print-defaultvalue.md) defaultValue | Default attributes of the printer, such as the default paper size and color mode.<br><!--Device-Print_DefaultValue defaultValue--><!--Device-Print_DefaultValue defaultValue-End--> |
| bool isDefaultPrinter | Whether the printer is the default one. The value **true** indicates that the printer is the default one, and the value **false** indicates the opposite.<br><!--Device-bool isDefaultPrinter--><!--Device-bool isDefaultPrinter-End--> |
| char *printerId | Printer ID, which specifies the target printer. You can obtain a valid printer ID by calling the related query API, for example, [OH_Print_QueryPrinterList](capi-ohprint-h.md#oh_print_queryprinterlist).<br><!--Device-char *printerId--><!--Device-char *printerId-End--> |
| char *printerName | Printer name.<br><!--Device-char *printerName--><!--Device-char *printerName-End--> |
| char *description | Printer description.<br><!--Device-char *description--><!--Device-char *description-End--> |
| char *location | Printer location.<br><!--Device-char *location--><!--Device-char *location-End--> |
| char *makeAndModel | Brand and model of the printer.<br><!--Device-char *makeAndModel--><!--Device-char *makeAndModel-End--> |
| char *printerUri | Printer URI, which is used to locate and access the printer. The value is in the format of **scheme://[user@] host[:port]/resource**.<br><!--Device-char *printerUri--><!--Device-char *printerUri-End--> |
| char *detailInfo | Details in JSON format. <br>The supported keys are as follows: <br>- **printerAlias**: printer alias, the value is of the string type. This key is supported since API version 24. <br>- **vendorId**: USB printer VID, the value is of the int type and within the range of [0, 65535]. This key is supported since API version 12. <br>- **productId**: USB printer PID, the value is of the int type and within the range of [0, 65535]. This key is supported since API version 12. <br>- **protocol**: array of protocols supported by the printer. The value is of the string type, and the options include **ipp**, **ipps**, **lpd**, and **socket**. This key is supported since API version 24. <br>- **ipp**: printer URI of the IPP protocol, the value is of the string type. This key is supported since API version 24. <br>- **ipps**: printer URI of the IPPS protocol, the value is of the string type. This key is supported since API version 24. <br>- **lpd**: printer URI of the LPD protocol, the value is of the string type. This key is supported since API version 24. <br>- **socket**: printer URI of the Socket protocol, the value is of the string type. This key is supported since API version 24.<br><!--Device-char *detailInfo--><!--Device-char *detailInfo-End--> |


