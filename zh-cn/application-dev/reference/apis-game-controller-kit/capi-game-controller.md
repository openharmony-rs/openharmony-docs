# GameController
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

GameController模块提供游戏控制器功能的API接口。

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21


## 汇总


### 文件

| 名称 | 描述 | 
| -------- | -------- |
| [game_controller_type.h](capi-game-controller-type.md) | 定义GameController模块的通用枚举类型。 | 
| [game_device.h](capi-game-device.md) | 定义游戏设备的接口。 | 
| [game_device_event.h](capi-game-device-event.md) | 定义游戏设备事件的接口。 | 
| [game_pad.h](capi-game-pad.md) | 定义游戏手柄的接口。 | 
| [game_pad_event.h](capi-game-pad-event.md) | 定义游戏手柄事件的接口。 | 


### 类型定义

| 名称 | 描述 | 
| -------- | -------- |
| typedef enum [GameController_ErrorCode](#gamecontroller_errorcode) [GameController_ErrorCode](#gamecontroller_errorcode) | 此枚举定义游戏控制器的错误码。 | 
| typedef struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) | 定义[OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos)接口的调用结果。 | 
| typedef enum [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) | 此枚举定义设备的状态变化类型。 | 
| typedef enum [GameDevice_DeviceType](#gamedevice_devicetype) [GameDevice_DeviceType](#gamedevice_devicetype) | 此枚举定义设备类型。 | 
| typedef struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) [GameDevice_DeviceInfo](#gamedevice_deviceinfo) | 定义设备信息。 | 
| typedef struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) [GameDevice_DeviceEvent](#gamedevice_deviceevent) | 定义设备状态变化事件。 | 
| typedef void(\*[GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback)) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent) | 定义[OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor)中使用的回调函数。当设备上线或下线时，该回调函数将被调用。 | 
| typedef enum [GamePad_AxisSourceType](#gamepad_axissourcetype) [GamePad_AxisSourceType](#gamepad_axissourcetype) | 此枚举定义手柄轴事件来源类型。 | 
| typedef enum [GamePad_Button_ActionType](#gamepad_button_actiontype) [GamePad_Button_ActionType](#gamepad_button_actiontype) | 此枚举定义手柄按键动作类型。 | 
| typedef struct [GamePad_ButtonEvent](#gamepad_buttonevent) [GamePad_ButtonEvent](#gamepad_buttonevent) | 定义手柄按键事件。 | 
| typedef struct [GamePad_AxisEvent](#gamepad_axisevent) [GamePad_AxisEvent](#gamepad_axisevent) | 定义手柄轴事件。 | 
| typedef struct [GamePad_PressedButton](#gamepad_pressedbutton) [GamePad_PressedButton](#gamepad_pressedbutton) | 定义手柄按下的按键。 | 
| typedef void(\*[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent) | 定义在按键事件注册监听接口中使用的回调函数。当玩家按下按键时，该回调函数将被调用。 | 
| typedef void(\*[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent) | 定义在轴事件注册监听接口中使用的回调函数。当玩家操作摇杆时，该回调函数将被调用。 | 


### 枚举

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](#gamecontroller_errorcode) {<br/>GAME_CONTROLLER_SUCCESS = 0,<br/>GAME_CONTROLLER_PARAM_ERROR = 401,<br/>GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR = 32200001,<br/>GAME_CONTROLLER_NO_MEMORY = 32200002<br/>} | 游戏控制器错误码。 | 
| [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) {<br/>OFFLINE = 0,<br/>ONLINE = 1<br/>} | 设备的状态变化类型。 | 
| [GameDevice_DeviceType](#gamedevice_devicetype) {<br/>UNKNOWN = 0,<br/>GAME_PAD = 1<br/>} | 设备类型。 | 
| [GamePad_AxisSourceType](#gamepad_axissourcetype) {<br/>DPAD = 0,<br/>LEFT_THUMBSTICK = 1,<br/>RIGHT_THUMBSTICK = 2,<br/>LEFT_TRIGGER = 3,<br/>RIGHT_TRIGGER = 4<br/>} | 手柄轴事件来源类型。 | 
| [GamePad_Button_ActionType](#gamepad_button_actiontype) {<br/>DOWN = 0,<br/>UP = 1<br/>} | 手柄按键动作类型。 | 


### 函数

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos) ([GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | 获取所有在线设备的信息。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor) ([GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback) deviceMonitorCallback) | 注册设备状态变化事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_UnregisterDeviceMonitor](#oh_gamedevice_unregisterdevicemonitor) (void) | 取消注册设备状态变化事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DestroyAllDeviceInfos](#oh_gamedevice_destroyalldeviceinfos) ([GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | 当[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例不再使用，销毁该实例。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetCount](#oh_gamedevice_alldeviceinfos_getcount) (const struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*allDeviceInfos, int32_t \*count) | 获取设备数量。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetDeviceInfo](#oh_gamedevice_alldeviceinfos_getdeviceinfo) (const struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*allDeviceInfos, const int32_t index, [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | 从所有设备信息中获取指定序号的设备信息。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetChangedType](#oh_gamedevice_deviceevent_getchangedtype) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent, [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) \*statusChangedType) | 从设备状态变化事件中获取状态变化类型。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetDeviceInfo](#oh_gamedevice_deviceevent_getdeviceinfo) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent, [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | 从设备状态变化事件中获取设备信息。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DestroyDeviceInfo](#oh_gamedevice_destroydeviceinfo) ([GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | 当[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例不再使用，销毁该实例。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceId](#oh_gamedevice_deviceinfo_getdeviceid) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*deviceId) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备ID。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetName](#oh_gamedevice_deviceinfo_getname) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*name) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备名称。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetProduct](#oh_gamedevice_deviceinfo_getproduct) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, int32_t \*product) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取产品信息。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetVersion](#oh_gamedevice_deviceinfo_getversion) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, int32_t \*version) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取版本信息。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetPhysicalAddress](#oh_gamedevice_deviceinfo_getphysicaladdress) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*physicalAddress) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取物理地址。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceType](#oh_gamedevice_deviceinfo_getdevicetype) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, [GameDevice_DeviceType](#gamedevice_devicetype) \*deviceType) | 从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备类型。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftShoulder_RegisterButtonInputMonitor](#oh_gamepad_leftshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor](#oh_gamepad_leftshoulder_unregisterbuttoninputmonitor) (void) | 取消注册LeftShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightShoulder_RegisterButtonInputMonitor](#oh_gamepad_rightshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightShoulder_UnregisterButtonInputMonitor](#oh_gamepad_rightshoulder_unregisterbuttoninputmonitor) (void) | 取消注册RightShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_RegisterButtonInputMonitor](#oh_gamepad_lefttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor](#oh_gamepad_lefttrigger_unregisterbuttoninputmonitor) (void) | 取消注册LeftTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_RegisterAxisInputMonitor](#oh_gamepad_lefttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册LeftTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor](#oh_gamepad_lefttrigger_unregisteraxisinputmonitor) (void) | 取消注册LeftTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_RegisterButtonInputMonitor](#oh_gamepad_righttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_UnregisterButtonInputMonitor](#oh_gamepad_righttrigger_unregisterbuttoninputmonitor) (void) | 取消注册RightTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_RegisterAxisInputMonitor](#oh_gamepad_righttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册RightTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_UnregisterAxisInputMonitor](#oh_gamepad_righttrigger_unregisteraxisinputmonitor) (void) | 取消注册RightTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonMenu_RegisterButtonInputMonitor](#oh_gamepad_buttonmenu_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Menu按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor](#oh_gamepad_buttonmenu_unregisterbuttoninputmonitor) (void) | 取消注册Menu按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonHome_RegisterButtonInputMonitor](#oh_gamepad_buttonhome_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Home按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonHome_UnregisterButtonInputMonitor](#oh_gamepad_buttonhome_unregisterbuttoninputmonitor) (void) | 取消注册Home按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonA_RegisterButtonInputMonitor](#oh_gamepad_buttona_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册A按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonA_UnregisterButtonInputMonitor](#oh_gamepad_buttona_unregisterbuttoninputmonitor) (void) | 取消注册A按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonB_RegisterButtonInputMonitor](#oh_gamepad_buttonb_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册B按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonB_UnregisterButtonInputMonitor](#oh_gamepad_buttonb_unregisterbuttoninputmonitor) (void) | 取消注册B按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonX_RegisterButtonInputMonitor](#oh_gamepad_buttonx_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册X按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonX_UnregisterButtonInputMonitor](#oh_gamepad_buttonx_unregisterbuttoninputmonitor) (void) | 取消注册X按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonY_RegisterButtonInputMonitor](#oh_gamepad_buttony_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Y按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonY_UnregisterButtonInputMonitor](#oh_gamepad_buttony_unregisterbuttoninputmonitor) (void) | 取消注册Y按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonC_RegisterButtonInputMonitor](#oh_gamepad_buttonc_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册C按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonC_UnregisterButtonInputMonitor](#oh_gamepad_buttonc_unregisterbuttoninputmonitor) (void) | 取消注册C按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_leftbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向左按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_leftbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向左按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_rightbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向右按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_rightbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向右按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_upbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向上按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_upbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向上按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_downbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向下按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_downbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向下按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RegisterAxisInputMonitor](#oh_gamepad_dpad_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册方向按键轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UnregisterAxisInputMonitor](#oh_gamepad_dpad_unregisteraxisinputmonitor) (void) | 取消注册方向按键轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor](#oh_gamepad_leftthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor](#oh_gamepad_leftthumbstick_unregisterbuttoninputmonitor) (void) | 取消注册LeftThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor](#oh_gamepad_leftthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册LeftThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor](#oh_gamepad_leftthumbstick_unregisteraxisinputmonitor) (void) | 取消注册LeftThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_RegisterButtonInputMonitor](#oh_gamepad_rightthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor](#oh_gamepad_rightthumbstick_unregisterbuttoninputmonitor) (void) | 取消注册RightThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_RegisterAxisInputMonitor](#oh_gamepad_rightthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册RightThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor](#oh_gamepad_rightthumbstick_unregisteraxisinputmonitor) (void) | 取消注册RightThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetDeviceId](#oh_gamepad_buttonevent_getdeviceid) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, char \*\*deviceId) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取设备ID。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonAction](#oh_gamepad_buttonevent_getbuttonaction) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, [GamePad_Button_ActionType](#gamepad_button_actiontype) \*actionType) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键动作类型。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCode](#oh_gamepad_buttonevent_getbuttoncode) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int32_t \*code) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键编码。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCodeName](#oh_gamepad_buttonevent_getbuttoncodename) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, char \*\*codeName) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键的名称。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetCount](#oh_gamepad_pressedbuttons_getcount) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int32_t \*count) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按下的按键数量。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetButtonInfo](#oh_gamepad_pressedbuttons_getbuttoninfo) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, const int32_t index, [GamePad_PressedButton](#gamepad_pressedbutton) \*\*pressedButton) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取指定序号的按下的按键。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_DestroyPressedButton](#oh_gamepad_destroypressedbutton) ([GamePad_PressedButton](#gamepad_pressedbutton) \*\*pressedButton) | 当[GamePad_PressedButton](#gamepad_pressedbutton)实例不再使用， 销毁该实例。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCode](#oh_gamepad_pressedbutton_getbuttoncode) (const struct [GamePad_PressedButton](#gamepad_pressedbutton) \*pressedButton, int32_t \*code) | 从按下的按键[GamePad_PressedButton](#gamepad_pressedbutton)中获取按键编码。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCodeName](#oh_gamepad_pressedbutton_getbuttoncodename) (const struct [GamePad_PressedButton](#gamepad_pressedbutton) \*pressedButton, char \*\*codeName) | 从按下的按键[GamePad_PressedButton](#gamepad_pressedbutton)中获取按键的名称。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetActionTime](#oh_gamepad_buttonevent_getactiontime) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int64_t \*actionTime) | 从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键动作的时间。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetDeviceId](#oh_gamepad_axisevent_getdeviceid) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, char \*\*deviceId) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取设备ID。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetAxisSourceType](#oh_gamepad_axisevent_getaxissourcetype) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, [GamePad_AxisSourceType](#gamepad_axissourcetype) \*axisSourceType) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取轴事件来源类型。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetXAxisValue](#oh_gamepad_axisevent_getxaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取X轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetYAxisValue](#oh_gamepad_axisevent_getyaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Y轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetZAxisValue](#oh_gamepad_axisevent_getzaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Z轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetRZAxisValue](#oh_gamepad_axisevent_getrzaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取RZ轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatXAxisValue](#oh_gamepad_axisevent_gethatxaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取HatX轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatYAxisValue](#oh_gamepad_axisevent_gethatyaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取HatY轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetBrakeAxisValue](#oh_gamepad_axisevent_getbrakeaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Brake轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetGasAxisValue](#oh_gamepad_axisevent_getgasaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Gas轴的轴值。 | 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetActionTime](#oh_gamepad_axisevent_getactiontime) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, int64_t \*actionTime) | 从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取动作时间。 | 


## 类型定义说明


### GameController_ErrorCode

```c
typedef enum GameController_ErrorCode GameController_ErrorCode
```

**描述**

此枚举定义游戏控制器的错误码。

**起始版本：** 21


### GameDevice_AllDeviceInfos

```c
typedef struct GameDevice_AllDeviceInfos GameDevice_AllDeviceInfos
```

**描述**

定义[OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos)接口的调用结果。

**起始版本：** 21


### GameDevice_DeviceEvent

```c
typedef struct GameDevice_DeviceEvent GameDevice_DeviceEvent
```

**描述**

定义设备状态变化事件。

**起始版本：** 21


### GameDevice_DeviceInfo

```c
typedef struct GameDevice_DeviceInfo GameDevice_DeviceInfo
```

**描述**

定义设备信息。

**起始版本：** 21


### GameDevice_DeviceMonitorCallback

```c
typedef void(*GameDevice_DeviceMonitorCallback) (const struct GameDevice_DeviceEvent *deviceEvent)
```

**描述**

定义[OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor)中使用的回调函数。当设备上线或下线时，该回调函数将被调用。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceEvent | 输出参数。设备状态变化事件[GameDevice_DeviceEvent](#gamedevice_deviceevent)。 | 


### GameDevice_DeviceType

```c
typedef enum GameDevice_DeviceType GameDevice_DeviceType
```

**描述**

此枚举定义设备类型。

**起始版本：** 21


### GameDevice_StatusChangedType

```c
typedef enum GameDevice_StatusChangedType GameDevice_StatusChangedType
```

**描述**

此枚举定义设备的状态变化类型。

**起始版本：** 21


### GamePad_AxisEvent

```c
typedef struct GamePad_AxisEvent GamePad_AxisEvent
```

**描述**

定义手柄轴事件。

**起始版本：** 21


### GamePad_AxisInputMonitorCallback

```c
typedef void(*GamePad_AxisInputMonitorCallback) (const struct GamePad_AxisEvent *axisEvent)
```

**描述**

定义在轴事件注册监听接口中使用的回调函数。当玩家操作摇杆时，该回调函数将被调用。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 输出参数，手柄轴事件[GamePad_AxisEvent](#gamepad_axisevent)。 | 


### GamePad_AxisSourceType

```c
typedef enum GamePad_AxisSourceType GamePad_AxisSourceType
```

**描述**

此枚举定义手柄轴事件来源类型。

**起始版本：** 21


### GamePad_Button_ActionType

```c
typedef enum GamePad_Button_ActionType GamePad_Button_ActionType
```

**描述**

此枚举定义手柄按键动作类型。

**起始版本：** 21


### GamePad_ButtonEvent

```c
typedef struct GamePad_ButtonEvent GamePad_ButtonEvent
```

**描述**

定义手柄按键事件。

**起始版本：** 21


### GamePad_ButtonInputMonitorCallback

```c
typedef void(*GamePad_ButtonInputMonitorCallback) (const struct GamePad_ButtonEvent *buttonEvent)
```

**描述**

定义在按键事件注册监听接口中使用的回调函数。当玩家按下按键时，该回调函数将被调用。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 输出参数，手柄按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)。 | 


### GamePad_PressedButton

```c
typedef struct GamePad_PressedButton GamePad_PressedButton
```

**描述**

定义手柄按下的按键。

**起始版本：** 21


## 枚举类型说明


### GameController_ErrorCode

```c
enum GameController_ErrorCode
```

**描述**

此枚举定义游戏控制器的错误码。

**起始版本：** 21

| 枚举值 | 描述 | 
| -------- | -------- |
| GAME_CONTROLLER_SUCCESS | 成功。 | 
| GAME_CONTROLLER_PARAM_ERROR | 参数非法。 | 
| GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR | 查询多模输入中所有设备信息失败。 | 
| GAME_CONTROLLER_NO_MEMORY | 设备内存不足。 | 


### GameDevice_DeviceType

```c
enum GameDevice_DeviceType
```

**描述**

此枚举定义设备类型。

**起始版本：** 21

| 枚举值 | 描述 | 
| -------- | -------- |
| UNKNOWN | 未知。 | 
| GAME_PAD | 游戏手柄。 | 


### GameDevice_StatusChangedType

```c
enum GameDevice_StatusChangedType
```

**描述**

此枚举定义设备的状态变化类型。

**起始版本：** 21

| 枚举值 | 描述 | 
| -------- | -------- |
| OFFLINE | 设备下线。 | 
| ONLINE | 设备上线。 | 


### GamePad_AxisSourceType

```c
enum GamePad_AxisSourceType
```

**描述**

此枚举定义手柄轴事件来源类型。

**起始版本：** 21

| 枚举值 | 描述 | 
| -------- | -------- |
| DPAD | 轴事件来源于方向按键DPAD。 | 
| LEFT_THUMBSTICK | 轴事件来源于LeftThumbstick。 | 
| RIGHT_THUMBSTICK | 轴事件来源于RightThumbstick。 | 
| LEFT_TRIGGER | 轴事件来源于LeftTrigger。 | 
| RIGHT_TRIGGER | 轴事件来源于RightTrigger。 | 


### GamePad_Button_ActionType

```c
enum GamePad_Button_ActionType
```

**描述**

此枚举定义手柄按键动作类型。

**起始版本：** 21

| 枚举值 | 描述 | 
| -------- | -------- |
| DOWN | 按键按下。 | 
| UP | 按键抬起。 | 


## 函数说明


### OH_GameDevice_AllDeviceInfos_GetCount()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetCount (const struct GameDevice_AllDeviceInfos *allDeviceInfos, int32_t *count)
```

**描述**

获取设备数量。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| allDeviceInfos | 指针指向[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例，不能为空，否则将返回错误码。 | 
| count | 输出参数，设备数量。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数allDeviceInfos为null。


### OH_GameDevice_AllDeviceInfos_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetDeviceInfo (const struct GameDevice_AllDeviceInfos *allDeviceInfos, const int32_t index, GameDevice_DeviceInfo **deviceInfo)
```

**描述**

从所有设备信息中获取指定序号的设备信息。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| allDeviceInfos | 指针指向[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例，不能为空，否则将返回错误码。 | 
| index | 指定查询的设备序号。 | 
| deviceInfo | 输出参数，二级指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)设备信息实例。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：allDeviceInfos为null或者index小于0或者index大于等于所有设备数。


### OH_GameDevice_DestroyAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_DestroyAllDeviceInfos (GameDevice_AllDeviceInfos **allDeviceInfos)
```

**描述**

当[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例不再使用，销毁该实例。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| allDeviceInfos | 二级指针指向[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数allDeviceInfos为null。


### OH_GameDevice_DestroyDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DestroyDeviceInfo (GameDevice_DeviceInfo **deviceInfo)
```

**描述**

当[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例不再使用，销毁该实例。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 二级指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo为null。


### OH_GameDevice_DeviceEvent_GetChangedType()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetChangedType (const struct GameDevice_DeviceEvent *deviceEvent, GameDevice_StatusChangedType *statusChangedType)
```

**描述**

从设备状态变化事件[GameDevice_DeviceEvent](#gamedevice_deviceevent)中获取状态变化类型。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceEvent | 指针指向[GameDevice_DeviceEvent](#gamedevice_deviceevent)实例，不能为空，否则将返回错误码。 | 
| statusChangedType | 输出参数，设备状态变化类型。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceEvent为null。


### OH_GameDevice_DeviceEvent_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetDeviceInfo (const struct GameDevice_DeviceEvent *deviceEvent, GameDevice_DeviceInfo **deviceInfo)
```

**描述**

从设备状态变化事件[GameDevice_DeviceEvent](#gamedevice_deviceevent)中获取设备信息。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceEvent | 指针指向[GameDevice_DeviceEvent](#gamedevice_deviceevent)实例，不能为空，否则将返回错误码。 | 
| deviceInfo | 输出参数，二级指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)设备信息实例。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceEvent为null。


### OH_GameDevice_DeviceInfo_GetDeviceId()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceId (const struct GameDevice_DeviceInfo *deviceInfo, char **deviceId)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备ID。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| deviceId | 输出参数，二级指针指向设备ID。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo或deviceId为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GameDevice_DeviceInfo_GetDeviceType()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceType (const struct GameDevice_DeviceInfo *deviceInfo, GameDevice_DeviceType *deviceType)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备类型。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| deviceType | 输出参数，设备类型。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo为null。


### OH_GameDevice_DeviceInfo_GetName()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetName (const struct GameDevice_DeviceInfo *deviceInfo, char **name)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取设备名称。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| name | 输出参数，二级指针指向设备名称。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo或name为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GameDevice_DeviceInfo_GetPhysicalAddress()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetPhysicalAddress (const struct GameDevice_DeviceInfo *deviceInfo, char **physicalAddress)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取物理地址。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| physicalAddress | 输出参数，二级指针指向物理地址。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo或physicalAddress为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GameDevice_DeviceInfo_GetProduct()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetProduct (const struct GameDevice_DeviceInfo *deviceInfo, int32_t *product)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取产品信息。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| product | 输出参数，产品信息。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo为null。


### OH_GameDevice_DeviceInfo_GetVersion()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetVersion (const struct GameDevice_DeviceInfo *deviceInfo, int32_t *version)
```

**描述**

从设备信息[GameDevice_DeviceInfo](#gamedevice_deviceinfo)中获取版本信息。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceInfo | 指针指向[GameDevice_DeviceInfo](#gamedevice_deviceinfo)实例，不能为空，否则将返回错误码。 | 
| version | 输出参数，版本信息。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceInfo为null。


### OH_GameDevice_GetAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_GetAllDeviceInfos (GameDevice_AllDeviceInfos **allDeviceInfos)
```

**描述**

获取所有在线设备的信息。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| allDeviceInfos | 输出参数。二级指针指向[GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos)实例，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR：查询多模输入中所有设备信息失败。


### OH_GameDevice_RegisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_RegisterDeviceMonitor (GameDevice_DeviceMonitorCallback deviceMonitorCallback)
```

**描述**

注册设备状态变化事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| deviceMonitorCallback | 回调函数[GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数deviceMonitorCallback为null。


### OH_GameDevice_UnregisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_UnregisterDeviceMonitor (void)
```

**描述**

取消注册设备状态变化事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_AxisEvent_GetActionTime()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetActionTime (const struct GamePad_AxisEvent *axisEvent, int64_t *actionTime)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取动作时间。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| actionTime | 输出参数，动作时间。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetAxisSourceType()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetAxisSourceType (const struct GamePad_AxisEvent *axisEvent, GamePad_AxisSourceType *axisSourceType)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取轴事件来源类型。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisSourceType | 输出参数，轴事件来源类型[GamePad_AxisSourceType](#gamepad_axissourcetype)。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetBrakeAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetBrakeAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Brake轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetDeviceId()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetDeviceId (const struct GamePad_AxisEvent *axisEvent, char **deviceId)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取设备ID。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| deviceId | 输出参数，二级指针指向设备ID。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent或deviceId为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GamePad_AxisEvent_GetGasAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetGasAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Gas轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetHatXAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetHatXAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取HatX轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetHatYAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetHatYAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取HatY轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetRZAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetRZAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取RZ轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetXAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetXAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取X轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetYAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetYAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Y轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_AxisEvent_GetZAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetZAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**描述**

从轴事件[GamePad_AxisEvent](#gamepad_axisevent)中获取Z轴的轴值。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| axisEvent | 指针指向[GamePad_AxisEvent](#gamepad_axisevent)实例，不能为空，否则将返回错误码。 | 
| axisValue | 输出参数，轴值。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数axisEvent为null。


### OH_GamePad_ButtonA_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonA_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册A按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonA_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonA_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册A按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonB_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonB_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册B按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 输出参数，回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonB_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonB_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册B按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonC_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonC_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册C按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 输出参数，回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonC_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonC_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册C按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonEvent_GetActionTime()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetActionTime (const struct GamePad_ButtonEvent *buttonEvent, int64_t *actionTime)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键动作的时间。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| actionTime | 输出参数，按键动作的时间。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent为null。


### OH_GamePad_ButtonEvent_GetButtonAction()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonAction (const struct GamePad_ButtonEvent *buttonEvent, GamePad_Button_ActionType *actionType)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键动作类型。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| actionType | 输出参数，按键动作类型。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent为null。


### OH_GamePad_ButtonEvent_GetButtonCode()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonCode (const struct GamePad_ButtonEvent *buttonEvent, int32_t *code)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键编码。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| code | 输出参数，按键编码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent为null。


### OH_GamePad_ButtonEvent_GetButtonCodeName()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonCodeName (const struct GamePad_ButtonEvent *buttonEvent, char **codeName)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按键的名称。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| codeName | 输出参数，二级指针指向按键的名称。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent或codeName为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GamePad_ButtonEvent_GetDeviceId()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetDeviceId (const struct GamePad_ButtonEvent *buttonEvent, char **deviceId)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取设备ID。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| deviceId | 输出参数，二级指针指向设备ID。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent或deviceId为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GamePad_ButtonHome_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonHome_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册Home按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonHome_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonHome_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册Home按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonMenu_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonMenu_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册Menu按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册Menu按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonX_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonX_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册X按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 输出参数，回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonX_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonX_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册X按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_ButtonY_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonY_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册Y按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 输出参数，回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_ButtonY_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonY_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册Y按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_DestroyPressedButton()

```c
GameController_ErrorCode OH_GamePad_DestroyPressedButton (GamePad_PressedButton **pressedButton)
```

**描述**

当[GamePad_PressedButton](#gamepad_pressedbutton)实例不再使用， 销毁该实例。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| pressedButton | 二级指针指向[GamePad_PressedButton](#gamepad_pressedbutton)实例，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数pressedButton为null。


### OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册方向按键的向下按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册方向按键的向下按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册方向按键的向左按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册方向按键的向左按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_Dpad_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**描述**

注册方向按键轴事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册方向按键的向右按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册方向按键的向右按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_Dpad_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UnregisterAxisInputMonitor (void)
```

**描述**

取消注册方向按键轴事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册方向按键的向上按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册方向按键的向上按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_LeftShoulder_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftShoulder_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册LeftShoulder按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册LeftShoulder按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**描述**

注册LeftThumbstick轴事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册LeftThumbstick按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor (void)
```

**描述**

取消注册LeftThumbstick轴事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册LeftThumbstick按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_LeftTrigger_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**描述**

注册LeftTrigger轴事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_LeftTrigger_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册LeftTrigger按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor (void)
```

**描述**

取消注册LeftTrigger轴事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册LeftTrigger按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_PressedButton_GetButtonCode()

```c
GameController_ErrorCode OH_GamePad_PressedButton_GetButtonCode (const struct GamePad_PressedButton *pressedButton, int32_t *code)
```

**描述**

从按下的按键[GamePad_PressedButton](#gamepad_pressedbutton)中获取按键编码。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| pressedButton | 指针指向[GamePad_PressedButton](#gamepad_pressedbutton)实例，不能为空，否则将返回错误码。 | 
| code | 输出参数，按键编码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数pressedButton为null。


### OH_GamePad_PressedButton_GetButtonCodeName()

```c
GameController_ErrorCode OH_GamePad_PressedButton_GetButtonCodeName (const struct GamePad_PressedButton *pressedButton, char **codeName)
```

**描述**

从按下的按键[GamePad_PressedButton](#gamepad_pressedbutton)中获取按键的名称。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| pressedButton | 指针指向[GamePad_PressedButton](#gamepad_pressedbutton)实例，不能为空，否则将返回错误码。 | 
| codeName | 输出参数，二级指针指向按键的名称。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数pressedButton或codeName为null。

- GAME_CONTROLLER_NO_MEMORY：设备内存不足。


### OH_GamePad_PressedButtons_GetButtonInfo()

```c
GameController_ErrorCode OH_GamePad_PressedButtons_GetButtonInfo (const struct GamePad_ButtonEvent *buttonEvent, const int32_t index, GamePad_PressedButton **pressedButton)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取指定序号的按下的按键。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| index | 指定按键序号。 | 
| pressedButton | 输出参数，二级指针指向按下的键。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：buttonEvent为null或index小于0或index大于等于所有按键数。


### OH_GamePad_PressedButtons_GetCount()

```c
GameController_ErrorCode OH_GamePad_PressedButtons_GetCount (const struct GamePad_ButtonEvent *buttonEvent, int32_t *count)
```

**描述**

从按键事件[GamePad_ButtonEvent](#gamepad_buttonevent)中获取按下的按键数量。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| buttonEvent | 指针指向[GamePad_ButtonEvent](#gamepad_buttonevent)实例，不能为空，否则将返回错误码。 | 
| count | 输出参数，按下的按键数量。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数buttonEvent为null。


### OH_GamePad_RightShoulder_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightShoulder_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册RightShoulder按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_RightShoulder_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightShoulder_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册RightShoulder按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_RightThumbstick_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**描述**

注册RightThumbstick轴事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_RightThumbstick_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册RightThumbstick按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor (void)
```

**描述**

取消注册RightThumbstick轴事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册RightThumbstick按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_RightTrigger_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**描述**

注册RightTrigger轴事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_RightTrigger_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**描述**

注册RightTrigger按键事件的监听回调。

**起始版本：** 21

**参数:**

| 名称 | 描述 | 
| -------- | -------- |
| inputMonitorCallback | 回调函数[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)，不能为空，否则将返回错误码。 | 

**返回：**

函数的执行结果，错误码[GameController_ErrorCode](#gamecontroller_errorcode)：

- GAME_CONTROLLER_SUCCESS：成功。

- GAME_CONTROLLER_PARAM_ERROR：参数inputMonitorCallback为null。


### OH_GamePad_RightTrigger_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_UnregisterAxisInputMonitor (void)
```

**描述**

取消注册RightTrigger轴事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。


### OH_GamePad_RightTrigger_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_UnregisterButtonInputMonitor (void)
```

**描述**

取消注册RightTrigger按键事件的监听回调。

**起始版本：** 21

**返回：**

函数的执行结果，执行成功返回GAME_CONTROLLER_SUCCESS。
