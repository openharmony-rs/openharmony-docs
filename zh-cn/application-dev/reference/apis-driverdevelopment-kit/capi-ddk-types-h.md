# ddk_types.h
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## 概述

提供基础DDK接口所使用的Base DDK类型，宏定义，枚举值和数据结构。

**引用文件：** <ddk/ddk_types.h>

**库：** libddk_base.z.so

**系统能力：** SystemCapability.Driver.DDK.Extension

**起始版本：** 12

**相关模块：** [BaseDdk](capi-baseddk.md)

## 汇总

### 结构体

| 名称                                       | typedef关键字 | 描述 |
|------------------------------------------| -- | -- |
| [DDK_Ashmem](capi-baseddk-ddk-ashmem.md) | DDK_Ashmem | 定义通过接口<b>OH_DDK_CreateAshmem</b>创建的共享内存，共享内存的缓冲区提供更好的性能。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [DDK_RetCode](#ddk_retcode) | DDK_RetCode | 枚举基本DDK中使用的错误代码。 |

## 枚举类型说明

### DDK_RetCode

```
enum DDK_RetCode
```

**描述**

枚举基本DDK中使用的错误代码。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DDK_SUCCESS = 0 | 操作成功 |
| DDK_FAILURE = 28600001 | 操作失败 |
| DDK_INVALID_PARAMETER = 28600002 | 无效参数 |
| DDK_INVALID_OPERATION = 28600003 | 无效操作 |
| DDK_NULL_PTR = 28600004 | 空指针异常 |


