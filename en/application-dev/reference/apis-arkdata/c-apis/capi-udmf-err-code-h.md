# udmf_err_code.h

## Overview

Declaration error code information.

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-udmf.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Udmf_ErrCode](#udmf_errcode) | Udmf_ErrCode | Indicates the error code information. |
| [Udmf_ListenerStatus](#udmf_listenerstatus) | Udmf_ListenerStatus | Indicates the error code information. |

## Enum type description

### Udmf_ErrCode

```c
enum Udmf_ErrCode
```

**Description**

Indicates the error code information.

**Since**: 12

| Enum item | Description |
| -- | -- |
| UDMF_E_OK = 0 | The error code in the correct case. |
| UDMF_ERR = 20400000 | The error code for common exceptions. |
| UDMF_E_INVALID_PARAM = (UDMF_ERR + 1) | The error code for common invalid args. |

### Udmf_ListenerStatus

```c
enum Udmf_ListenerStatus
```

**Description**

Indicates the error code information.

**Since**: 15

| Enum item | Description |
| -- | -- |
| UDMF_FINISHED = 0 | brief Indicates the finished status. |
| UDMF_PROCESSING | Indicates that processing is still in progress. |
| UDMF_CANCELED | Indicates that the process has been canceled. |
| UDMF_INNER_ERROR = 200 | Indicates that an internal error has occurred. |
| UDMF_INVALID_PARAMETERS | Indicates that the GetDataParams contains invalid parameters. |
| UDMF_DATA_NOT_FOUND | Indicates that no data is obtained. |
| UDMF_SYNC_FAILED | Indicates that an error occurred in the synchronization process. |
| UDMF_COPY_FILE_FAILED | Indicates that an error occurred during file copying. |


