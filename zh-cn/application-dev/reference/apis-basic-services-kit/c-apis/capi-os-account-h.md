# os_account.h

## 概述

声明访问和管理系统账号信息的API。

**库：** libos_account_ndk.so

**系统能力：** SystemCapability.Account.OsAccount

**起始版本：** 12

**相关模块：** [OsAccount](capi-osaccount.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)](#oh_osaccount_getname) | 获取调用方进程所属的系统账号的名称。 |
| [OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)](#oh_osaccount_getnamebylocalid) | 根据本地ID获取目标系统账号的名称。 |

## 函数说明

### OH_OsAccount_GetName()

```c
OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)
```

**描述**

获取调用方进程所属的系统账号的名称。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *buffer | 名称字符数组，其应具有能够存放名称和结束字符（'\0'）的空间，且最大长度为LOGIN_NAME_MAX。 |
| size_t buffer_size | 名称字符数组的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OsAccount_ErrCode](capi-os-account-common-h.md#osaccount_errcode) | <ul><br>         <li>[OS_ACCOUNT_ERR_OK](capi-os-account-common-h.md#osaccount_errcode) 操作成功。</li><br>         <li>[OS_ACCOUNT_ERR_INTERNAL_ERROR](capi-os-account-common-h.md#osaccount_errcode) 内部错误。</li><br>         <li>[OS_ACCOUNT_ERR_INVALID_PARAMETER](capi-os-account-common-h.md#osaccount_errcode) 表示buffer为空指针或名称长度（包括结束字符'\0'）大于buffer_size。</li><br>         </ul> |

### OH_OsAccount_GetNameByLocalId()

```c
OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)
```

**描述**

根据本地ID获取目标系统账号的名称。

**需要权限：** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t localId | 目标系统账号的本地ID。 |
| char *name | 名称字符数组，其应具有能够存放名称和结束字符（'\0'）的空间，最大长度为LOGIN_NAME_MAX。 |
| size_t name_size | 名称字符数组的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OsAccount_ErrCode](capi-os-account-common-h.md#osaccount_errcode) | <ul><br>         <li>[OS_ACCOUNT_ERR_OK](capi-os-account-common-h.md#osaccount_errcode) 操作成功。</li><br>         <li>[OS_ACCOUNT_ERR_PERMISSION_DENIED](capi-os-account-common-h.md#osaccount_errcode) 权限不足。</li><br>         <li>[OS_ACCOUNT_ERR_INTERNAL_ERROR](capi-os-account-common-h.md#osaccount_errcode) 内部错误。</li><br>         <li>[OS_ACCOUNT_ERR_INVALID_PARAMETER](capi-os-account-common-h.md#osaccount_errcode) name为空指针或名称长度（包括结束字符'\0'）大于name_size。</li><br>         <li>[OS_ACCOUNT_ERR_ACCOUNT_NOT_FOUND](capi-os-account-common-h.md#osaccount_errcode) 账号不存在。</li><br>         <li>[OS_ACCOUNT_ERR_RESTRICTED_ACCOUNT](capi-os-account-common-h.md#osaccount_errcode) 受限账号。</li><br>         </ul> |


