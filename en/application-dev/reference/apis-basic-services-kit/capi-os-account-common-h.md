# os_account_common.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->

## Overview

Defines common types used in **OsAccount** APIs.

**Library**: libos_account_ndk.so

**Header file**: <BasicServicesKit/os_account_common.h>

**System capability**: SystemCapability.Account.OsAccount

**Since**: 12

**Related module**: [OsAccount](capi-osaccount.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OsAccount_ErrCode](#osaccount_errcode) | OsAccount_ErrCode | Enumerates the error codes.|

## Enum Description

### OsAccount_ErrCode

```c
enum OsAccount_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| OS_ACCOUNT_ERR_OK = 0 | Operation successful.|
| OS_ACCOUNT_ERR_PERMISSION_DENIED = 201 | No permission.<br>**Since**: 26.0.0|
| OS_ACCOUNT_ERR_INTERNAL_ERROR = 12300001 | Internal error.|
| OS_ACCOUNT_ERR_INVALID_PARAMETER = 12300002 | Invalid parameter.|
| OS_ACCOUNT_ERR_ACCOUNT_NOT_FOUND = 12300003 | Account not found.<br>**Since**: 26.0.0|
| OS_ACCOUNT_ERR_RESTRICTED_ACCOUNT = 12300008 | Restricted account.<br>**Since**: 26.0.0|
