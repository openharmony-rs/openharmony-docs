# OH_CloudDisk_CallbackContext

```c
typedef union OH_CloudDisk_CallbackContext {...} OH_CloudDisk_CallbackContext
```

## Overview

A union that encapsulates callback request context information.

<!--Device-union OH_CloudDisk_CallbackContext {...}--><!--Device-union OH_CloudDisk_CallbackContext {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) *fetchData | Fetch data request. It takes effect when callbackType is [OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *cancelFetchData | Cancel fetch data request. It takes effect when callbackType is [OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) *dehydrateData | Dehydrate authorization request. It takes effect when callbackType is [OH_CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.0.1 |
| [OH_CloudDisk_FetchRangeDataRequest](capi-clouddisk-oh-clouddisk-fetchrangedatarequest.md) *fetchRangeData | Fetch range data request. It takes effect when callbackType is [OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_RANGE_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype).<br>**Since**: 26.1.0 |


