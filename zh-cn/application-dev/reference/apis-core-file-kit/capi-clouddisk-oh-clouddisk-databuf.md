# OH_CloudDisk_DataBuf
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_DataBuf {...} OH_CloudDisk_DataBuf
```

## 概述

云盘数据缓冲区信息。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t *data | 数据缓冲区指针。<br>**起始版本：** 26.0.1 |
| uint64_t dataSize | 数据缓冲区大小，以字节为单位。<br>**起始版本：** 26.0.1 |
