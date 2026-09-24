# os_account.h

## Overview

Defines the APIs for accessing and managing OS account information.

**Library**: libos_account_ndk.so

**System capability**: SystemCapability.Account.OsAccount

**Since**: 12

**Related module**: [OsAccount](capi-osaccount.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| OS_ACCOUNT_H | Defines the APIs for accessing and managing OS account information.<br>**Since**: 12<br>**System capability**: SystemCapability.Account.OsAccount |

### Function

| Name | Description |
| -- | -- |
| [OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)](#oh_osaccount_getname) | Obtains the name of the OS account, to which the caller process belongs. |
| [OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)](#oh_osaccount_getnamebylocalid) | Obtains the name of the target OS account based on its local ID. |

## Function description

### OH_OsAccount_GetName()

```c
OsAccount_ErrCode OH_OsAccount_GetName(char *buffer, size_t buffer_size)
```

**Description**

Obtains the name of the OS account, to which the caller process belongs.

**System capability**: SystemCapability.Account.OsAccount

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *buffer | Character array of the OS account name, which must contain the OS account name and the null terminator ('\0'). The maximum length is defined by **LOGIN_NAME_MAX**. |
| size_t buffer_size | Size of the OS account name's character array. |

**Returns**:

| Type | Description |
| -- | -- |
| OsAccount_ErrCode | <ul>          <li>[OS_ACCOUNT_ERR_OK](capi-os-account-common-h.md#osaccount_errcode) The operation is successful.</li>          <li>[OS_ACCOUNT_ERR_INTERNAL_ERROR](capi-os-account-common-h.md#osaccount_errcode) An internal error occurs.</li>          <li>[OS_ACCOUNT_ERR_INVALID_PARAMETER](capi-os-account-common-h.md#osaccount_errcode) The buffer is a null pointer or the size of the OS account          name's character array (including \0) is greater than the value of buffer_size.</li>          </ul> |

### OH_OsAccount_GetNameByLocalId()

```c
OsAccount_ErrCode OH_OsAccount_GetNameByLocalId(int32_t localId, char *name, size_t name_size)
```

**Description**

Obtains the name of the target OS account based on its local ID.

**System capability**: SystemCapability.Account.OsAccount

**Required permission**: ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t localId | Local ID of the target OS account. |
| char *name | Character array of the OS account name, which must contain the OS account name and the null terminator ('\0'). The maximum length is defined by **LOGIN_NAME_MAX**. |
| size_t name_size | Size of the OS account name's character array. |

**Returns**:

| Type | Description |
| -- | -- |
| OsAccount_ErrCode | <ul>          <li>[OS_ACCOUNT_ERR_OK](capi-os-account-common-h.md#osaccount_errcode) The operation is successful.</li>          <li>[OS_ACCOUNT_ERR_PERMISSION_DENIED](capi-os-account-common-h.md#osaccount_errcode) Permission is denied.</li>          <li>[OS_ACCOUNT_ERR_INTERNAL_ERROR](capi-os-account-common-h.md#osaccount_errcode) An internal error occurs.</li>          <li>[OS_ACCOUNT_ERR_INVALID_PARAMETER](capi-os-account-common-h.md#osaccount_errcode) The name is a null pointer or the size of the OS account          name's character array (including \0) is greater than the value of name_size.</li>          <li>[OS_ACCOUNT_ERR_ACCOUNT_NOT_FOUND](capi-os-account-common-h.md#osaccount_errcode) The account is not found.</li>          <li>[OS_ACCOUNT_ERR_RESTRICTED_ACCOUNT](capi-os-account-common-h.md#osaccount_errcode) The account is restricted and cannot be queried.</li>          </ul> |


