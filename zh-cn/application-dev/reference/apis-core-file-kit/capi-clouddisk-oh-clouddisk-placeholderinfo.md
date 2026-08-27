# OH_CloudDisk_PlaceholderInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_PlaceholderInfo {...} OH_CloudDisk_PlaceholderInfo
```

## 概述

占位符相关操作使用的文件元数据信息。

**起始版本：** 26.1.0

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t logicalSize | 占位符文件的逻辑大小，表示其对应云端文件的大小，单位为字节。<br>**起始版本：** 26.1.0 |
| uint64_t atimeMs | 占位符文件对应云端文件的创建时间，单位为毫秒。<br>**起始版本：** 26.1.0 |
| uint64_t mtimeMs | 占位符文件对应云端文件的最后一次修改时间，单位为毫秒。<br>**起始版本：** 26.1.0 |
