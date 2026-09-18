# oh_device_manager.h

## Overview

Provides APIs to obtain information about trusted devices and local devices.

**Library**: libdevicemanager_ndk.so

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Since**: 20

**Related module**: [DeviceManager](capi-devicemanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_DeviceManager_GetLocalDeviceName(char **localDeviceName, unsigned int &len)](#oh_devicemanager_getlocaldevicename) | Obtains the display name of the local device. The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name.(Deprecated in API26.0.0) |
| [int32_t OH_DeviceManager_GetLocalDeviceNameC(char **localDeviceName, unsigned int *len)](#oh_devicemanager_getlocaldevicenamec) | Obtains the display name of the local device. The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name. |

## Function description

### OH_DeviceManager_GetLocalDeviceName()

```c
int32_t OH_DeviceManager_GetLocalDeviceName(char **localDeviceName, unsigned int &len)
```

**Description**

Obtains the display name of the local device. The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name.

**Required permission**: ohos.permission.READ_LOCAL_DEVICE_NAME

**Since**: 20

**Deprecated**: 26.0.0

**Replaced by**: OH_DeviceManager_GetLocalDeviceNameC

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **localDeviceName | Pointer to the display name of the local device. After using this API, you need to manually release resources to free up space. If the application has the ohos.permission.READ_LOCAL_DEVICE_NAME permission, the device display name is returned. Otherwise, the default device name is returned. |
| len | Character length of the display name of the local device. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code. For details about the error code definitions, see {@link DeviceManager_ErrorCode}.<br>     Returns {@link ERR_OK} is returned if the execution is successful.<br>     Returns {@link DM_ERR_FAILED} is returned if the function fails to be executed.<br>     Returns {@link DM_ERR_OBTAIN_SERVICE} is returned if the device management service fails to be obtained.<br>     Returns {@link DM_ERR_OBTAIN_BUNDLE_NAME} is returned if the bundle name fails to be obtained.<br>     Returns {@link ERR_INVALID_PARAMETER} is returned if the localDeviceName is nullptr or                                              localDeviceName is not nullptr. |

### OH_DeviceManager_GetLocalDeviceNameC()

```c
int32_t OH_DeviceManager_GetLocalDeviceNameC(char **localDeviceName, unsigned int *len)
```

**Description**

Obtains the display name of the local device. The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name.

**Required permission**: ohos.permission.READ_LOCAL_DEVICE_NAME

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **localDeviceName | Pointer to the display name of the local device. After using this API, you need to manually release resources to free up space. If the application has the ohos.permission.READ_LOCAL_DEVICE_NAME permission, the device display name is returned. Otherwise, the default device name is returned. |
| unsigned int *len | Pointer to the length of the display name of the local device. After using this API, you need to manually release resources to free up space. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code. For details about the error code definitions, see {@link DeviceManager_ErrorCode}.<br>     Returns {@link ERR_OK} is returned if the execution is successful.<br>     Returns {@link DM_ERR_FAILED} is returned if the function fails to be executed.<br>     Returns {@link DM_ERR_OBTAIN_SERVICE} is returned if the device management service fails to be obtained.<br>     Returns {@link DM_ERR_OBTAIN_BUNDLE_NAME} is returned if the bundle name fails to be obtained.<br>     Returns {@link ERR_INVALID_PARAMETER} is returned if the localDeviceName is nullptr or                                              localDeviceName is not nullptr or len is nullptr. |


