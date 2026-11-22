# OH_CloudDisk_FetchDataRequest
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_FetchDataRequest {...} OH_CloudDisk_FetchDataRequest
```

## 概述

获取数据请求信息。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | 同步根内相对文件路径。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_HydratePriority](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_hydratepriority) priority | 水合优先级。<br>**起始版本：** 26.0.1 |
