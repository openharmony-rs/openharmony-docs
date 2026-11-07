# OH_CloudDisk_PlaceholderCustomInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=59eeb9f6a3c275fe7a80a4997398fbcb8aee3ded translatedAt=2026-11-04T03:42:25.062Z pushedAt=2026-11-04T10:12:33.412Z nl=1 -->

```c
typedef struct OH_CloudDisk_PlaceholderCustomInfo OH_CloudDisk_PlaceholderCustomInfo
```

## Overview

Opaque custom information associated with a placeholder.

**Since:** 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| size_t dataLength | Length of the custom information, in bytes.<br>**Since:** 26.0.1 |
| const uint8_t *data | Pointer to the custom information.<br>**Since:** 26.0.1 |

