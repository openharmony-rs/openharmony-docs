# native_deviceinfo.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

Declares the definitions of playback control device information.

**File to include:** <multimedia/av_session/native_deviceinfo.h>

**Library:** libohavsession.so

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVSession_OutputDeviceInfo](capi-ohavsession-avsession-outputdeviceinfo.md) | - | Defines a struct for the target device information.|
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) | AVSession_DeviceInfo | Defines a struct for the device information. This instance is used to obtain more device information and its detailed properties.|

### Functions

| Name| Description|
| -- | -- |
| [AVSession_ErrCode OH_DeviceInfo_GetAVCastCategory(AVSession_DeviceInfo *deviceInfo, AVSession_AVCastCategory *aVCastCategory)](#oh_deviceinfo_getavcastcategory) | Obtains the cast category of the target device.|
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceId(AVSession_DeviceInfo *deviceInfo, char **deviceId)](#oh_deviceinfo_getdeviceid) | Obtains the device ID of the target device.|
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceName(AVSession_DeviceInfo *deviceInfo, char **deviceName)](#oh_deviceinfo_getdevicename) | Obtains the name of the target device.|
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceType(AVSession_DeviceInfo *deviceInfo, AVSession_DeviceType *deviceType)](#oh_deviceinfo_getdevicetype) | Obtains the type of the target device.|
| [AVSession_ErrCode OH_DeviceInfo_GetSupportedProtocols(AVSession_DeviceInfo *deviceInfo, uint32_t *deviceProtocolType)](#oh_deviceinfo_getsupportedprotocols) | Obtains the protocols supported by the target device.|

## Function Description

### OH_DeviceInfo_GetAVCastCategory()

```c
AVSession_ErrCode OH_DeviceInfo_GetAVCastCategory(AVSession_DeviceInfo *deviceInfo, AVSession_AVCastCategory *aVCastCategory)
```

**Description**

Obtains the cast category of the target device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | Pointer to the device information instance.|
| [AVSession_AVCastCategory](capi-native-avsession-base-h.md#avsession_avcastcategory) *aVCastCategory | Pointer to the **aVCastCategory** value.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **deviceInfo** parameter is **nullptr**.<br>                                         2. The **aVCastCategory** parameter is **nullptr**.|

### OH_DeviceInfo_GetDeviceId()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceId(AVSession_DeviceInfo *deviceInfo, char **deviceId)
```

**Description**

Obtains the device ID of the target device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | Pointer to the device information instance.|
| char **deviceId | Double pointer to the device ID.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **deviceInfo** parameter is **nullptr**.<br>                                         2. The **deviceId** parameter is **nullptr**.|

### OH_DeviceInfo_GetDeviceName()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceName(AVSession_DeviceInfo *deviceInfo, char **deviceName)
```

**Description**

Obtains the name of the target device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | Pointer to the device information instance.|
| char **deviceName | Double pointer to the device name.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **deviceInfo** parameter is **nullptr**.<br>                                         2. The **deviceName** parameter is **nullptr**.|

### OH_DeviceInfo_GetDeviceType()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceType(AVSession_DeviceInfo *deviceInfo, AVSession_DeviceType *deviceType)
```

**Description**

Obtains the type of the target device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | Pointer to the device information instance.|
| [AVSession_DeviceType](capi-native-avsession-base-h.md#avsession_devicetype) *deviceType | Double pointer to the device type.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **deviceInfo** parameter is **nullptr**.<br>                                         2. The **deviceType** parameter is **nullptr**.|

### OH_DeviceInfo_GetSupportedProtocols()

```c
AVSession_ErrCode OH_DeviceInfo_GetSupportedProtocols(AVSession_DeviceInfo *deviceInfo, uint32_t *deviceProtocolType)
```

**Description**

Obtains the protocols supported by the target device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | Pointer to the device information instance.|
| uint32_t *deviceProtocolType | Pointer to the protocol supported by the device.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **deviceInfo** parameter is **nullptr**.<br>                                         2. The **deviceProtocolType** parameter is **nullptr**.|
