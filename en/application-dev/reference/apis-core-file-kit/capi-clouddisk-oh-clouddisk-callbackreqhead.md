# OH_CloudDisk_CallbackReqHead
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:43:25.902Z pushedAt=2026-11-04T03:11:33.438Z nl=1 -->

```c
typedef struct OH_CloudDisk_CallbackReqHead {...} OH_CloudDisk_CallbackReqHead
```

## Overview

Defines the cloud disk callback request header information.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [CloudDisk_SyncFolderPath](capi-clouddisk-clouddisk-pathinfo.md) syncFolderPath | Sync root path to which the callback request belongs.<br>**Since:** 26.0.1 |
| [OH_CloudDisk_CallbackType](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype) callbackType | Callback request type.<br>**Since:** 26.0.1 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) reqKey | Hydration request identifier.<br>**Since:** 26.0.1 |
