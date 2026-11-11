# OH_CloudDisk_DataBuf
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:43:57.682Z pushedAt=2026-11-04T03:11:33.443Z nl=1 -->

```c
typedef struct OH_CloudDisk_DataBuf {...} OH_CloudDisk_DataBuf
```

## Overview

Cloud disk data buffer information.

**Since:** 26.0.1

**Related Modules:** [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t *data | Pointer to the data buffer.<br>**Since:** 26.0.1 |
| uint64_t dataSize | Size of the data buffer, in bytes.<br>**Since:** 26.0.1 |
