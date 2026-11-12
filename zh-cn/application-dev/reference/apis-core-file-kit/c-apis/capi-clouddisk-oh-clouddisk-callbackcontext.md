# OH_CloudDisk_CallbackContext

```c
typedef union OH_CloudDisk_CallbackContext {...} OH_CloudDisk_CallbackContext
```

## 概述

回调请求上下文信息联合体。

<!--Device-union OH_CloudDisk_CallbackContext {...}--><!--Device-union OH_CloudDisk_CallbackContext {...}-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-core-file-kit-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) *fetchData | 获取数据请求。当callbackType为CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA时生效。<br>**起始版本：** 26.0.1 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *cancelFetchData | 取消获取数据请求。当callbackType为CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA时生效。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) *dehydrateData | 脱水授权请求。当callbackType为CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE时生效。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_FetchRangeDataRequest](capi-clouddisk-oh-clouddisk-fetchrangedatarequest.md) *fetchRangeData | 获取范围数据请求。当callbackType为CLOUD_DISK_CALLBACK_TYPE_FETCH_RANGE_DATA时生效。<br>**起始版本：** 26.1.0 |


