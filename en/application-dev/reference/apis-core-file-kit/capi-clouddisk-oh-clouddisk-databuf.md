# OH_CloudDisk_DataBuf
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=4165f338bbfe7f5ad0b3bd882976a1f16b4d44a0 translatedAt=2026-11-04T03:40:54.860Z pushedAt=2026-11-04T10:12:33.408Z nl=1 -->

```c
typedef struct OH_CloudDisk_DataBuf {...} OH_CloudDisk_DataBuf
```

## Overview

Cloud disk data buffer information.

**Since:** 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t *data | Pointer to the data buffer.<br>**Since:** 26.0.1 |
| uint64_t dataSize | Size of the data buffer, in bytes.<br>**Since:** 26.0.1 |
