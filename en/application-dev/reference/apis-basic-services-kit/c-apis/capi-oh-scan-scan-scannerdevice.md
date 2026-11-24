# Scan_ScannerDevice

```c
typedef struct Scan_ScannerDevice {...} Scan_ScannerDevice
```

## Overview

Represents the scanner device information, including the scanner ID, manufacturer, model, discovery mode, and serial number. It is used to obtain device details during the scanner discovery process. You can obtain this struct using the scanner discovery API to select the target scanner for scanning. For details about the design logic of the related module, see OH_Scan.

<!--Device-typedef struct Scan_ScannerDevice {...} Scan_ScannerDevice--><!--Device-typedef struct Scan_ScannerDevice {...} Scan_ScannerDevice-End-->

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [OH_Scan](capi-basic-services-kit-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *scannerId | Scanner ID.<br><!--Device-const char *scannerId--><!--Device-const char *scannerId-End--> |
| const char *manufacturer | Scanner manufacturer.<br><!--Device-const char *manufacturer--><!--Device-const char *manufacturer-End--> |
| const char *model | Scanner model.<br><!--Device-const char *model--><!--Device-const char *model-End--> |
| const char *discoverMode | Scanner discovery mode, indicating how the scanner is discovered by the system. The value **TCP** indicates that the scanner is discovered over the network, and the value **USB** indicates that the scanner is discovered through the USB connection.<br><!--Device-const char *discoverMode--><!--Device-const char *discoverMode-End--> |
| const char *serialNumber | Scanner serial number.<br><!--Device-const char *serialNumber--><!--Device-const char *serialNumber-End--> |


