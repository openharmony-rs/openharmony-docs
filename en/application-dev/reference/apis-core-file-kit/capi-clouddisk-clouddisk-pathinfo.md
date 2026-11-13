# CloudDisk_PathInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:42:24.099Z pushedAt=2026-11-04T03:11:33.431Z nl=1 -->

```c
typedef struct CloudDisk_PathInfo {...} CloudDisk_PathInfo
typedef struct CloudDisk_PathInfo CloudDisk_FileIdInfo
typedef struct CloudDisk_PathInfo CloudDisk_SyncFolderPath
```

## Overview

File path information, used to describe the file paths involved in cloud disk management APIs and their lengths.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *value | Path string of the file, ending with the '\0' character. |
| size_t length | Length of the file path, excluding the '\0' character at the end.|


