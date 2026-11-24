# OH_CloudDisk_PlaceholderInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-03T03:45:18.441Z pushedAt=2026-11-04T03:11:33.452Z nl=1 -->

```c
typedef struct OH_CloudDisk_PlaceholderInfo {...} OH_CloudDisk_PlaceholderInfo
```

## Overview

File metadata information used for placeholder-related operations.

**Since:** 26.0.1

**Related Modules:** [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t logicalSize | Logical size of the placeholder file, indicating the size of its corresponding cloud file, in bytes.<br>**Since:** 26.0.1 |
| uint64_t atimeMs | Creation time of the cloud file corresponding to the placeholder file, in milliseconds.<br>**Since:** 26.0.1 |
| uint64_t mtimeMs | Last modification time of the cloud file corresponding to the placeholder file, in milliseconds.<br>**Since:** 26.0.1 |
