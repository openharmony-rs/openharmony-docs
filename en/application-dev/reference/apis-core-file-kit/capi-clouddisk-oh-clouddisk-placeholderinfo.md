# OH_CloudDisk_PlaceholderInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=054fc5e77d4aade491541c0c5d73757a31378403 translatedAt=2026-11-04T03:43:08.127Z pushedAt=2026-11-04T10:12:33.414Z nl=1 -->

```c
typedef struct OH_CloudDisk_PlaceholderInfo {...} OH_CloudDisk_PlaceholderInfo
```

## Overview

File metadata information used by placeholder-related operations.

**Since:** 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t logicalSize | Logical size of the placeholder file, indicating the size of its corresponding cloud file, in bytes.<br>**Since:** 26.0.1 |
| uint64_t atimeMs | Creation time of the cloud file corresponding to the placeholder file, in milliseconds.<br>**Since:** 26.0.1 |
| uint64_t mtimeMs | Last modification time of the cloud file corresponding to the placeholder file, in milliseconds.<br>**Since:** 26.0.1 |
