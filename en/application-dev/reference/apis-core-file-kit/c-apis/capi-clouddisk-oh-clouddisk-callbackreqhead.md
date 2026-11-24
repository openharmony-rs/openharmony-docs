# OH_CloudDisk_CallbackReqHead

```c
typedef struct OH_CloudDisk_CallbackReqHead {...} OH_CloudDisk_CallbackReqHead
```

## Overview

A struct that encapsulates the cloud disk callback request header.

<!--Device-struct OH_CloudDisk_CallbackReqHead {...}--><!--Device-struct OH_CloudDisk_CallbackReqHead {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| CloudDisk_SyncFolderPath syncFolderPath | Sync root path of the callback request.<br>**Since**: 26.0.1<br><!--Device-CloudDisk_SyncFolderPath syncFolderPath--><!--Device-CloudDisk_SyncFolderPath syncFolderPath-End--> |
| [OH_CloudDisk_CallbackType](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype) callbackType | Callback request type.<br>**Since**: 26.0.1<br><!--Device-OH_CloudDisk_CallbackType callbackType--><!--Device-OH_CloudDisk_CallbackType callbackType-End--> |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) reqKey | Opaque request key.<br>**Since**: 26.0.1<br><!--Device-OH_CloudDisk_DataBuf reqKey--><!--Device-OH_CloudDisk_DataBuf reqKey-End--> |


