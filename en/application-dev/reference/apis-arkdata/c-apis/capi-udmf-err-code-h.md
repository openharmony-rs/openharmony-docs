# udmf_err_code.h

## Overview

Declares the error codes used in the UDMF.

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-arkdata-udmf.md)

## Summary

### Enums

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

<!--Device-enum Udmf_ErrCode--><!--Device-enum Udmf_ErrCode-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| UDMF_E_OK = 0 | Operation successful.<br>**Since**: 12<br><!--Device-UDMF_E_OK = 0--><!--Device-UDMF_E_OK = 0-End--> |
| UDMF_ERR = 20400000 | Universal error codes.<br>**Since**: 12<br><!--Device-UDMF_ERR = 20400000--><!--Device-UDMF_ERR = 20400000-End--> |
| UDMF_E_INVALID_PARAM = (UDMF_ERR + 1) | Invalid parameter.<br>**Since**: 12<br><!--Device-UDMF_E_INVALID_PARAM = (UDMF_ERR + 1)--><!--Device-UDMF_E_INVALID_PARAM = (UDMF_ERR + 1)-End--> |

### Udmf_ListenerStatus

```c
enum Udmf_ListenerStatus
```

**Description**

Enumerates the status codes returned when data is obtained asynchronously.

<!--Device-enum Udmf_ListenerStatus--><!--Device-enum Udmf_ListenerStatus-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 15

| Enum item | Description |
| -- | -- |
| UDMF_FINISHED = 0 | Data is obtained successfully.<br>**Since**: 15<br><!--Device-UDMF_FINISHED = 0--><!--Device-UDMF_FINISHED = 0-End--> |
| UDMF_PROCESSING | This task is being processed.<br>**Since**: 15<br><!--Device-UDMF_PROCESSING--><!--Device-UDMF_PROCESSING-End--> |
| UDMF_CANCELED | This task is canceled.<br>**Since**: 15<br><!--Device-UDMF_CANCELED--><!--Device-UDMF_CANCELED-End--> |
| UDMF_INNER_ERROR = 200 | An internal error occurs.<br>**Since**: 15<br><!--Device-UDMF_INNER_ERROR = 200--><!--Device-UDMF_INNER_ERROR = 200-End--> |
| UDMF_INVALID_PARAMETERS | Invalid parameters are contained.<br>**Since**: 15<br><!--Device-UDMF_INVALID_PARAMETERS--><!--Device-UDMF_INVALID_PARAMETERS-End--> |
| UDMF_DATA_NOT_FOUND | No data is obtained.<br>**Since**: 15<br><!--Device-UDMF_DATA_NOT_FOUND--><!--Device-UDMF_DATA_NOT_FOUND-End--> |
| UDMF_SYNC_FAILED | An error occurs during data synchronization.<br>**Since**: 15<br><!--Device-UDMF_SYNC_FAILED--><!--Device-UDMF_SYNC_FAILED-End--> |
| UDMF_COPY_FILE_FAILED | Failed to copy the file.<br>**Since**: 15<br><!--Device-UDMF_COPY_FILE_FAILED--><!--Device-UDMF_COPY_FILE_FAILED-End--> |


