# native_drm_err.h

## Overview

The file declares the DRM error codes.

**Library**: libnative_drm.so

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Drm_ErrCode](#drm_errcode) | Drm_ErrCode | Enumerates the DRM error codes. |

## Enum type description

### Drm_ErrCode

```c
enum Drm_ErrCode
```

**Description**

Enumerates the DRM error codes.

<!--Device-enum Drm_ErrCode--><!--Device-enum Drm_ErrCode-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| DRM_ERR_OK = 0 | Operation successful.<br><!--Device-DRM_ERR_OK = 0--><!--Device-DRM_ERR_OK = 0-End--> |
| DRM_CAPI_ERR_BASE = 24700500 | Base error code.<br><!--Device-DRM_CAPI_ERR_BASE = 24700500--><!--Device-DRM_CAPI_ERR_BASE = 24700500-End--> |
| DRM_ERR_NO_MEMORY = DRM_CAPI_ERR_BASE + 1 | Insufficient memory.<br><!--Device-DRM_ERR_NO_MEMORY = DRM_CAPI_ERR_BASE + 1--><!--Device-DRM_ERR_NO_MEMORY = DRM_CAPI_ERR_BASE + 1-End--> |
| DRM_ERR_OPERATION_NOT_PERMITTED = DRM_CAPI_ERR_BASE + 2 | Operation not permitted.<br><!--Device-DRM_ERR_OPERATION_NOT_PERMITTED = DRM_CAPI_ERR_BASE + 2--><!--Device-DRM_ERR_OPERATION_NOT_PERMITTED = DRM_CAPI_ERR_BASE + 2-End--> |
| DRM_ERR_INVALID_VAL = DRM_CAPI_ERR_BASE + 3 | Invalid parameter.<br><!--Device-DRM_ERR_INVALID_VAL = DRM_CAPI_ERR_BASE + 3--><!--Device-DRM_ERR_INVALID_VAL = DRM_CAPI_ERR_BASE + 3-End--> |
| DRM_ERR_IO = DRM_CAPI_ERR_BASE + 4 | I/O error.<br><!--Device-DRM_ERR_IO = DRM_CAPI_ERR_BASE + 4--><!--Device-DRM_ERR_IO = DRM_CAPI_ERR_BASE + 4-End--> |
| DRM_ERR_TIMEOUT = DRM_CAPI_ERR_BASE + 5 | Network timeout.<br><!--Device-DRM_ERR_TIMEOUT = DRM_CAPI_ERR_BASE + 5--><!--Device-DRM_ERR_TIMEOUT = DRM_CAPI_ERR_BASE + 5-End--> |
| DRM_ERR_UNKNOWN = DRM_CAPI_ERR_BASE + 6 | Unknown error.<br><!--Device-DRM_ERR_UNKNOWN = DRM_CAPI_ERR_BASE + 6--><!--Device-DRM_ERR_UNKNOWN = DRM_CAPI_ERR_BASE + 6-End--> |
| DRM_ERR_SERVICE_DIED = DRM_CAPI_ERR_BASE + 7 | DRM service unavailable.<br><!--Device-DRM_ERR_SERVICE_DIED = DRM_CAPI_ERR_BASE + 7--><!--Device-DRM_ERR_SERVICE_DIED = DRM_CAPI_ERR_BASE + 7-End--> |
| DRM_ERR_INVALID_STATE = DRM_CAPI_ERR_BASE + 8 | Invalid operation state.<br><!--Device-DRM_ERR_INVALID_STATE = DRM_CAPI_ERR_BASE + 8--><!--Device-DRM_ERR_INVALID_STATE = DRM_CAPI_ERR_BASE + 8-End--> |
| DRM_ERR_UNSUPPORTED = DRM_CAPI_ERR_BASE + 9 | Unsupported operation.<br><!--Device-DRM_ERR_UNSUPPORTED = DRM_CAPI_ERR_BASE + 9--><!--Device-DRM_ERR_UNSUPPORTED = DRM_CAPI_ERR_BASE + 9-End--> |
| DRM_ERR_MAX_SYSTEM_NUM_REACHED = DRM_CAPI_ERR_BASE + 10 | Too many MediaKeySystem instances.<br><!--Device-DRM_ERR_MAX_SYSTEM_NUM_REACHED = DRM_CAPI_ERR_BASE + 10--><!--Device-DRM_ERR_MAX_SYSTEM_NUM_REACHED = DRM_CAPI_ERR_BASE + 10-End--> |
| DRM_ERR_MAX_SESSION_NUM_REACHED = DRM_CAPI_ERR_BASE + 11 | Too many MediaKeySession instances.<br><!--Device-DRM_ERR_MAX_SESSION_NUM_REACHED = DRM_CAPI_ERR_BASE + 11--><!--Device-DRM_ERR_MAX_SESSION_NUM_REACHED = DRM_CAPI_ERR_BASE + 11-End--> |
| DRM_ERR_EXTEND_START = DRM_CAPI_ERR_BASE + 100 | Extended error codes start.<br><!--Device-DRM_ERR_EXTEND_START = DRM_CAPI_ERR_BASE + 100--><!--Device-DRM_ERR_EXTEND_START = DRM_CAPI_ERR_BASE + 100-End--> |


