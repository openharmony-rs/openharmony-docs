# Scan_ScannerDevice
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Scan_ScannerDevice
```

## Overview

Defines scanner information.

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* scannerId | Scanner ID.|
| const char* manufacturer | Scanner manufacturer.|
| const char* model | Scanner model.|
| const char* discoverMode | Discovery mode of the scanner.|
| const char* serialNumber | Scanner serial number.|
