# Scan_PictureScanProgress

```c
typedef struct Scan_PictureScanProgress {...} Scan_PictureScanProgress
```

## Overview

Defines the progress of scanning a picture by the scanner.

**System capability**: SystemCapability.Print.PrintFramework

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t progress | Picture scanning progress, in percentage. The value ranges from 0 to 100. |
| int32_t fd | Scanner file handle. |
| bool isFinal | Whether the picture is the last one to be scanned. The value **true** indicates that the picture is the last one to be scanned, and **false** indicates the opposite. |


