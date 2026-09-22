# game_device.h

## Overview

Defines APIs for game devices.

**Library**: libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-gamecontroller.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md) | GameDevice_AllDeviceInfos | Defines the result returned by {@link OH_GameDevice_GetAllDeviceInfos}. |

### Function

| Name | Description |
| -- | -- |
| [GameController_ErrorCode OH_GameDevice_GetAllDeviceInfos(GameDevice_AllDeviceInfos** allDeviceInfos)](#oh_gamedevice_getalldeviceinfos) | Obtains information about all online devices. |
| [GameController_ErrorCode OH_GameDevice_RegisterDeviceMonitor(GameDevice_DeviceMonitorCallback deviceMonitorCallback)](#oh_gamedevice_registerdevicemonitor) | Registers a callback for device status change events. |
| [GameController_ErrorCode OH_GameDevice_UnregisterDeviceMonitor(void)](#oh_gamedevice_unregisterdevicemonitor) | Unregisters the callback for device status change events. |
| [GameController_ErrorCode OH_GameDevice_DestroyAllDeviceInfos(GameDevice_AllDeviceInfos** allDeviceInfos)](#oh_gamedevice_destroyalldeviceinfos) | Destroys all device information instances. |
| [GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetCount(const struct GameDevice_AllDeviceInfos* allDeviceInfos, int32_t* count)](#oh_gamedevice_alldeviceinfos_getcount) | Obtains the number of devices. |
| [GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetDeviceInfo(const struct GameDevice_AllDeviceInfos* allDeviceInfos, const int32_t index, GameDevice_DeviceInfo** deviceInfo)](#oh_gamedevice_alldeviceinfos_getdeviceinfo) | Obtains the device information at the specified index. |

## Function description

### OH_GameDevice_GetAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_GetAllDeviceInfos(GameDevice_AllDeviceInfos** allDeviceInfos)
```

**Description**

Obtains information about all online devices.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md)** allDeviceInfos | Output parameter. Double pointer to the [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md) instance. The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       allDeviceInfos parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If querying      all device information in multimodal input fails, [GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.      </li></ul> |

**Reference**:

[OH_GameDevice_DestroyAllDeviceInfos](capi-game-device-h.md#oh_gamedevice_destroyalldeviceinfos) destroys all device information instances


### OH_GameDevice_RegisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_RegisterDeviceMonitor(GameDevice_DeviceMonitorCallback deviceMonitorCallback)
```

**Description**

Registers a callback for device status change events.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| GameDevice_DeviceMonitorCallback deviceMonitorCallback | Callback function [GameDevice_DeviceMonitorCallback](capi-game-device-event-h.md#gamedevice_devicemonitorcallback), which cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       deviceMonitorCallback parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

**Reference**:

[OH_GameDevice_UnregisterDeviceMonitor](capi-game-device-h.md#oh_gamedevice_unregisterdevicemonitor) unregisters the callback for device status change events


### OH_GameDevice_UnregisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_UnregisterDeviceMonitor(void)
```

**Description**

Unregisters the callback for device status change events.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned. |

### OH_GameDevice_DestroyAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_DestroyAllDeviceInfos(GameDevice_AllDeviceInfos** allDeviceInfos)
```

**Description**

Destroys all device information instances.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md)** allDeviceInfos | Double pointer to the [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md) instance. The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       allDeviceInfos parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_AllDeviceInfos_GetCount()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetCount(const struct GameDevice_AllDeviceInfos* allDeviceInfos, int32_t* count)
```

**Description**

Obtains the number of devices.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md)* allDeviceInfos | Pointer to the [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md) instance. The pointer cannot be null. |
| int32_t* count | Output parameter. Number of devices. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       allDeviceInfos parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_AllDeviceInfos_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetDeviceInfo(const struct GameDevice_AllDeviceInfos* allDeviceInfos, const int32_t index, GameDevice_DeviceInfo** deviceInfo)
```

**Description**

Obtains the device information at the specified index.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md)* allDeviceInfos | Pointer to the [GameDevice_AllDeviceInfos](capi-gamecontroller-gamedevice-alldeviceinfos.md) instance. The pointer cannot be null. |
| const int32_t index | Index of the device. |
| GameDevice_DeviceInfo** deviceInfo | Output parameter. Double pointer to the device information. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       allDeviceInfos is null, or index is less than 0 or greater than or equal to the total number of devices,      [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |


