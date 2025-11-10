# game_device.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

定义游戏设备的接口。

**库：** libohgame_controller.z.so

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21

**相关模块：**[GameController](capi-game-controller.md)


## 汇总


### 类型定义

| 名称 | 描述 | 
| -------- | -------- |
| typedef struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos)[GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) | 定义[OH_GameDevice_GetAllDeviceInfos](capi-game-controller.md#oh_gamedevice_getalldeviceinfos)接口的调用结果。 | 


### 函数

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_GetAllDeviceInfos](capi-game-controller.md#oh_gamedevice_getalldeviceinfos) ([GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | 获取所有在线设备的信息。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_RegisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_registerdevicemonitor) ([GameDevice_DeviceMonitorCallback](capi-game-controller.md#gamedevice_devicemonitorcallback) deviceMonitorCallback) | 注册设备状态变化事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_UnregisterDeviceMonitor](capi-game-controller.md#oh_gamedevice_unregisterdevicemonitor) (void) | 取消注册设备状态变化事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_DestroyAllDeviceInfos](capi-game-controller.md#oh_gamedevice_destroyalldeviceinfos) ([GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | 当[GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos)实例不再使用，销毁该实例。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_AllDeviceInfos_GetCount](capi-game-controller.md#oh_gamedevice_alldeviceinfos_getcount) (const struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*allDeviceInfos, int32_t \*count) | 获取设备数量。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GameDevice_AllDeviceInfos_GetDeviceInfo](capi-game-controller.md#oh_gamedevice_alldeviceinfos_getdeviceinfo) (const struct [GameDevice_AllDeviceInfos](capi-game-controller.md#gamedevice_alldeviceinfos) \*allDeviceInfos, const int32_t index, [GameDevice_DeviceInfo](capi-game-controller.md#gamedevice_deviceinfo) \*\*deviceInfo) | 从所有设备信息中获取指定序号的设备信息。 | 
