# game_pad.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

定义游戏手柄的接口。

**库：** libohgame_controller.z.so

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21

**相关模块：**[GameController](capi-game-controller.md)


## 汇总


### 函数

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftShoulder_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_leftshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_leftshoulder_unregisterbuttoninputmonitor) (void) | 取消注册LeftShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightShoulder_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_rightshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightShoulder_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_rightshoulder_unregisterbuttoninputmonitor) (void) | 取消注册RightShoulder按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftTrigger_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_lefttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_lefttrigger_unregisterbuttoninputmonitor) (void) | 取消注册LeftTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftTrigger_RegisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_lefttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册LeftTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_lefttrigger_unregisteraxisinputmonitor) (void) | 取消注册LeftTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightTrigger_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_righttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightTrigger_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_righttrigger_unregisterbuttoninputmonitor) (void) | 取消注册RightTrigger按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightTrigger_RegisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_righttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册RightTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightTrigger_UnregisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_righttrigger_unregisteraxisinputmonitor) (void) | 取消注册RightTrigger轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonMenu_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonmenu_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Menu按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonmenu_unregisterbuttoninputmonitor) (void) | 取消注册Menu按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonHome_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonhome_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Home按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonHome_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonhome_unregisterbuttoninputmonitor) (void) | 取消注册Home按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonA_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttona_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册A按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonA_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttona_unregisterbuttoninputmonitor) (void) | 取消注册A按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonB_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonb_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册B按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonB_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonb_unregisterbuttoninputmonitor) (void) | 取消注册B按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonX_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonx_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册X按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonX_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonx_unregisterbuttoninputmonitor) (void) | 取消注册X按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonY_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttony_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册Y按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonY_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttony_unregisterbuttoninputmonitor) (void) | 取消注册Y按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonC_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonc_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册C按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_ButtonC_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_buttonc_unregisterbuttoninputmonitor) (void) | 取消注册C按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_leftbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向左按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_leftbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向左按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_rightbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向右按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_rightbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向右按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_upbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向上按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_upbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向上按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_downbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册方向按键的向下按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_dpad_downbutton_unregisterbuttoninputmonitor) (void) | 取消注册方向按键的向下按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_RegisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_dpad_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册方向按键轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_Dpad_UnregisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_dpad_unregisteraxisinputmonitor) (void) | 取消注册方向按键轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_leftthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册LeftThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_leftthumbstick_unregisterbuttoninputmonitor) (void) | 取消注册LeftThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_leftthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册LeftThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_leftthumbstick_unregisteraxisinputmonitor) (void) | 取消注册LeftThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightThumbstick_RegisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_rightthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | 注册RightThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor](capi-game-controller.md#oh_gamepad_rightthumbstick_unregisterbuttoninputmonitor) (void) | 取消注册RightThumbstick按键事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightThumbstick_RegisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_rightthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback) inputMonitorCallback) | 注册RightThumbstick轴事件的监听回调。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode)[OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor](capi-game-controller.md#oh_gamepad_rightthumbstick_unregisteraxisinputmonitor) (void) | 取消注册RightThumbstick轴事件的监听回调。 | 
