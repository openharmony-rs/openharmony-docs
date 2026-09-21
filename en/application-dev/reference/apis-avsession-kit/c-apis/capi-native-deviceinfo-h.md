# native_deviceinfo.h

## Overview

Declare device info interfaces.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVSession_OutputDeviceInfo](capi-ohavsession-avsession-outputdeviceinfo.md) | - | Declaring the target Device Information. |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) | AVSession_DeviceInfo | Declaring the device information. The instance is used to get more device information detail attributes. |

### Function

| Name | Description |
| -- | -- |
| [AVSession_ErrCode OH_DeviceInfo_GetAVCastCategory(AVSession_DeviceInfo *deviceInfo, AVSession_AVCastCategory *aVCastCategory)](#oh_deviceinfo_getavcastcategory) | Get Cast Category of the target device. |
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceId(AVSession_DeviceInfo *deviceInfo, char **deviceId)](#oh_deviceinfo_getdeviceid) | Get device Id of the target device. |
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceName(AVSession_DeviceInfo *deviceInfo, char **deviceName)](#oh_deviceinfo_getdevicename) | Get device name of the target device. |
| [AVSession_ErrCode OH_DeviceInfo_GetDeviceType(AVSession_DeviceInfo *deviceInfo, AVSession_DeviceType *deviceType)](#oh_deviceinfo_getdevicetype) | Get device type of the target device. |
| [AVSession_ErrCode OH_DeviceInfo_GetSupportedProtocols(AVSession_DeviceInfo *deviceInfo, uint32_t *deviceProtocolType)](#oh_deviceinfo_getsupportedprotocols) | Get supported protocols of the target device. |

## Function description

### OH_DeviceInfo_GetAVCastCategory()

```c
AVSession_ErrCode OH_DeviceInfo_GetAVCastCategory(AVSession_DeviceInfo *deviceInfo, AVSession_AVCastCategory *aVCastCategory)
```

**Description**

Get Cast Category of the target device.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | The deviceInfo instance pointer |
| AVSession_AVCastCategory *aVCastCategory | The pointer [AVSession_AVCastCategory](capi-native-avsession-base-h.md#avsession_avcastcategory) variable that will be set the device Cast Category value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.          [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode)                                                  1.The param of deviceInfo is nullptr;                                                  2.The param of aVCastCategory is nullptr. |

### OH_DeviceInfo_GetDeviceId()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceId(AVSession_DeviceInfo *deviceInfo, char **deviceId)
```

**Description**

Get device Id of the target device.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | The deviceInfo instance pointer |
| char **deviceId | the pointer variable that will be set the device id value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.          [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode)                                                  1.The param of deviceInfo is nullptr;                                                  2.The param of deviceId is nullptr. |

### OH_DeviceInfo_GetDeviceName()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceName(AVSession_DeviceInfo *deviceInfo, char **deviceName)
```

**Description**

Get device name of the target device.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | The deviceInfo instance pointer |
| char **deviceName | the pointer variable that will be set the device name value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.          [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode)                                                  1.The param of deviceInfo is nullptr;                                                  2.The param of deviceName is nullptr. |

### OH_DeviceInfo_GetDeviceType()

```c
AVSession_ErrCode OH_DeviceInfo_GetDeviceType(AVSession_DeviceInfo *deviceInfo, AVSession_DeviceType *deviceType)
```

**Description**

Get device type of the target device.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | The deviceInfo instance pointer |
| AVSession_DeviceType *deviceType | the pointer [AVSession_DeviceType](capi-native-avsession-base-h.md#avsession_devicetype) variable that will be set the device type value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.          [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode)                                                  1.The param of deviceInfo is nullptr;                                                  2.The param of deviceType is nullptr. |

### OH_DeviceInfo_GetSupportedProtocols()

```c
AVSession_ErrCode OH_DeviceInfo_GetSupportedProtocols(AVSession_DeviceInfo *deviceInfo, uint32_t *deviceProtocolType)
```

**Description**

Get supported protocols of the target device.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) *deviceInfo | The deviceInfo instance pointer |
| uint32_t *deviceProtocolType | the pointer variable that will be set the protocols supported by current device, can be union of {@link ProtocolType}. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.          [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode)                                                  1.The param of deviceInfo is nullptr;                                                  2.The param of deviceProtocolType is nullptr. |


