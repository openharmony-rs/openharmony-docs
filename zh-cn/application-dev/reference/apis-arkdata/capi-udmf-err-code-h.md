# udmf_err_code.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 概述

声明统一数据管理框架错误码信息。

**引用文件：** <database/udmf/udmf_err_code.h>

**库：** libudmf.so

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 12

**相关模块：** [UDMF](capi-udmf.md)

## 汇总

### 枚举

| 名称                                        | typedef关键字       | 描述                         |
| ------------------------------------------- | ------------------- | ---------------------------- |
| [Udmf_ErrCode](#udmf_errcode)               | Udmf_ErrCode        | 错误码信息。                 |
| [Udmf_ListenerStatus](#udmf_listenerstatus) | Udmf_ListenerStatus | 异步获取数据时的状态码枚举。 |

## 枚举类型说明

### Udmf_ErrCode

```
enum Udmf_ErrCode
```

**描述**

错误码信息。

**起始版本：** 12

| 枚举项                                | 描述         |
| ------------------------------------- | ------------ |
| UDMF_E_OK = 0                         | 执行成功。   |
| UDMF_ERR = 20400000                   | 通用错误码。 |
| UDMF_E_INVALID_PARAM = (UDMF_ERR + 1) | 非法参数。   |

### Udmf_ListenerStatus

```
enum Udmf_ListenerStatus
```

**描述**

异步获取数据时的状态码枚举。

**起始版本：** 15

| 枚举项                  | 描述                         |
| ----------------------- | ---------------------------- |
| UDMF_FINISHED = 0       | 表示获取数据成功。           |
| UDMF_PROCESSING         | 表示正在处理中。             |
| UDMF_CANCELED           | 表示本次任务已被取消。       |
| UDMF_INNER_ERROR = 200  | 表示有内部错误发生。         |
| UDMF_INVALID_PARAMETERS | 表示包含无效参数。           |
| UDMF_DATA_NOT_FOUND     | 表示没有获取到数据。         |
| UDMF_SYNC_FAILED        | 表示同步数据过程中出现错误。 |
| UDMF_COPY_FILE_FAILED   | 表示文件拷贝过程中出现错误。 |

