# Print_PrinterInfo
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PrinterInfo
```

## Overview

Defines a struct for the printer information.

**Since**: 12

**Related module**: [OH_Print](capi-oh-print.md)

**Header file**: [ohprint.h](capi-ohprint-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Print_PrinterState](capi-ohprint-h.md#print_printerstate) printerState | Printer state.|
| [Print_PrinterCapability](capi-oh-print-print-printercapability.md) capability | Printer capability.|
| [Print_DefaultValue](capi-oh-print-print-defaultvalue.md) defaultValue | Default property value of the printer.|
| bool isDefaultPrinter | Default printer.|
| char *printerId | Printer ID.|
| char *printerName | Printer name.|
| char *description | Printer description.|
| char *location | Printer location.|
| char *makeAndModel | Brand and model of the printer.|
| char *printerUri | Printer URI.|
| char *detailInfo | Details in JSON format.<br>The supported keys are as follows:<br>- **printerAlias**: string type, indicating the printer alias. **Since**: 24<br>- **vendorId**: int type, indicating the USB vendor ID of the printer. **Since**: 12<br>- **productId**: int type, indicating the USB product ID of the printer. **Since**: 12<br>- **protocol**: string array, indicating the list of protocols detected for the printer. **Since**: 24<br>- **ipp**: string type, indicating the printer URI for the detected IPP protocol. **Since**: 24<br>- **ipps**: string type, indicating the printer URI for the detected IPPS protocol. **Since**: 24<br>- **lpd**: string type, indicating the printer URI for the detected LPD protocol. **Since**: 24<br>- **socket**: string type, indicating the printer URI for the detected Socket protocol. **Since**: 24|
