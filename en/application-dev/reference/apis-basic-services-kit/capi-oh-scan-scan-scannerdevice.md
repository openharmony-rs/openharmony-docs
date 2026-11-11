# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=432796cf3e6a4be981f95a7796deb982eeaff362 translatedAt=2026-11-10T03:58:19.755Z pushedAt=2026-11-10T06:01:52.653Z nl=1 -->

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


