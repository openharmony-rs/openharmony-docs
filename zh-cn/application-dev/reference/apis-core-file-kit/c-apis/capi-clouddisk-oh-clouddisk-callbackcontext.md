# OH_CloudDisk_CallbackContext

```c
union OH_CloudDisk_CallbackContext {...}
```

## 概述

回调请求上下文信息联合体。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_CloudDisk_FetchDataRequest *fetchData | 获取数据请求。当callbackType为[CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype)时生效。<br>**起始版本：** 26.0.1 |
| CloudDisk_PathInfo *cancelFetchData | 取消获取数据请求。当callbackType为[CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype)时生效。<br>**起始版本：** 26.0.1 |
| OH_CloudDisk_DehydrateInfo *dehydrateData | 脱水授权请求。当callbackType为[CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype)时生效。<br>**起始版本：** 26.0.1 |
| OH_CloudDisk_FetchRangeDataRequest *fetchRangeData | 获取范围数据请求。当callbackType为[CLOUD_DISK_CALLBACK_TYPE_FETCH_RANGE_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype)时生效。<br>**起始版本：** 26.2.0 |


