# OH_CloudDisk_FetchDataRequest
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:44:42.282Z pushedAt=2026-11-04T03:11:33.446Z nl=1 -->

```c
typedef struct OH_CloudDisk_FetchDataRequest {...} OH_CloudDisk_FetchDataRequest
```

## Overview

Obtains the data request information.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | Relative file path within the sync root.<br>**Since:** 26.0.1 |
| [OH_CloudDisk_HydratePriority](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_hydratepriority) priority | Hydration priority.<br>**Since:** 26.0.1 |
