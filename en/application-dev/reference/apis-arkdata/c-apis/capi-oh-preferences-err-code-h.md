# oh_preferences_err_code.h

## Overview

Defines the error codes used in the **Preferences** module.

**Library**: libohpreferences.so

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

**Related module**: [Preferences](capi-arkdata-preferences.md)

## Summary

### Enums

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

<!--Device-OH_Preferences_ErrCode--><!--Device-OH_Preferences_ErrCode-End-->

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| PREFERENCES_OK = 0 | The operation is successful. |
| PREFERENCES_ERROR_INVALID_PARAM = 401 | &nbsp;Invalid args. |
| PREFERENCES_ERROR_NOT_SUPPORTED = 801 | &nbsp;Capability not supported. |
| PREFERENCES_ERROR_BASE = 15500000 | &nbsp;Base error code. |
| PREFERENCES_ERROR_DELETE_FILE = 15500010 | &nbsp;Failed to delete a file. |
| PREFERENCES_ERROR_STORAGE = 15500011 | &nbsp;Storage error. |
| PREFERENCES_ERROR_MALLOC = 15500012 | &nbsp;Failed to malloc memory. |
| PREFERENCES_ERROR_KEY_NOT_FOUND = 15500013 | &nbsp;Key not found error. |
| PREFERENCES_ERROR_GET_DATAOBSMGRCLIENT = 15500019 | &nbsp;Failed to get DataObsMgrClient. |


