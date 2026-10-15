# udmf_err_code.h

## Overview

Declares the error codes used in the UDMF.

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-udmf.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Udmf_ErrCode](#udmf_errcode) | Udmf_ErrCode | Enumerates the error codes. |
| [Udmf_ListenerStatus](#udmf_listenerstatus) | Udmf_ListenerStatus | Enumerates the status codes returned when data is obtained asynchronously. |

## Enum type description

### Udmf_ErrCode

```c
enum Udmf_ErrCode
```

**Description**

Enumerates the error codes.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| UDMF_E_OK = 0 | Operation successful.<br>**Since**: 12 |
| UDMF_ERR = 20400000 | Universal error codes.<br>**Since**: 12 |
| UDMF_E_INVALID_PARAM = (UDMF_ERR + 1) | Invalid parameter.<br>**Since**: 12 |

### Udmf_ListenerStatus

```c
enum Udmf_ListenerStatus
```

**Description**

Enumerates the status codes returned when data is obtained asynchronously.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 15

| Enum item | Description |
| -- | -- |
| UDMF_FINISHED = 0 | Data is obtained successfully.<br>**Since**: 15 |
| UDMF_PROCESSING | This task is being processed.<br>**Since**: 15 |
| UDMF_CANCELED | This task is canceled.<br>**Since**: 15 |
| UDMF_INNER_ERROR = 200 | An internal error occurs.<br>**Since**: 15 |
| UDMF_INVALID_PARAMETERS | Invalid parameters are contained.<br>**Since**: 15 |
| UDMF_DATA_NOT_FOUND | No data is obtained.<br>**Since**: 15 |
| UDMF_SYNC_FAILED | An error occurs during data synchronization.<br>**Since**: 15 |
| UDMF_COPY_FILE_FAILED | Failed to copy the file.<br>**Since**: 15 |


