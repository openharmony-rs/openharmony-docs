# Scan_PictureScanProgress
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T03:12:26.423Z pushedAt=2026-09-03T12:17:38.344Z -->

```cpp
typedef struct {...} Scan_PictureScanProgress
```

## Overview

Defines the progress of scanning a picture by the scanner. This struct contains the **progress**, **fd** (file descriptor), and **isFinal** (whether the picture is the last one to be scanned) attributes. It can be used to track the picture scanning status in real time and obtain the scanning result file in an app. For details about the implementation mechanism, see [OH_Scan](capi-oh-scan.md).

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t progress | Picture scanning progress, in percentage. The value range is [0, 100]. The value **0** indicates that the scanning starts, and the value **100** indicates that the scanning is complete. |
| int32_t fd | File descriptor of the scanned picture, which is used to read the image data transmitted by the scanner. **fd** is valid only when the value of **progress** is **100**. |
| bool isFinal | Whether the picture is the last one to be scanned. The value **true** indicates that the picture is the last one to be scanned, and **false** indicates that the picture is not the last one. |


