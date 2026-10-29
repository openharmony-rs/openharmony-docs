# OH_CloudDisk_PlaceholderCustomInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_PlaceholderCustomInfo OH_CloudDisk_PlaceholderCustomInfo
```

## 概述

与占位符关联的不透明自定义信息。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t dataLength | 自定义信息的长度，单位为字节。<br>**起始版本：** 26.0.1 |
| const uint8_t *data | 指向自定义信息的指针。<br>**起始版本：** 26.0.1 |

