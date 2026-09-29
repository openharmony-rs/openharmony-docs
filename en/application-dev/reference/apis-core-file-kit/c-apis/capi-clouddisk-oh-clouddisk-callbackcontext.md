# OH_CloudDisk_CallbackContext

```c
union OH_CloudDisk_CallbackContext {...}
```

## Overview

A union that encapsulates callback request context information.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_CloudDisk_FetchDataRequest *fetchData | Fetch data request. It takes effect when callbackType is [CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| CloudDisk_PathInfo *cancelFetchData | Cancel fetch data request. It takes effect when callbackType is [CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| OH_CloudDisk_DehydrateInfo *dehydrateData | Dehydrate authorization request. It takes effect when callbackType is [CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| OH_CloudDisk_FetchRangeDataRequest *fetchRangeData | Fetch range data request. It takes effect when callbackType is [CLOUD_DISK_CALLBACK_TYPE_FETCH_RANGE_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.2.0 |


