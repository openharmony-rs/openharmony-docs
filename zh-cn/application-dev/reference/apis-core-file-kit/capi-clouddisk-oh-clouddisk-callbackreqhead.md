# OH_CloudDisk_CallbackReqHead
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_CallbackReqHead {...} OH_CloudDisk_CallbackReqHead
```

## 概述

云盘回调请求头信息。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_SyncFolderPath](capi-clouddisk-clouddisk-pathinfo.md) syncFolderPath | 回调请求所属同步根路径。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_CallbackType](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype) callbackType | 回调请求类型。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) reqKey | 水合请求标识。<br>**起始版本：** 26.0.1 |
