# CloudDisk_DisplayNameInfo

```c
typedef struct CloudDisk_DisplayNameInfo {...} CloudDisk_DisplayNameInfo
```

## 概述

定义同步根路径的显示名称信息。

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t displayNameResId | 应用同步根路径显示名称对应的静态资源ID。<br>**起始版本：** 21 |
| char *customAlias |  |
| size_t customAliasLength | 自定义别名的长度，范围：[0, 255]。<br>**起始版本：** 21 |


