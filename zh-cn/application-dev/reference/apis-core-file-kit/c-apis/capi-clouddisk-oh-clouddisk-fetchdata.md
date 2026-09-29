# OH_CloudDisk_FetchData

```c
struct OH_CloudDisk_FetchData {...}
```

## 概述

云端文件数据获取结果。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t offset | 本次数据在文件中的起始偏移，以字节为单位。<br>**起始版本：** 26.0.1 |
| uint64_t size | 本次下载数据长度，以字节为单位。<br>**起始版本：** 26.0.1 |
| uint64_t totalSize | 云端文件总大小，以字节为单位。<br>**起始版本：** 26.0.1 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) data | 文件数据缓冲区。<br>**起始版本：** 26.0.1 |
| bool isComplete | 是否是最后一块数据。<br>**起始版本：** 26.0.1 |


