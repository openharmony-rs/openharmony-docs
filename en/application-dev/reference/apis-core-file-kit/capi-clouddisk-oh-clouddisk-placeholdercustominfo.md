# OH_CloudDisk_PlaceholderCustomInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=36f5c809bf10cb082643c8b6a0ce69b4a4b79846 translatedAt=2026-11-03T03:45:11.767Z pushedAt=2026-11-04T03:11:33.450Z nl=1 -->

```c
typedef struct OH_CloudDisk_PlaceholderCustomInfo OH_CloudDisk_PlaceholderCustomInfo
```

## Overview

Opaque custom information associated with the placeholder.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| size_t dataLength | Length of the custom information, in bytes.<br>**Since:** 26.0.1 |
| const uint8_t *data | Pointer to the custom information.<br>**Since:** 26.0.1 |

