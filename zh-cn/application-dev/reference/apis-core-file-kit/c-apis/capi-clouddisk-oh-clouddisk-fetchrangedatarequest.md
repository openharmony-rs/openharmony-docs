# OH_CloudDisk_FetchRangeDataRequest

```c
struct OH_CloudDisk_FetchRangeDataRequest {...}
```

## 概述

获取范围数据请求信息。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.2.0

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | 同步根内相对文件路径。<br>**起始版本：** 26.2.0 |
| uint64_t offset | 获取范围数据的起始偏移，以字节为单位。<br>**起始版本：** 26.2.0 |
| uint64_t size | 获取范围数据的大小，以字节为单位。<br>**起始版本：** 26.2.0 |
| OH_CloudDisk_DataBuf *data | 需要读取的数据。<br>**起始版本：** 26.2.0 |


