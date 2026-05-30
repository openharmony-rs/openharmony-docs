# os_account.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

## Overview

Defines the APIs for accessing and managing system account information.

**Library**: libos_account_ndk.so

**Header file**: <BasicServicesKit/os_account.h>

**System capability**: SystemCapability.Account.OsAccount

**Since**: 12

**Related module**: [OsAccount](capi-osaccount.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)](#oh_osaccount_getname) | Obtains the name of the system account, to which the caller process belongs.|
| [OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)](#oh_osaccount_getnamebylocalid) | Obtains the name of the target system account based on its local ID.|

## Function Description

### OH_OsAccount_GetName()

```c
OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)
```

**Description**

Obtains the name of the system account, to which the caller process belongs.

**System capability**: SystemCapability.Account.OsAccount

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char *buffer | Name character array. Its minimum length is the system account name plus the terminator (**\0**). Its maximum length is defined by **LOGIN_NAME_MAX**.|
| size_t buffer_size | Length of the system account name.|

**Returns**

| Type| Description|
| -- | -- |
| [OsAccount_ErrCode](capi-os-account-common-h.md#osaccount_errcode) | **OS_ACCOUNT_ERR_OK**: The operation is successful.<br>         **OS_ACCOUNT_ERR_INTERNAL_ERROR**: An internal error occurs.<br>         **OS_ACCOUNT_ERR_INVALID_PARAMETER**: The buffer is a null pointer, or the length of the system account name (excluding **\0**) is greater than or equal to the value of **buffer_size**.|

### OH_OsAccount_GetNameByLocalId()

```c
OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)
```

**Description**

Obtains the name of the target system account based on its local ID.

**Required permissions**: ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| int32_t localId | Local ID of the target system account.|
| char *name | Name character array, which must contain the system account name and terminator (**\0**). The maximum length is defined by **LOGIN_NAME_MAX** whose value is **256**.|
| size_t name_size | Length of the system account name.|

**Returns**

| Type| Description|
| -- | -- |
| [OsAccount_ErrCode](capi-os-account-common-h.md#osaccount_errcode) | **OS_ACCOUNT_ERR_OK**: The operation is successful.<br>         **OS_ACCOUNT_ERR_PERMISSION_DENIED**: Permission is denied.<br>         **OS_ACCOUNT_ERR_INTERNAL_ERROR**: An internal error occurs.<br>         **OS_ACCOUNT_ERR_INVALID_PARAMETER**: The name is null pointer or the length of the system account name (including **\0**) is greater than the value of **name_size**.<br>         **OS_ACCOUNT_ERR_ACCOUNT_NOT_FOUND**: The account is not found.<br>         **OS_ACCOUNT_ERR_RESTRICTED_ACCOUNT**: The account is restricted and cannot be queried.|
