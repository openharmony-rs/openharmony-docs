# OH_CloudDisk_PlaceholderInfo

```c
typedef struct OH_CloudDisk_PlaceholderInfo {...} OH_CloudDisk_PlaceholderInfo
```

## 概述

占位符文件的元数据信息。

**起始版本：** 26.1.0

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t logicalSize | 占位符文件的逻辑大小，以字节为单位，反映云文件的实际大小。<br>**起始版本：** 26.1.0 |
| uint64_t atimeMs | 占位文件的创建时间，对应文件在云端创建的实际时间。<br>**起始版本：** 26.1.0 |
| uint64_t mtimeMs | 占位文件的修改时间，反映云侧文件的实际修改时间。<br>**起始版本：** 26.1.0 |


