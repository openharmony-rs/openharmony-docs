# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=bf611caa56efccbf7609e58b71abec1b4e33c1b6 translatedAt=2026-10-09T11:46:50.377Z pushedAt=2026-10-10T04:43:31.545Z -->

```cpp
typedef struct {...} Scan_ScannerDevice
```

## Overview

Represents the scanner device information, including the scanner ID, manufacturer, model, discovery mode, and serial number. It is used to obtain device details during the scanner discovery process. You can obtain this struct using the scanner discovery API to select the target scanner for scanning. For details about the design logic of the related module, see [OH_Scan](capi-oh-scan.md).

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* scannerId | Scanner ID. |
| const char* manufacturer | Scanner manufacturer. |
| const char* model | Scanner model. |
| const char* discoverMode | Scanner discovery mode, indicating how the scanner is discovered by the system. The value **TCP** indicates that the scanner is discovered over the network, and the value **USB** indicates that the scanner is discovered through the USB connection. |
| const char* serialNumber | Scanner serial number. |


