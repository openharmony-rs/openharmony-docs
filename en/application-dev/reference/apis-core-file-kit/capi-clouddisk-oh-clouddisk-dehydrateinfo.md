# OH_CloudDisk_DehydrateInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:44:04.887Z pushedAt=2026-11-04T03:11:33.444Z nl=1 -->

```c
typedef struct OH_CloudDisk_DehydrateInfo {...} OH_CloudDisk_DehydrateInfo
```

## Overview

Dehydration authorization information.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | Relative file path within the sync root.<br>**Since:** 26.0.1 |
| bool allow | Whether dehydration is allowed. The value true indicates that dehydration is allowed for this file; the value false indicates that dehydration is not allowed, and the application should skip the dehydration operation for this file.<br>**Since:** 26.0.1 |
