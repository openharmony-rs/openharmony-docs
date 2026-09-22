# game_device_event.h

## Overview

Defines APIs for game device events.

**Library**: libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-gamecontroller.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) | GameDevice_DeviceInfo | Defines the device information. |
| [GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md) | GameDevice_DeviceEvent | Defines device status change events. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) | GameDevice_StatusChangedType | Defines status change types of devices. |
| [GameDevice_DeviceType](#gamedevice_devicetype) | GameDevice_DeviceType | Defines device types. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void(\* GameDevice_DeviceMonitorCallback)(const struct GameDevice_DeviceEvent* deviceEvent)](#gamedevice_devicemonitorcallback) | GameDevice_DeviceMonitorCallback | Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](capi-game-device-h.md#oh_gamedevice_registerdevicemonitor). Called when the device goes online or offline. |
| [GameController_ErrorCode OH_GameDevice_DeviceEvent_GetChangedType(const struct GameDevice_DeviceEvent* deviceEvent, GameDevice_StatusChangedType* statusChangedType)](#oh_gamedevice_deviceevent_getchangedtype) | - | Obtains the status change type from a device status change event. |
| [GameController_ErrorCode OH_GameDevice_DeviceEvent_GetDeviceInfo(const struct GameDevice_DeviceEvent* deviceEvent, GameDevice_DeviceInfo** deviceInfo)](#oh_gamedevice_deviceevent_getdeviceinfo) | - | Obtains the device information from a device status change event. |
| [GameController_ErrorCode OH_GameDevice_DestroyDeviceInfo(GameDevice_DeviceInfo** deviceInfo)](#oh_gamedevice_destroydeviceinfo) | - | Destroys a device information instance. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceId(const struct GameDevice_DeviceInfo* deviceInfo, char** deviceId)](#oh_gamedevice_deviceinfo_getdeviceid) | - | Obtains the device ID from the device information. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetName(const struct GameDevice_DeviceInfo* deviceInfo, char** name)](#oh_gamedevice_deviceinfo_getname) | - | Obtains the device name from the device information. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetProduct(const struct GameDevice_DeviceInfo* deviceInfo, int32_t* product)](#oh_gamedevice_deviceinfo_getproduct) | - | Obtains the product information from the device information. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetVersion(const struct GameDevice_DeviceInfo* deviceInfo, int32_t* version)](#oh_gamedevice_deviceinfo_getversion) | - | Obtains the version information from the device information. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetPhysicalAddress(const struct GameDevice_DeviceInfo* deviceInfo, char** physicalAddress)](#oh_gamedevice_deviceinfo_getphysicaladdress) | - | Obtains the physical address from the device information. |
| [GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceType(const struct GameDevice_DeviceInfo* deviceInfo, GameDevice_DeviceType* deviceType)](#oh_gamedevice_deviceinfo_getdevicetype) | - | Obtains the device type from the device information. |

### Variable

| Name | Description |
| -- | -- |
| void(* GameDevice_DeviceMonitorCallback)(const struct GameDevice_DeviceEvent* deviceEvent) | Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](capi-game-device-h.md#oh_gamedevice_registerdevicemonitor). Called when the device goes online or offline.<br>**Since**: 21 |

## Enum type description

### GameDevice_StatusChangedType

```c
enum GameDevice_StatusChangedType
```

**Description**

Defines status change types of devices.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

| Enum item | Description |
| -- | -- |
| OFFLINE = 0 |  |
| ONLINE = 1 |  |

### GameDevice_DeviceType

```c
enum GameDevice_DeviceType
```

**Description**

Defines device types.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

| Enum item | Description |
| -- | -- |
| UNKNOWN = 0 |  |
| GAME_PAD = 1 |  |


## Function description

### GameDevice_DeviceMonitorCallback()

```c
typedef void(* GameDevice_DeviceMonitorCallback)(const struct GameDevice_DeviceEvent* deviceEvent)
```

**Description**

Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](capi-game-device-h.md#oh_gamedevice_registerdevicemonitor). Called when the device goes online or offline.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md)\* deviceEvent | Output parameter. Game device status change event [GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md). |

### OH_GameDevice_DeviceEvent_GetChangedType()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetChangedType(const struct GameDevice_DeviceEvent* deviceEvent, GameDevice_StatusChangedType* statusChangedType)
```

**Description**

Obtains the status change type from a device status change event.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md)* deviceEvent | Pointer to the [GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md) instance. The pointer cannot be null. |
| [GameDevice_StatusChangedType](capi-game-device-event-h.md#gamedevice_statuschangedtype)* statusChangedType | Output parameter. Device status change type. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceEvent is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceEvent_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetDeviceInfo(const struct GameDevice_DeviceEvent* deviceEvent, GameDevice_DeviceInfo** deviceInfo)
```

**Description**

Obtains the device information from a device status change event.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md)* deviceEvent | Pointer to the [GameDevice_DeviceEvent](capi-gamecontroller-gamedevice-deviceevent.md) instance. The pointer cannot be null. |
| [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)** deviceInfo | Output parameter. Double pointer to the device information. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceEvent is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

**Reference**:

[OH_GameDevice_DestroyDeviceInfo](capi-game-device-event-h.md#oh_gamedevice_destroydeviceinfo) destroys a device information instance


### OH_GameDevice_DestroyDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DestroyDeviceInfo(GameDevice_DeviceInfo** deviceInfo)
```

**Description**

Destroys a device information instance.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)** deviceInfo | Double pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceInfo is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetDeviceId()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceId(const struct GameDevice_DeviceInfo* deviceInfo, char** deviceId)
```

**Description**

Obtains the device ID from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| char** deviceId | Output parameter. Double pointer to the device ID. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceInfo or deviceId is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the      device memory is insufficient, [GAME_CONTROLLER_NO_MEMORY](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetName()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetName(const struct GameDevice_DeviceInfo* deviceInfo, char** name)
```

**Description**

Obtains the device name from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| char** name | Output parameter. Double pointer to the device name. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceInfo or name is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the device      memory is insufficient, [GAME_CONTROLLER_NO_MEMORY](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetProduct()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetProduct(const struct GameDevice_DeviceInfo* deviceInfo, int32_t* product)
```

**Description**

Obtains the product information from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| int32_t* product | Output parameter. Product information. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       deviceInfo parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetVersion()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetVersion(const struct GameDevice_DeviceInfo* deviceInfo, int32_t* version)
```

**Description**

Obtains the version information from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| int32_t* version | Output parameter. Version information. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       deviceInfo parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetPhysicalAddress()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetPhysicalAddress(const struct GameDevice_DeviceInfo* deviceInfo, char** physicalAddress)
```

**Description**

Obtains the physical address from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| char** physicalAddress | Output parameter. Double pointer to the physical address. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If       deviceInfo or physicalAddress is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If      the device memory is insufficient, [GAME_CONTROLLER_NO_MEMORY](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |

### OH_GameDevice_DeviceInfo_GetDeviceType()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceType(const struct GameDevice_DeviceInfo* deviceInfo, GameDevice_DeviceType* deviceType)
```

**Description**

Obtains the device type from the device information.

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const struct GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md)* deviceInfo | Pointer to the [GameDevice_DeviceInfo](capi-gamecontroller-gamedevice-deviceinfo.md) instance. The pointer cannot be null. |
| [GameDevice_DeviceType](capi-game-device-event-h.md#gamedevice_devicetype)* deviceType | Output parameter. Device type. |

**Returns**:

| Type | Description |
| -- | -- |
| GameController_ErrorCode | <ul><li>If the operation is successful, [GAME_CONTROLLER_SUCCESS](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li>     <li>If the       deviceInfo parameter is null, [GAME_CONTROLLER_PARAM_ERROR](capi-game-controller-type-h.md#gamecontroller_errorcode) is returned.</li></ul> |


