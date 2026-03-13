# oh_device_manager.h
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao;@huangkai71-->
<!--Designer: @gsxiaowen;@lee_jet520-->
<!--Tester: @hanjiawei;@Ytt-test-->
<!--Adviser: @hu-zhiqiong-->

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

## Function Description

### OH_DeviceManager_GetLocalDeviceName()

```c
int32_t OH_DeviceManager_GetLocalDeviceName(char **localDeviceName, unsigned int &len)
```

**Description**

Obtains the display name of the local device.<br>The device display name involves user privacy. You need to provide a privacy statement to declare the purpose of the device display name.

**Required permissions**: ohos.permission.READ_LOCAL_DEVICE_NAME

**Since**: 20


**Parameters**

| Parameter| Description|
| -- | -- |
| char **localDeviceName | Pointer to the display name of the local device. After using this API, you need to manually release resources to free up space. If the application has the **ohos.permission.READ_LOCAL_DEVICE_NAME** permission, the device display name is returned. Otherwise, the default device name is returned.|
| unsigned int &len | Length of the display name of the local device.|

**Return value**

| Type| Description                                                                                                                                                                                                                                                                                                                                                                          |
| -- |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int32_t | Error code. For details about the error code definitions, see [DeviceManager_ErrorCode](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode).<br>         [ERR_OK](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) is returned if the execution is successful.<br>         [DM_ERR_FAILED](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) is returned if the function fails to be executed.<br>         [DM_ERR_OBTAIN_SERVICE](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) is returned if the device management service fails to be obtained.<br>         [DM_ERR_OBTAIN_BUNDLE_NAME](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) is returned if the bundle name fails to be obtained.<br>         [ERR_INVALID_PARAMETER](capi-oh-device-manager-err-code-h.md#devicemanager_errorcode) is returned if the parameter **localDeviceName** is a null pointer or ***localDeviceName** is not a null pointer.|

**Example**

```c++
#include "napi/native_api.h"
#include "hilog/log.h"
#include <distributedhardware/device_manager/oh_device_manager.h>
#include <distributedhardware/device_manager/oh_device_manager_err_code.h>
static napi_value GetDeviceName(napi_env env, napi_callback_info info) {
    napi_value result = nullptr;
    napi_create_object(env, &result);
    char *localDeviceName = nullptr; // Declare an empty string. You do not need to allocate the address in advance. The address is allocated internally.
    unsigned int len = 0;
    // Pass the address of the empty string to the API.
    int32_t ret = OH_DeviceManager_GetLocalDeviceName(&localDeviceName, len);
    if (ret != ERR_OK) {
        OH_LOG_ERROR(LOG_APP, "ret:%{public}d", ret);
    }

    napi_value code = nullptr;
    napi_create_int32(env, ret, &code);
    napi_set_named_property(env, result, "code", code);

    if (ret == ERR_OK && localDeviceName != nullptr) {
        napi_value deviceName = nullptr;
        napi_create_string_utf8(env, localDeviceName, NAPI_AUTO_LENGTH, &deviceName);
        napi_set_named_property(env, result, "deviceName", deviceName);
        delete[] localDeviceName; // Free the memory.

        napi_value deviceNameLen = nullptr;
        napi_create_int32(env, len, &deviceNameLen);
        napi_set_named_property(env, result, "deviceNameLen", deviceNameLen);
    }
    return result;
}
```
