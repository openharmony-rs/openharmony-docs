# oh_device_manager_err_code.h

## Overview

Declares the error codes of the distributed device management module.

**File to Include**: <distributedhardware/device_manager/oh_device_manager_err_code.h>

**Library**: libdevicemanager_ndk.so

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Since**: 20

**Related module**: [DeviceManager](capi-distributed-service-kit-devicemanager.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DeviceManager_ErrorCode](#devicemanager_errorcode) | DeviceManager_ErrorCode | Error codes of the distributed device management module. |

## Enum type description

### DeviceManager_ErrorCode

```c
enum DeviceManager_ErrorCode
```

**Description**

Error codes of the distributed device management module.

<!--Device-enum DeviceManager_ErrorCode--><!--Device-enum DeviceManager_ErrorCode-End-->

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | Operation success.<br>**Since**: 20<br><!--Device-ERR_OK = 0--><!--Device-ERR_OK = 0-End--> |
| ERR_PERMISSION_ERROR = 201 | Permission verification failed.<br>**Since**: 20<br><!--Device-ERR_PERMISSION_ERROR = 201--><!--Device-ERR_PERMISSION_ERROR = 201-End--> |
| ERR_INVALID_PARAMETER = 401 | Invalid parameter.<br>**Since**: 20<br><!--Device-ERR_INVALID_PARAMETER = 401--><!--Device-ERR_INVALID_PARAMETER = 401-End--> |
| DM_ERR_FAILED = 11600101 | Function execution failed.<br>**Since**: 20<br><!--Device-DM_ERR_FAILED = 11600101--><!--Device-DM_ERR_FAILED = 11600101-End--> |
| DM_ERR_OBTAIN_SERVICE = 11600102 | Failed to obtain the device management service.<br>**Since**: 20<br><!--Device-DM_ERR_OBTAIN_SERVICE = 11600102--><!--Device-DM_ERR_OBTAIN_SERVICE = 11600102-End--> |
| DM_ERR_OBTAIN_BUNDLE_NAME = 11600109 | Failed to obtain the bundle name.<br>**Since**: 20<br><!--Device-DM_ERR_OBTAIN_BUNDLE_NAME = 11600109--><!--Device-DM_ERR_OBTAIN_BUNDLE_NAME = 11600109-End--> |


