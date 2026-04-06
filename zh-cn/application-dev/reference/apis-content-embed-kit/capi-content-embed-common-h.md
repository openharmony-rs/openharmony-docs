# content_embed_common.h
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

提供ContentEmbed的错误码定义和嵌入文档支持能力的类型枚举描述。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_common.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ErrorCode](#contentembed_errorcode) | ContentEmbed_ErrorCode | 提供ContentEmbed的错误码定义。 |
| [ContentEmbed_CapabilityCode](#contentembed_capabilitycode) | ContentEmbed_CapabilityCode | 定义了嵌入文档支持能力的类型枚举描述，可以通过位掩码的方式组合多个能力值。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_OEID_LENGTH (1 * 40) | 表示OE文档的系统可识别标识符的最大字符串长度。<br>**起始版本：** 24 |

## 枚举类型说明

### ContentEmbed_ErrorCode

```c
enum ContentEmbed_ErrorCode
```

**描述**

提供ContentEmbed的错误码定义。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| CE_ERR_OK = 0 | 表示操作成功。<br>**起始版本：** 24 |
| CE_ERR_PARAM_INVALID = 401 | 表示参数不合法。<br>**起始版本：** 24 |
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | 当前设备不支持此功能。<br>**起始版本：** 24 |
| CE_ERR_NULL_POINTER = 35300001 | 表示在应该返回有效指针的情况下返回了空指针，可能是内存分配失败或内部错误。<br>**起始版本：** 24 |
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | 表示客户端尚未注册必要的回调函数。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_ERROR = 35300003 | 表示OE Extension发生未知错误。<br>**起始版本：** 24 |
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | 表示系统服务出现异常，可能是服务未启动、连接中断或权限不足。<br>**起始版本：** 24 |
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | 表示OE格式文件目录相关操作失败。<br>**起始版本：** 24 |
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | 表示OE格式文件流相关操作失败。<br>**起始版本：** 24 |
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | 表示文件操作失败，可能是文件不存在、权限不足、路径错误或磁盘空间不足。<br>**起始版本：** 24 |
| CE_ERR_IN_DLP_SANDBOX = 35300008 | 表示当前应用正在DLP沙箱环境中运行，暂不支持调用相关功能。<br>**起始版本：** 24 |
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | 表示ImagePacker操作失败。<br>**起始版本：** 24 |
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | 表示客户端注册的回调函数在执行过程中发生异常。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | 表示OE Extension意外退出，可能是崩溃、被系统杀死或资源耗尽。<br>**起始版本：** 24 |
| CE_ERR_INVALID_LINKING_PATH = 35300012 | 表示尝试链接到不允许被链接目录中的文件，如应用沙箱目录内的文件。<br>**起始版本：** 24 |
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | 表示当前OE Extension连接超出限制。<br>**起始版本：** 24 |
| CE_ERR_FILE_NOT_GRANT = 35300014 | 表示当前文件没有授权。<br>**起始版本：** 24 |
| CE_ERR_DISK_FULL = 35300015 | 表示当前磁盘空间不足。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | 表示当前OE Extension不支持该能力。<br>**起始版本：** 24 |

### ContentEmbed_CapabilityCode

```c
enum ContentEmbed_CapabilityCode
```

**描述**

定义了嵌入文档支持能力的类型枚举描述，可以通过位掩码的方式组合多个能力值。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0 | 表示支持获取OE文档的快照图像。<br>**起始版本：** 24 |
| CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1 | 表示支持对OE文档进行编辑操作。<br>**起始版本：** 24 |
