# OH_CloudDisk_CallbackResponse
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef union OH_CloudDisk_CallbackResponse {...} OH_CloudDisk_CallbackResponse
```

## 概述

回调响应信息联合体。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_CloudDisk_FetchData](capi-clouddisk-oh-clouddisk-fetchdata.md) *fetchData | 获取数据响应。当callbackType为OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA时生效。<br>**起始版本：** 26.0.1 |
