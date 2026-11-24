# udmf_err_code.h

## 概述

声明统一数据管理框架错误码定义和错误描述信息。

**库：** libudmf.so

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 12

**相关模块：** [UDMF](capi-arkdata-udmf.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Udmf_ErrCode](#udmf_errcode) | Udmf_ErrCode | 错误码信息。 |
| [Udmf_ListenerStatus](#udmf_listenerstatus) | Udmf_ListenerStatus | 异步获取数据时的状态码枚举。 |

## 枚举类型说明

### Udmf_ErrCode

```c
enum Udmf_ErrCode
```

**描述：**

错误码信息。

<!--Device-enum Udmf_ErrCode--><!--Device-enum Udmf_ErrCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| UDMF_E_OK = 0 | 执行成功。<br><!--Device-UDMF_E_OK = 0--><!--Device-UDMF_E_OK = 0-End--> |
| UDMF_ERR = 20400000 | 通用错误码。<br><!--Device-UDMF_ERR = 20400000--><!--Device-UDMF_ERR = 20400000-End--> |
| UDMF_E_INVALID_PARAM = (UDMF_ERR + 1) | 非法参数。<br><!--Device-UDMF_E_INVALID_PARAM = (UDMF_ERR + 1)--><!--Device-UDMF_E_INVALID_PARAM = (UDMF_ERR + 1)-End--> |

### Udmf_ListenerStatus

```c
enum Udmf_ListenerStatus
```

**描述：**

异步获取数据时的状态码枚举。

<!--Device-enum Udmf_ListenerStatus--><!--Device-enum Udmf_ListenerStatus-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| UDMF_FINISHED = 0 | 表示获取数据成功。<br><!--Device-UDMF_FINISHED = 0--><!--Device-UDMF_FINISHED = 0-End--> |
| UDMF_PROCESSING | 表示正在处理中。<br><!--Device-UDMF_PROCESSING--><!--Device-UDMF_PROCESSING-End--> |
| UDMF_CANCELED | 表示本次任务已被取消。<br><!--Device-UDMF_CANCELED--><!--Device-UDMF_CANCELED-End--> |
| UDMF_INNER_ERROR = 200 | 表示有内部错误发生。<br><!--Device-UDMF_INNER_ERROR = 200--><!--Device-UDMF_INNER_ERROR = 200-End--> |
| UDMF_INVALID_PARAMETERS | 表示包含无效参数。<br><!--Device-UDMF_INVALID_PARAMETERS--><!--Device-UDMF_INVALID_PARAMETERS-End--> |
| UDMF_DATA_NOT_FOUND | 表示没有获取到数据。<br><!--Device-UDMF_DATA_NOT_FOUND--><!--Device-UDMF_DATA_NOT_FOUND-End--> |
| UDMF_SYNC_FAILED | 表示同步数据过程中出现错误。<br><!--Device-UDMF_SYNC_FAILED--><!--Device-UDMF_SYNC_FAILED-End--> |
| UDMF_COPY_FILE_FAILED | 表示文件拷贝过程中出现错误。<br><!--Device-UDMF_COPY_FILE_FAILED--><!--Device-UDMF_COPY_FILE_FAILED-End--> |


