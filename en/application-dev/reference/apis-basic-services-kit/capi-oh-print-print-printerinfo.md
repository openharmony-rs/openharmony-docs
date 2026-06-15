# Print_PrinterInfo

 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=417fc360382b810eaca71d157c09ed3f2422bbbb translatedAt=2026-06-10T02:10:03.544Z pushedAt=2026-06-10T05:56:30.853Z -->

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
| char *detailInfo | Detailed information in JSON format.<br>The supported keys are as follows:<br>- **printerAlias**: Printer alias, the value is of the string type. This key is supported since API version 24.<br>- **vendorId**: USB printer VID, the value is of the int type. This key is supported since API version 12.<br>- **productId**: USB printer PID, the value is of the int type. This key is supported since API version 12.<br>- **protocol**: List of protocols supported by the printer, the value is of the string type. This key is supported since API version 24.<br>- **ipp**: Printer URI of the IPP protocol, the value is of the string type. This key is supported since API version 24.<br>- **ipps**: Printer URI of the IPPS protocol, the value is of the string type. This key is supported since API version 24.<br>- **lpd**: Printer URI of the LPD protocol, the value is of the string type. This key is supported since API version 24.<br>- **socket**: Printer URI of the Socket protocol, the value is of the string type. This key is supported since API version 24. |