# oh_device_manager.h
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @liwei_hw-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=4439eda4ac1d25ec7653da252cc3d30bbfe19410 translatedAt=2026-11-03T12:57:41.261Z pushedAt=2026-11-04T08:47:59.640Z nl=1 -->

## Overview

Provides APIs to obtain information about trusted devices and local devices.

**File to include**: <distributedhardware/device_manager/oh_device_manager.h>

**Library**: libdevicemanager_ndk.so

**System capability**: SystemCapability.DistributedHardware.DeviceManager

**Since**: 20

**Related module**: [DeviceManager](capi-devicemanager.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [int32_t OH_DeviceManager_GetLocalDeviceName(char **localDeviceName, unsigned int &len)](#oh_devicemanager_getlocaldevicename) | Obtains the display name of the local device.<br>The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name.|
| [int32_t OH_DeviceManager_GetLocalDeviceNameC(char **localDeviceName, unsigned int *len)](#oh_devicemanager_getlocaldevicenamec) | Obtains the local device display name.<br> The device display name involves the user's privacy data. The app is required to provide a privacy statement to declare the purpose of the device display name. |

## Function Description

### OH_DeviceManager_GetLocalDeviceName()

```c
int32_t OH_DeviceManager_GetLocalDeviceName(char **localDeviceName, unsigned int &len)
```

**Description**

Obtains the local device display name.<br> The device display name involves the user's privacy data. The app is required to provide a privacy statement to declare the purpose of the device display name.

**Required permissions**: ohos.permission.READ_LOCAL_DEVICE_NAME

**Since**: 20

**Deprecated since:** 26.0.0

**Substitute API:** [OH_DeviceManager_GetLocalDeviceNameC](#oh_devicemanager_getlocaldevicenamec)

**Parameters**

| Parameter| Description|
| -- | -- |
| char **localDeviceName | Pointer to the name string of the local device display name. You need to manually release the space resources after use. If the app has the **ohos.permission.READ_LOCAL_DEVICE_NAME** permission, the device display name is returned; otherwise, the default device name is returned. |
| unsigned int &len | Length of the name string of the local device display name, in bytes. |

**Return value**

| Type | Description |
| -- | -- |
| int32_t | Result code. For details about the error codes, see [DeviceManager_ErrorCode](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode).<br>         Returns [ERR_OK](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the operation is successful.<br>         Returns [DM_ERR_FAILED](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the function fails to execute.<br>         Returns [DM_ERR_OBTAIN_SERVICE](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the device management service fails to be obtained.<br>         Returns [DM_ERR_OBTAIN_BUNDLE_NAME](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if **bundleName** fails to be obtained.<br>         Returns [ERR_INVALID_PARAMETER](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the parameter **localDeviceName** is a null pointer or *localDeviceName is a non-null pointer. |

### OH_DeviceManager_GetLocalDeviceNameC()

```c
int32_t OH_DeviceManager_GetLocalDeviceNameC(char **localDeviceName, unsigned int *len)
```

**Description**

Obtains the local device display name.<br> The device display name involves the user's privacy data. The app is required to provide a privacy statement to declare the purpose of the device display name.

**Required permissions**: ohos.permission.READ_LOCAL_DEVICE_NAME

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| char **localDeviceName | Pointer to the name string of the local device display name. You need to manually release the space resources after use. If the app has the **ohos.permission.READ_LOCAL_DEVICE_NAME** permission, the device display name is returned; otherwise, the default device name is returned. |
| unsigned int *len | Pointer to the address of the length of the local device display name string. You need to manually release the space resources after use. Unit: byte. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code. For details about the error codes, see [DeviceManager_ErrorCode](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode).<br>         Returns [ERR_OK](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the operation is successful.<br>         Returns [DM_ERR_FAILED](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the function fails to execute.<br>         Returns [DM_ERR_OBTAIN_SERVICE](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if obtaining the device management service fails.<br>         Returns [DM_ERR_OBTAIN_BUNDLE_NAME](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if **bundleName** fails to be obtained.<br>         Returns [ERR_INVALID_PARAMETER](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) if the parameter **localDeviceName** is a null pointer, *localDeviceName is a non-null pointer, or **len** is a null pointer. |