# OH_CloudDisk_CallbackContext
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef union OH_CloudDisk_CallbackContext {...} OH_CloudDisk_CallbackContext
```

## 概述

回调请求上下文信息联合体。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) *fetchData | 获取数据请求。当callbackType为OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA时生效。<br>**起始版本：** 26.0.1 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *cancelFetchData | 取消获取数据请求。当callbackType为OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA时生效。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) *dehydrateData | 脱水授权请求。当callbackType为OH_CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE时生效。<br>**起始版本：** 26.0.1 |
