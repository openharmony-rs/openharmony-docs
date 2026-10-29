# OH_CloudDisk_DehydrateInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_DehydrateInfo {...} OH_CloudDisk_DehydrateInfo
```

## 概述

脱水授权信息。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | 同步根内相对文件路径。<br>**起始版本：** 26.0.1 |
| bool allow | 是否允许脱水。true表示允许对该文件执行脱水；false表示不允许脱水，应用应跳过该文件的脱水操作。<br>**起始版本：** 26.0.1 |
