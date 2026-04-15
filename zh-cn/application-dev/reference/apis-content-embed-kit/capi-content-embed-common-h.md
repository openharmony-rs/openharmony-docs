# content_embed_common.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @wanxiaoguo-->
<!--Designer: @zhuwei;@weiguoning-->
<!--Tester: @yinjian-->
<!--Adviser: @jinqiuheng-->

## 概述

提供内容嵌入模块的错误码定义和嵌入文档支持能力的类型枚举描述。

**引用文件：** <ContentEmbedKit/content_embed/content_embed_common.h>

**库：** libcontent_embed_ndk.so

**系统能力：** SystemCapability.ContentEmbed.ObjectEditor

**起始版本：** 24

**相关模块：** [ContentEmbed](capi-contentembed.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ContentEmbed_ErrorCode](#contentembed_errorcode) | ContentEmbed_ErrorCode | 提供内容嵌入模块的错误码定义。 |
| [ContentEmbed_CapabilityCode](#contentembed_capabilitycode) | ContentEmbed_CapabilityCode | 嵌入文档对象支持的功能枚举，并支持通过位掩码组合多个能力值。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| MAX_OEID_LENGTH (1 * 40) | 表示被嵌入文档的标识符OEID的最大字符串长度。<br>**起始版本：** 24 |

## 枚举类型说明

### ContentEmbed_ErrorCode

```c
enum ContentEmbed_ErrorCode
```

**描述**

提供内容嵌入模块的错误码定义。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| CE_ERR_OK = 0 | 操作成功。<br>**起始版本：** 24 |
| CE_ERR_PARAM_INVALID = 401 | 参数不合法。<br>**起始版本：** 24 |
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | 当前设备不支持此功能。<br>**起始版本：** 24 |
| CE_ERR_NULL_POINTER = 35300001 | 返回空指针，可能是内存分配失败或内部错误。<br>**起始版本：** 24 |
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | 客户端未注册对应的回调函数。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_ERROR = 35300003 | OE Extension发生未知错误。<br>**起始版本：** 24 |
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | 系统服务出现异常，可能是服务未启动、连接中断或权限不足。<br>**起始版本：** 24 |
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | OE文档Storage对象相关操作失败。<br>**起始版本：** 24 |
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | OE文档Stream对象相关操作失败。<br>**起始版本：** 24 |
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | 文件操作失败，可能是文件不存在、权限不足、路径错误或磁盘空间不足。<br>**起始版本：** 24 |
| CE_ERR_IN_DLP_SANDBOX = 35300008 | 当前应用正在DLP沙箱环境中运行，暂不支持调用相关功能。<br>**起始版本：** 24 |
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | ImagePacker操作失败。<br>**起始版本：** 24 |
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | 客户端注册的回调函数在执行过程中发生异常。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | OE Extension意外退出。<br>**起始版本：** 24 |
| CE_ERR_INVALID_LINKING_PATH = 35300012 | 链接到不允许被链接目录中的文件，如应用沙箱目录内的文件。<br>**起始版本：** 24 |
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | 当前OE Extension连接超出限制。<br>**起始版本：** 24 |
| CE_ERR_FILE_NOT_GRANT = 35300014 | 当前文件未授权。<br>**起始版本：** 24 |
| CE_ERR_DISK_FULL = 35300015 | 当前磁盘空间不足。<br>**起始版本：** 24 |
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | 当前OE Extension不支持该能力。<br>**起始版本：** 24 |

### ContentEmbed_CapabilityCode

```c
enum ContentEmbed_CapabilityCode
```

**描述**

嵌入文档对象支持的功能枚举，并支持通过位掩码组合多个能力值。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0 | 表示支持获取OE文档的快照图像。<br>**起始版本：** 24 |
| CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1 | 表示支持对OE文档进行编辑操作。<br>**起始版本：** 24 |
