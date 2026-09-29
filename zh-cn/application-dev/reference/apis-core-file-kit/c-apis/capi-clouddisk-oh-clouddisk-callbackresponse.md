# OH_CloudDisk_CallbackResponse

```c
union OH_CloudDisk_CallbackResponse {...}
```

## 概述

回调响应信息联合体。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| OH_CloudDisk_FetchData *fetchData | 获取数据响应。当callbackType为[OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype)时生效。<br>**起始版本：** 26.0.1 |


