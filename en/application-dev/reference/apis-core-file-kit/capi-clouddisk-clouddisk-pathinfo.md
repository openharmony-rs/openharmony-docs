# CloudDisk_PathInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=4165f338bbfe7f5ad0b3bd882976a1f16b4d44a0 translatedAt=2026-11-04T03:36:36.320Z pushedAt=2026-11-04T10:12:33.390Z nl=1 -->

```c
typedef struct CloudDisk_PathInfo {...} CloudDisk_PathInfo
typedef struct CloudDisk_PathInfo CloudDisk_FileIdInfo
typedef struct CloudDisk_PathInfo CloudDisk_SyncFolderPath
```

## Overview

A struct that encapsulates the file path information.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *value | Pointer to the file path, which ends with '\0'.|
| size_t length | Length of the file path, excluding the '\0' character at the end.|


