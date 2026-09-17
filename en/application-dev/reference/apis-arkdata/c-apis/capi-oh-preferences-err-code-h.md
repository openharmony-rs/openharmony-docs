# oh_preferences_err_code.h

## Overview

Defines the error codes used in the **Preferences** module.

**Library**: libohpreferences.so

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Related module**: [Preferences](capi-preferences.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Preferences_ErrCode](#oh_preferences_errcode) | OH_Preferences_ErrCode | Enumerates the error codes. |

## Enum type description

### OH_Preferences_ErrCode

```c
enum OH_Preferences_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 13

| Enum item | Description |
| -- | -- |
| PREFERENCES_OK = 0 | The operation is successful. |
| PREFERENCES_ERROR_INVALID_PARAM = 401 | @error Invalid args. |
| PREFERENCES_ERROR_NOT_SUPPORTED = 801 | @error Capability not supported. |
| PREFERENCES_ERROR_BASE = 15500000 | @error Base error code. |
| PREFERENCES_ERROR_DELETE_FILE = 15500010 | @error Failed to delete a file. |
| PREFERENCES_ERROR_STORAGE = 15500011 | @error Storage error. |
| PREFERENCES_ERROR_MALLOC = 15500012 | @error Failed to malloc memory. |
| PREFERENCES_ERROR_KEY_NOT_FOUND = 15500013 | @error Key not found error. |
| PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT = 15500019 | @error Failed to get DataObsMgrClient. |


