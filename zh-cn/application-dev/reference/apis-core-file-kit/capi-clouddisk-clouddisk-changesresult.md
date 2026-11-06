# CloudDisk_ChangesResult
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct CloudDisk_ChangesResult {...} CloudDisk_ChangesResult
```

## 概述

查询同步根路径中文件变更的结果。该结构体包含同步根路径中文件的变更数据，包括下一次可查询的更新序列号、结尾标志以及变更数据项数组。适用于增量查询同步根路径中文件变更记录的场景。

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t nextUsn{0} | 下一次可查询的有效起始变更序列号。开发者可在下一次增量查询时使用该值继续获取后续变更。 |
| bool isEof{false} | 本次变更是否为同步根路径中记录的最后一批修改记录。true表示是最后一批修改记录，false表示不是最后一批修改记录。 |
| size_t bufferLength{0} | 历史变更记录数组中的元素数量，与changeDatas数组中的元素个数对应。 |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) changeDatas[] | 历史变更记录数组，数组长度由bufferLength指定。 |


