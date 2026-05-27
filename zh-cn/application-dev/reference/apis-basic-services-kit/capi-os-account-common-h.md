# os_account_common.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

## 概述

提供OsAccount接口的公共类型定义。

**库：** libos_account_ndk.so

**引用文件：** <BasicServicesKit/os_account_common.h>

**系统能力：** SystemCapability.Account.OsAccount

**起始版本：** 12

**相关模块：** [OsAccount](capi-osaccount.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OsAccount_ErrCode](#osaccount_errcode) | OsAccount_ErrCode | 枚举错误码。 |

## 枚举类型说明

### OsAccount_ErrCode

```c
enum OsAccount_ErrCode
```

**描述**

枚举错误码。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OS_ACCOUNT_ERR_OK = 0 | 成功。 |
| OS_ACCOUNT_ERR_PERMISSION_DENIED = 201 |  没有权限。<br>**起始版本：** 26.0.0 |
| OS_ACCOUNT_ERR_INTERNAL_ERROR = 12300001 | 内部错误。 |
| OS_ACCOUNT_ERR_INVALID_PARAMETER = 12300002 | 无效的参数。 |
| OS_ACCOUNT_ERR_ACCOUNT_NOT_FOUND = 12300003 |  账号不存在。<br>**起始版本：** 26.0.0 |
| OS_ACCOUNT_ERR_RESTRICTED_ACCOUNT = 12300008 |  受限账号。<br>**起始版本：** 26.0.0 |


