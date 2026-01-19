# game_device_event.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## Overview

Defines APIs for game device events.

**Library:** libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-game-controller.md)


## Summary


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) | Defines status change types of game devices.| 
| typedef enum [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) | Defines game device types.| 
| typedef struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) | Defines the device information.| 
| typedef struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) | Defines game device status change events.| 
| typedef void(\*[GameDevice_DeviceMonitorCallback](capi-game-controller.md#gamedevice_devicemonitorcallback)) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent) | Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_registerdevicemonitor). Called when the game device goes online or offline.| 


### Enums

| Name| Description| 
| -------- | -------- |
| [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) {<br>OFFLINE = 0,<br>ONLINE = 1<br>} | Game device status change types.| 
| [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) {<br>UNKNOWN = 0,<br>GAME_PAD = 1<br>} | Game device types.| 


### Functions

| Name| Description| 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetChangedType](capi-game-controller.md#oh_gamedevice_deviceevent_getchangedtype) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent, [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) \*statusChangedType) | Obtains the status change type from a game device status change event.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetDeviceInfo](capi-game-controller.md#oh_gamedevice_deviceevent_getdeviceinfo) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent, [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | Obtains the game device information from a device status change event.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DestroyDeviceInfo](capi-game-controller.md#oh_gamedevice_destroydeviceinfo) ([GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | Destroys the [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) instance when it is no longer in use.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceId](capi-game-controller.md#oh_gamedevice_deviceinfo_getdeviceid) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*deviceId) | Obtains the game device ID from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetName](capi-game-controller.md#oh_gamedevice_deviceinfo_getname) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*name) | Obtains the game device name from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetProduct](capi-game-controller.md#oh_gamedevice_deviceinfo_getproduct) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, int32_t \*product) | Obtains the product information from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetVersion](capi-game-controller.md#oh_gamedevice_deviceinfo_getversion) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, int32_t \*version) | Obtains the version information from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetPhysicalAddress](capi-game-controller.md#oh_gamedevice_deviceinfo_getphysicaladdress) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*physicalAddress) | Obtains the physical address from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceType](capi-game-controller.md#oh_gamedevice_deviceinfo_getdevicetype) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) \*deviceType) | Obtains the game device type from [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo).| 
