# oh_device_manager_err_code.h

## Overview

Declares the error codes of the distributed device management module.

**Library**: libdevicemanager_ndk.so

**Since**: 20

**Related module**: [DeviceManager](capi-devicemanager.md)

## Summary

### Enum

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

**Since**: 20

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | Operation success.<br>**Since**: 20 |
| ERR_PERMISSION_ERROR = 201 | Permission verification failed.<br>**Since**: 20 |
| ERR_INVALID_PARAMETER = 401 | Invalid parameter.<br>**Since**: 20 |
| DM_ERR_FAILED = 11600101 | Function execution failed.<br>**Since**: 20 |
| DM_ERR_OBTAIN_SERVICE = 11600102 | Failed to obtain the device management service.<br>**Since**: 20 |
| DM_ERR_OBTAIN_BUNDLE_NAME = 11600109 | Failed to obtain the bundle name.<br>**Since**: 20 |


