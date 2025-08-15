# FileShare_PolicyInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--Designer: @chenxi0605; @JerryH1011-->
<!--Tester: @leiyuqian-->
<!--Adviser: @foryourself-->

## 概述

需要授予或使能权限URI的策略信息。

**起始版本：** 12

**相关模块：** [fileShare](capi-fileshare.md)

**所在头文件：** [oh_file_share.h](capi-oh-file-share-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *uri | 需要授予或使能权限的URI。 |
| unsigned int length | URI的字节长度。 |
| unsigned int operationMode | 授予或使能权限的URI访问模式。<br> 示例：FileShare_OperationMode.READ_MODE 、 FileShare_OperationMode.WRITE_MODE <br> 或者 FileShare_OperationMode.READ_MODE\|FileShare_OperationMode.WRITE_MODE。 |


