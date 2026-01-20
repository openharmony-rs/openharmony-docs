# game_device.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## Overview

Defines APIs for game devices.

**Library:** libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-game-controller.md)


## Summary


### Types

| Name| Description| 
| -------- | -------- |
| typedef struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) | Defines the calling result of [OH_GameDevice_GetAllDeviceInfos](capi-game-controller.md#oh_gamedevice_getalldeviceinfos).| 


### Functions

| Name| Description| 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_GetAllDeviceInfos](capi-game-controller.md#oh_gamedevice_getalldeviceinfos) ([GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | Obtains information about all online game devices.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_RegisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_registerdevicemonitor) ([GameDevice_DeviceMonitorCallback](capi-game-controller.md#gamedevice_devicemonitorcallback) deviceMonitorCallback) | Registers the listening callback for game device status change events.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_UnregisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_unregisterdevicemonitor) (void) | Unregisters the listening callback for game device status change events.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DestroyAllDeviceInfos](capi-game-controller.md#oh_gamedevice_destroyalldeviceinfos) ([GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | Destroys the [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) instance when it is no longer in use.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetCount](capi-game-controller.md#oh_gamedevice_alldeviceinfos_getcount) (const struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*allDeviceInfos, int32_t \*count) | Obtains the number of game devices.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetDeviceInfo](capi-game-controller.md#oh_gamedevice_alldeviceinfos_getdeviceinfo) (const struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*allDeviceInfos, const int32_t index, [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | Obtains information about a game device with a specified index.| 
