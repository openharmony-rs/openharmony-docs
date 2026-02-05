# game_device_event.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

定义游戏设备事件的接口。

**库：** libohgame_controller.z.so

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21

**相关模块：**[GameController](capi-game-controller.md)


## 汇总


### 类型定义

| 名称 | 描述 | 
| -------- | -------- |
| typedef enum [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) | 此枚举定义设备的状态变化类型。 | 
| typedef enum [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) | 此枚举定义设备类型。 | 
| typedef struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) | 定义设备信息。 | 
| typedef struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) | 定义设备状态变化事件。 | 
| typedef void(\*[GameDevice_DeviceMonitorCallback](capi-game-controller.md#gamedevice_devicemonitorcallback)) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent) | 定义[OH_GameDevice_RegisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_registerdevicemonitor)中使用的回调函数。当设备上线或下线时，该回调函数将被调用。 | 


### 枚举

| 名称 | 描述 | 
| -------- | -------- |
| [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) {<br/>OFFLINE = 0,<br/>ONLINE = 1<br/>} | 设备的状态变化类型。 | 
| [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) {<br/>UNKNOWN = 0,<br/>GAME_PAD = 1<br/>} | 设备类型。 | 


### 函数

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetChangedType](capi-game-controller.md#oh_gamedevice_deviceevent_getchangedtype) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent, [GameDevice_StatusChangedType](capi-game-controller.md#gamedevice_statuschangedtype) \*statusChangedType) | 从设备状态变化事件中获取状态变化类型。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetDeviceInfo](capi-game-controller.md#oh_gamedevice_deviceevent_getdeviceinfo) (const struct [GameDevice_DeviceEvent](capi-game-controller.md#gamedevice_deviceevent) \*deviceEvent, [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | 从设备状态变化事件中获取设备信息。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DestroyDeviceInfo](capi-game-controller.md#oh_gamedevice_destroydeviceinfo) ([GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | 当[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)实例不再使用，销毁该实例。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceId](capi-game-controller.md#oh_gamedevice_deviceinfo_getdeviceid) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*deviceId) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取设备ID。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetName](capi-game-controller.md#oh_gamedevice_deviceinfo_getname) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*name) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取设备名称。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetProduct](capi-game-controller.md#oh_gamedevice_deviceinfo_getproduct) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, int32_t \*product) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取产品信息。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetVersion](capi-game-controller.md#oh_gamedevice_deviceinfo_getversion) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, int32_t \*version) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取版本信息。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetPhysicalAddress](capi-game-controller.md#oh_gamedevice_deviceinfo_getphysicaladdress) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, char \*\*physicalAddress) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取物理地址。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceType](capi-game-controller.md#oh_gamedevice_deviceinfo_getdevicetype) (const struct [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*deviceInfo, [GameDevice_DeviceType](capi-game-controller.md#gamedevice_devicetype) \*deviceType) | 从设备信息[GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo)中获取设备类型。 | 
