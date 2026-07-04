# FileShare_PolicyInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--Designer: @chenxi0605; @JerryH1011-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct FileShare_PolicyInfo {...} FileShare_PolicyInfo
```

## 概述

需要授予或激活URI访问权限的策略信息。

**起始版本：** 12

**相关模块：** [fileShare](capi-fileshare.md)

**所在头文件：** [oh_file_share.h](capi-oh-file-share-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *uri | 需要授予或激活访问权限的URI。 |
| unsigned int length | uri指向字符串的字节长度，不包含字符串结束符'\0'。 |
| unsigned int operationMode | 授予或激活权限的URI访问模式。READ_MODE表示读取权限，WRITE_MODE表示写入权限。<br>示例：FileShare_OperationMode.READ_MODE、FileShare_OperationMode.WRITE_MODE，或者FileShare_OperationMode.READ_MODE\|FileShare_OperationMode.WRITE_MODE。 |

