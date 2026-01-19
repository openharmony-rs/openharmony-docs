# GameController
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## Overview

Provides APIs for game controller functionality.

**System capability**: SystemCapability.Game.GameController

**Since**: 21


## Summary


### Files

| Name| Description| 
| -------- | -------- |
| [game_controller_type.h](capi-game-controller-type.md) | Defines common enumeration types for the **GameController** module.| 
| [game_device.h](capi-game-device.md) | Defines APIs for game devices.| 
| [game_device_event.h](capi-game-device-event.md) | Defines APIs for game device events.| 
| [game_pad.h](capi-game-pad.md) | Defines APIs for game controllers.| 
| [game_pad_event.h](capi-game-pad-event.md) | Defines APIs for game controller events.| 


### Types

| Name| Description|
| -------- | -------- |
| typedef enum [GameController_ErrorCode](#gamecontroller_errorcode) [GameController_ErrorCode](#gamecontroller_errorcode) | Defines error codes of the game controller.|
| typedef struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) | Defines the calling result of [OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos).|
| typedef enum [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) | Defines status change types of game devices. |
| typedef enum [GameDevice_DeviceType](#gamedevice_devicetype) [GameDevice_DeviceType](#gamedevice_devicetype) | Defines game device types. |
| typedef struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) [GameDevice_DeviceInfo](#gamedevice_deviceinfo) | Defines the game device information. |
| typedef struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) [GameDevice_DeviceEvent](#gamedevice_deviceevent) | Defines game device status change events. |
| typedef void(\*[GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback)) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent) | Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor). Called when the game device goes online or offline.|
| typedef enum [GamePad_AxisSourceType](#gamepad_axissourcetype) [GamePad_AxisSourceType](#gamepad_axissourcetype) | Defines source types of game controller axis events.|
| typedef enum [GamePad_Button_ActionType](#gamepad_button_actiontype) [GamePad_Button_ActionType](#gamepad_button_actiontype) | Defines button action types of the game controller.|
| typedef struct [GamePad_ButtonEvent](#gamepad_buttonevent) [GamePad_ButtonEvent](#gamepad_buttonevent) | Defines game controller button events.|
| typedef struct [GamePad_AxisEvent](#gamepad_axisevent) [GamePad_AxisEvent](#gamepad_axisevent) | Defines game controller axis events.|
| typedef struct [GamePad_PressedButton](#gamepad_pressedbutton) [GamePad_PressedButton](#gamepad_pressedbutton) | Defines pressed buttons.|
| typedef void(\*[GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback)) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent) | Defines the callback function used in the button event registration listening API. Called when a player presses a button.|
| typedef void(\*[GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback)) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent) | Defines the callback function used in the axis event registration listening API. Called when a player operates a joystick.|


### Enums

| Name| Description| 
| -------- | -------- |
| [GameController_ErrorCode](#gamecontroller_errorcode) {<br>GAME_CONTROLLER_SUCCESS = 0,<br>GAME_CONTROLLER_PARAM_ERROR = 401,<br>GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR = 32200001,<br>GAME_CONTROLLER_NO_MEMORY = 32200002<br>} | Game controller error codes.| 
| [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) {<br>OFFLINE = 0,<br>ONLINE = 1<br>} | Game device status change types.| 
| [GameDevice_DeviceType](#gamedevice_devicetype) {<br>UNKNOWN = 0,<br>GAME_PAD = 1<br>} | Game device types.| 
| [GamePad_AxisSourceType](#gamepad_axissourcetype) {<br>DPAD = 0,<br>LEFT_THUMBSTICK = 1,<br>RIGHT_THUMBSTICK = 2,<br>LEFT_TRIGGER = 3,<br>RIGHT_TRIGGER = 4<br>} | Source types of game controller axis events.| 
| [GamePad_Button_ActionType](#gamepad_button_actiontype) {<br>DOWN = 0,<br>UP = 1<br>} | Button action types of the game controller.| 


### Functions

| Name| Description| 
| -------- | -------- |
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos) ([GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | Obtains information about all online controllers.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor) ([GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback) deviceMonitorCallback) | Registers the listening callback for game device status change events.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_UnregisterDeviceMonitor](#oh_gamedevice_unregisterdevicemonitor) (void) | Unregisters the listening callback for game device status change events.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DestroyAllDeviceInfos](#oh_gamedevice_destroyalldeviceinfos) ([GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*\*allDeviceInfos) | Destroys the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance when it is no longer in use.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetCount](#oh_gamedevice_alldeviceinfos_getcount) (const struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*allDeviceInfos, int32_t \*count) | Obtains the number of game devices.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_AllDeviceInfos_GetDeviceInfo](#oh_gamedevice_alldeviceinfos_getdeviceinfo) (const struct [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) \*allDeviceInfos, const int32_t index, [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | Obtains information about a game device with a specified index.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetChangedType](#oh_gamedevice_deviceevent_getchangedtype) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent, [GameDevice_StatusChangedType](#gamedevice_statuschangedtype) \*statusChangedType) | Obtains the status change type from a game device status change event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceEvent_GetDeviceInfo](#oh_gamedevice_deviceevent_getdeviceinfo) (const struct [GameDevice_DeviceEvent](#gamedevice_deviceevent) \*deviceEvent, [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | Obtains the game device information from a device status change event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DestroyDeviceInfo](#oh_gamedevice_destroydeviceinfo) ([GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*\*deviceInfo) | Destroys the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance when it is no longer in use.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceId](#oh_gamedevice_deviceinfo_getdeviceid) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*deviceId) | Obtains the game device ID from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetName](#oh_gamedevice_deviceinfo_getname) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*name) | Obtains the game device name from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetProduct](#oh_gamedevice_deviceinfo_getproduct) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, int32_t \*product) | Obtains the product information from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetVersion](#oh_gamedevice_deviceinfo_getversion) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, int32_t \*version) | Obtains the version information from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetPhysicalAddress](#oh_gamedevice_deviceinfo_getphysicaladdress) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, char \*\*physicalAddress) | Obtains the physical address from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GameDevice_DeviceInfo_GetDeviceType](#oh_gamedevice_deviceinfo_getdevicetype) (const struct [GameDevice_DeviceInfo](#gamedevice_deviceinfo) \*deviceInfo, [GameDevice_DeviceType](#gamedevice_devicetype) \*deviceType) | Obtains the game device type from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftShoulder_RegisterButtonInputMonitor](#oh_gamepad_leftshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Shoulder button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor](#oh_gamepad_leftshoulder_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Left Shoulder button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightShoulder_RegisterButtonInputMonitor](#oh_gamepad_rightshoulder_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Shoulder button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightShoulder_UnregisterButtonInputMonitor](#oh_gamepad_rightshoulder_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Right Shoulder button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_RegisterButtonInputMonitor](#oh_gamepad_lefttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Trigger button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor](#oh_gamepad_lefttrigger_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Left Trigger button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_RegisterAxisInputMonitor](#oh_gamepad_lefttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Trigger axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor](#oh_gamepad_lefttrigger_unregisteraxisinputmonitor) (void) | Unregisters the listening callback for the Left Trigger axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_RegisterButtonInputMonitor](#oh_gamepad_righttrigger_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Trigger button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_UnregisterButtonInputMonitor](#oh_gamepad_righttrigger_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Right Trigger button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_RegisterAxisInputMonitor](#oh_gamepad_righttrigger_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Trigger axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightTrigger_UnregisterAxisInputMonitor](#oh_gamepad_righttrigger_unregisteraxisinputmonitor) (void) | Unregisters the listening callback for the Right Trigger axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonMenu_RegisterButtonInputMonitor](#oh_gamepad_buttonmenu_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Menu button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor](#oh_gamepad_buttonmenu_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Menu button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonHome_RegisterButtonInputMonitor](#oh_gamepad_buttonhome_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Home button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonHome_UnregisterButtonInputMonitor](#oh_gamepad_buttonhome_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Home button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonA_RegisterButtonInputMonitor](#oh_gamepad_buttona_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the A button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonA_UnregisterButtonInputMonitor](#oh_gamepad_buttona_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the A button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonB_RegisterButtonInputMonitor](#oh_gamepad_buttonb_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the B button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonB_UnregisterButtonInputMonitor](#oh_gamepad_buttonb_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the B button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonX_RegisterButtonInputMonitor](#oh_gamepad_buttonx_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the X button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonX_UnregisterButtonInputMonitor](#oh_gamepad_buttonx_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the X button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonY_RegisterButtonInputMonitor](#oh_gamepad_buttony_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Y button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonY_UnregisterButtonInputMonitor](#oh_gamepad_buttony_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Y button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonC_RegisterButtonInputMonitor](#oh_gamepad_buttonc_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the C button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonC_UnregisterButtonInputMonitor](#oh_gamepad_buttonc_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the C button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_leftbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_leftbutton_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Left Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_rightbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_rightbutton_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Right Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_upbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Up Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_upbutton_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Up Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor](#oh_gamepad_dpad_downbutton_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Down Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor](#oh_gamepad_dpad_downbutton_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Down Directional button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_RegisterAxisInputMonitor](#oh_gamepad_dpad_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Directional Pad button axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_Dpad_UnregisterAxisInputMonitor](#oh_gamepad_dpad_unregisteraxisinputmonitor) (void) | Unregisters the listening callback for the Directional Pad button axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor](#oh_gamepad_leftthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Thumbstick button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor](#oh_gamepad_leftthumbstick_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Left Thumbstick button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor](#oh_gamepad_leftthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Left Thumbstick axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor](#oh_gamepad_leftthumbstick_unregisteraxisinputmonitor) (void) | Unregisters the listening callback for the Left Thumbstick axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_RegisterButtonInputMonitor](#oh_gamepad_rightthumbstick_registerbuttoninputmonitor) ([GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Thumbstick button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor](#oh_gamepad_rightthumbstick_unregisterbuttoninputmonitor) (void) | Unregisters the listening callback for the Right Thumbstick button event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_RegisterAxisInputMonitor](#oh_gamepad_rightthumbstick_registeraxisinputmonitor) ([GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback) inputMonitorCallback) | Registers the listening callback for the Right Thumbstick axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor](#oh_gamepad_rightthumbstick_unregisteraxisinputmonitor) (void) | Unregisters the listening callback for the Right Thumbstick axis event.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetDeviceId](#oh_gamepad_buttonevent_getdeviceid) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, char \*\*deviceId) | Obtains the game device ID from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonAction](#oh_gamepad_buttonevent_getbuttonaction) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, [GamePad_Button_ActionType](#gamepad_button_actiontype) \*actionType) | Obtains the button action type from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCode](#oh_gamepad_buttonevent_getbuttoncode) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int32_t \*code) | Obtains the button code from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCodeName](#oh_gamepad_buttonevent_getbuttoncodename) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, char \*\*codeName) | Obtains the button name from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetCount](#oh_gamepad_pressedbuttons_getcount) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int32_t \*count) | Obtains the number of pressed buttons from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetButtonInfo](#oh_gamepad_pressedbuttons_getbuttoninfo) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, const int32_t index, [GamePad_PressedButton](#gamepad_pressedbutton) \*\*pressedButton) | Obtains the pressed button with a given index from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_DestroyPressedButton](#oh_gamepad_destroypressedbutton) ([GamePad_PressedButton](#gamepad_pressedbutton) \*\*pressedButton) | Destroys the [GamePad_PressedButton](#gamepad_pressedbutton) instance when it is no longer in use.| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCode](#oh_gamepad_pressedbutton_getbuttoncode) (const struct [GamePad_PressedButton](#gamepad_pressedbutton) \*pressedButton, int32_t \*code) | Obtains the button code from [GamePad_PressedButton](#gamepad_pressedbutton).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCodeName](#oh_gamepad_pressedbutton_getbuttoncodename) (const struct [GamePad_PressedButton](#gamepad_pressedbutton) \*pressedButton, char \*\*codeName) | Obtains the button name from [GamePad_PressedButton](#gamepad_pressedbutton).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetActionTime](#oh_gamepad_buttonevent_getactiontime) (const struct [GamePad_ButtonEvent](#gamepad_buttonevent) \*buttonEvent, int64_t \*actionTime) | Obtains the button action time from [GamePad_ButtonEvent](#gamepad_buttonevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetDeviceId](#oh_gamepad_axisevent_getdeviceid) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, char \*\*deviceId) | Obtains the game device ID from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetAxisSourceType](#oh_gamepad_axisevent_getaxissourcetype) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, [GamePad_AxisSourceType](#gamepad_axissourcetype) \*axisSourceType) | Obtains the source type of axis event from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetXAxisValue](#oh_gamepad_axisevent_getxaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the X-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetYAxisValue](#oh_gamepad_axisevent_getyaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Y-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetZAxisValue](#oh_gamepad_axisevent_getzaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Z-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetRZAxisValue](#oh_gamepad_axisevent_getrzaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the RZ-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatXAxisValue](#oh_gamepad_axisevent_gethatxaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the HatX-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatYAxisValue](#oh_gamepad_axisevent_gethatyaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the HatY-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetBrakeAxisValue](#oh_gamepad_axisevent_getbrakeaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Brake-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetGasAxisValue](#oh_gamepad_axisevent_getgasaxisvalue) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Gas-axis value from [GamePad_AxisEvent](#gamepad_axisevent).| 
| [GameController_ErrorCode](#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetActionTime](#oh_gamepad_axisevent_getactiontime) (const struct [GamePad_AxisEvent](#gamepad_axisevent) \*axisEvent, int64_t \*actionTime) | Obtains the action time from [GamePad_AxisEvent](#gamepad_axisevent).| 


## Type Description


### GameController_ErrorCode

```c
typedef enum GameController_ErrorCode GameController_ErrorCode
```

**Description**

Defines error codes of the game controller.

**Since**: 21


### GameDevice_AllDeviceInfos

```c
typedef struct GameDevice_AllDeviceInfos GameDevice_AllDeviceInfos
```

**Description**

Defines the calling result of [OH_GameDevice_GetAllDeviceInfos](#oh_gamedevice_getalldeviceinfos).

**Since**: 21


### GameDevice_DeviceEvent

```c
typedef struct GameDevice_DeviceEvent GameDevice_DeviceEvent
```

**Description**

Defines game device status change events.

**Since**: 21


### GameDevice_DeviceInfo

```c
typedef struct GameDevice_DeviceInfo GameDevice_DeviceInfo
```

**Description**

Defines the game device information.

**Since**: 21


### GameDevice_DeviceMonitorCallback

```c
typedef void(*GameDevice_DeviceMonitorCallback) (const struct GameDevice_DeviceEvent *deviceEvent)
```

**Description**

Defines the callback function used in [OH_GameDevice_RegisterDeviceMonitor](#oh_gamedevice_registerdevicemonitor). Called when the game device goes online or offline.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceEvent | Output parameter. Game device status change event [GameDevice_DeviceEvent](#gamedevice_deviceevent).| 


### GameDevice_DeviceType

```c
typedef enum GameDevice_DeviceType GameDevice_DeviceType
```

**Description**

Defines game device types.

**Since**: 21


### GameDevice_StatusChangedType

```c
typedef enum GameDevice_StatusChangedType GameDevice_StatusChangedType
```

**Description**

Defines status change types of game devices.

**Since**: 21


### GamePad_AxisEvent

```c
typedef struct GamePad_AxisEvent GamePad_AxisEvent
```

**Description**

Defines game controller axis events.

**Since**: 21


### GamePad_AxisInputMonitorCallback

```c
typedef void(*GamePad_AxisInputMonitorCallback) (const struct GamePad_AxisEvent *axisEvent)
```

**Description**

Defines the callback function used in the axis event registration listening API. Called when a player operates a joystick.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Output parameter. Game controller axis event [GamePad_AxisEvent](#gamepad_axisevent).| 


### GamePad_AxisSourceType

```c
typedef enum GamePad_AxisSourceType GamePad_AxisSourceType
```

**Description**

Defines source types of game controller axis events.

**Since**: 21


### GamePad_Button_ActionType

```c
typedef enum GamePad_Button_ActionType GamePad_Button_ActionType
```

**Description**

Defines button action types of the game controller.

**Since**: 21


### GamePad_ButtonEvent

```c
typedef struct GamePad_ButtonEvent GamePad_ButtonEvent
```

**Description**

Defines game controller button events.

**Since**: 21


### GamePad_ButtonInputMonitorCallback

```c
typedef void(*GamePad_ButtonInputMonitorCallback) (const struct GamePad_ButtonEvent *buttonEvent)
```

**Description**

Defines the callback function used in the button event registration listening API. Called when a player presses a button.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Output parameter. Game controller button event [GamePad_ButtonEvent](#gamepad_buttonevent).| 


### GamePad_PressedButton

```c
typedef struct GamePad_PressedButton GamePad_PressedButton
```

**Description**

Defines pressed buttons.

**Since**: 21


## Enum Description


### GameController_ErrorCode

```c
enum GameController_ErrorCode
```

**Description**

Defines error codes of the game controller.

**Since**: 21

| Value| Description| 
| -------- | -------- |
| GAME_CONTROLLER_SUCCESS | Success.| 
| GAME_CONTROLLER_PARAM_ERROR | Invalid parameter.| 
| GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR | Failed to query all game device information in multimodal input.| 
| GAME_CONTROLLER_NO_MEMORY | Insufficient game device memory.| 


### GameDevice_DeviceType

```c
enum GameDevice_DeviceType
```

**Description**

Defines game device types.

**Since**: 21

| Value| Description| 
| -------- | -------- |
| UNKNOWN | Unknown.| 
| GAME_PAD | Game controller.| 


### GameDevice_StatusChangedType

```c
enum GameDevice_StatusChangedType
```

**Description**

Defines status change types of game devices.

**Since**: 21

| Value| Description| 
| -------- | -------- |
| OFFLINE | The game device is offline.| 
| ONLINE | The game device is online.| 


### GamePad_AxisSourceType

```c
enum GamePad_AxisSourceType
```

**Description**

Defines source types of game controller axis events.

**Since**: 21

| Value| Description| 
| -------- | -------- |
| DPAD | The axis event comes from the directional pad (D-pad).| 
| LEFT_THUMBSTICK | The axis event comes from the left thumbstick.| 
| RIGHT_THUMBSTICK | The axis event comes from the right thumbstick.| 
| LEFT_TRIGGER | The axis event comes from the left trigger.| 
| RIGHT_TRIGGER | The axis event comes from the right trigger.| 


### GamePad_Button_ActionType

```c
enum GamePad_Button_ActionType
```

**Description**

Defines button action types of the game controller.

**Since**: 21

| Value| Description| 
| -------- | -------- |
| DOWN | The button is pressed.| 
| UP | The button is released.| 


## Function Description


### OH_GameDevice_AllDeviceInfos_GetCount()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetCount (const struct GameDevice_AllDeviceInfos *allDeviceInfos, int32_t *count)
```

**Description**

Obtains the number of game devices.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| allDeviceInfos | Pointer to the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| count | Output parameter. Number of game devices.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **allDeviceInfos** is null.


### OH_GameDevice_AllDeviceInfos_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_AllDeviceInfos_GetDeviceInfo (const struct GameDevice_AllDeviceInfos *allDeviceInfos, const int32_t index, GameDevice_DeviceInfo **deviceInfo)
```

**Description**

Obtains information about a game device with a specified index.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| allDeviceInfos | Pointer to the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| index | Index of the game device to be queried.| 
| deviceInfo | Output parameter. The level-2 pointer points to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **allDeviceInfos** is null, or the index is less than 0 or greater than or equal to the total number of game devices.


### OH_GameDevice_DestroyAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_DestroyAllDeviceInfos (GameDevice_AllDeviceInfos **allDeviceInfos)
```

**Description**

Destroys the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance when it is no longer in use.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| allDeviceInfos | Level-2 pointer to the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance. The pointer cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **allDeviceInfos** is null.


### OH_GameDevice_DestroyDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DestroyDeviceInfo (GameDevice_DeviceInfo **deviceInfo)
```

**Description**

Destroys the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance when it is no longer in use.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Level-2 pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** is null.


### OH_GameDevice_DeviceEvent_GetChangedType()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetChangedType (const struct GameDevice_DeviceEvent *deviceEvent, GameDevice_StatusChangedType *statusChangedType)
```

**Description**

Obtains the status change type from [GameDevice_DeviceEvent](#gamedevice_deviceevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceEvent | Pointer to the [GameDevice_DeviceEvent](#gamedevice_deviceevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| statusChangedType | Output parameter. Game device status change type.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceEvent** is null.


### OH_GameDevice_DeviceEvent_GetDeviceInfo()

```c
GameController_ErrorCode OH_GameDevice_DeviceEvent_GetDeviceInfo (const struct GameDevice_DeviceEvent *deviceEvent, GameDevice_DeviceInfo **deviceInfo)
```

**Description**

Obtains the game device information from [GameDevice_DeviceEvent](#gamedevice_deviceevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceEvent | Pointer to the [GameDevice_DeviceEvent](#gamedevice_deviceevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| deviceInfo | Output parameter. The level-2 pointer points to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceEvent** is null.


### OH_GameDevice_DeviceInfo_GetDeviceId()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceId (const struct GameDevice_DeviceInfo *deviceInfo, char **deviceId)
```

**Description**

Obtains the device ID from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| deviceId | Output parameter. The level-2 pointer points to the game device ID.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** or **deviceId** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GameDevice_DeviceInfo_GetDeviceType()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetDeviceType (const struct GameDevice_DeviceInfo *deviceInfo, GameDevice_DeviceType *deviceType)
```

**Description**

Obtains the game device type from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| deviceType | Output parameter. Game device type.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** is null.


### OH_GameDevice_DeviceInfo_GetName()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetName (const struct GameDevice_DeviceInfo *deviceInfo, char **name)
```

**Description**

Obtains the game device name from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| name | Output parameter. The level-2 pointer points to the game device name.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** or **name** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GameDevice_DeviceInfo_GetPhysicalAddress()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetPhysicalAddress (const struct GameDevice_DeviceInfo *deviceInfo, char **physicalAddress)
```

**Description**

Obtains the physical address from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| physicalAddress | Output parameter. The level-2 pointer points to the physical address.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** or **physicalAddress** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GameDevice_DeviceInfo_GetProduct()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetProduct (const struct GameDevice_DeviceInfo *deviceInfo, int32_t *product)
```

**Description**

Obtains the product information from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| product | Output parameter. Product information.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** is null.


### OH_GameDevice_DeviceInfo_GetVersion()

```c
GameController_ErrorCode OH_GameDevice_DeviceInfo_GetVersion (const struct GameDevice_DeviceInfo *deviceInfo, int32_t *version)
```

**Description**

Obtains the version information from [GameDevice_DeviceInfo](#gamedevice_deviceinfo).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceInfo | Pointer to the [GameDevice_DeviceInfo](#gamedevice_deviceinfo) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| version | Output parameter. Version information.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceInfo** is null.


### OH_GameDevice_GetAllDeviceInfos()

```c
GameController_ErrorCode OH_GameDevice_GetAllDeviceInfos (GameDevice_AllDeviceInfos **allDeviceInfos)
```

**Description**

Obtains information about all online game devices.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| allDeviceInfos | Output parameter. Level-2 pointer to the [GameDevice_AllDeviceInfos](#gamedevice_alldeviceinfos) instance. The pointer cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR**: Failed to query all game device information in multimodal input.


### OH_GameDevice_RegisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_RegisterDeviceMonitor (GameDevice_DeviceMonitorCallback deviceMonitorCallback)
```

**Description**

Registers the listening callback for game device status change events.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| deviceMonitorCallback | Callback function [GameDevice_DeviceMonitorCallback](#gamedevice_devicemonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **deviceMonitorCallback** is null.


### OH_GameDevice_UnregisterDeviceMonitor()

```c
GameController_ErrorCode OH_GameDevice_UnregisterDeviceMonitor (void)
```

**Description**

Unregisters the listening callback for game device status change events.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_AxisEvent_GetActionTime()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetActionTime (const struct GamePad_AxisEvent *axisEvent, int64_t *actionTime)
```

**Description**

Obtains the action time from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| actionTime | Output parameter. Action time.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetAxisSourceType()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetAxisSourceType (const struct GamePad_AxisEvent *axisEvent, GamePad_AxisSourceType *axisSourceType)
```

**Description**

Obtains the source type of axis event from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisSourceType | Output parameter. Source type of the axis event [GamePad_AxisSourceType](#gamepad_axissourcetype).| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetBrakeAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetBrakeAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the Brake-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetDeviceId()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetDeviceId (const struct GamePad_AxisEvent *axisEvent, char **deviceId)
```

**Description**

Obtains the game device ID from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| deviceId | Output parameter. The level-2 pointer points to the game device ID.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** or **deviceId** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GamePad_AxisEvent_GetGasAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetGasAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the Gas-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetHatXAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetHatXAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the HatX-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetHatYAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetHatYAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the HatY-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetRZAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetRZAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the RZ-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetXAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetXAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the X-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetYAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetYAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the Y-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_AxisEvent_GetZAxisValue()

```c
GameController_ErrorCode OH_GamePad_AxisEvent_GetZAxisValue (const struct GamePad_AxisEvent *axisEvent, double *axisValue)
```

**Description**

Obtains the Z-axis value from [GamePad_AxisEvent](#gamepad_axisevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| axisEvent | Pointer to the [GamePad_AxisEvent](#gamepad_axisevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| axisValue | Output parameter. Axis value.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **axisEvent** is null.


### OH_GamePad_ButtonA_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonA_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the A button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonA_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonA_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the A button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonB_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonB_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the B button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Output parameter. Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonB_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonB_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the B button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonC_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonC_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the C button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Output parameter. Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonC_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonC_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the C button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonEvent_GetActionTime()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetActionTime (const struct GamePad_ButtonEvent *buttonEvent, int64_t *actionTime)
```

**Description**

Obtains the button action time from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| actionTime | Output parameter. Time when the button action is performed.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** is null.


### OH_GamePad_ButtonEvent_GetButtonAction()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonAction (const struct GamePad_ButtonEvent *buttonEvent, GamePad_Button_ActionType *actionType)
```

**Description**

Obtains the button action type from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| actionType | Output parameter. Button action type.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** is null.


### OH_GamePad_ButtonEvent_GetButtonCode()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonCode (const struct GamePad_ButtonEvent *buttonEvent, int32_t *code)
```

**Description**

Obtains the button code from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| code | Output parameter. Button code.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** is null.


### OH_GamePad_ButtonEvent_GetButtonCodeName()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetButtonCodeName (const struct GamePad_ButtonEvent *buttonEvent, char **codeName)
```

**Description**

Obtains the button name from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| codeName | Output parameter. The level-2 pointer points to the button name.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** or **codeName** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GamePad_ButtonEvent_GetDeviceId()

```c
GameController_ErrorCode OH_GamePad_ButtonEvent_GetDeviceId (const struct GamePad_ButtonEvent *buttonEvent, char **deviceId)
```

**Description**

Obtains the game device ID from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| deviceId | Output parameter. The level-2 pointer points to the game device ID.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** or **deviceId** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GamePad_ButtonHome_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonHome_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Home button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonHome_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonHome_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Home button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonMenu_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonMenu_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Menu button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonMenu_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Menu button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonX_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonX_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the X button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Output parameter. Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonX_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonX_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the X button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_ButtonY_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonY_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Y button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Output parameter. Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_ButtonY_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_ButtonY_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Y button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_DestroyPressedButton()

```c
GameController_ErrorCode OH_GamePad_DestroyPressedButton (GamePad_PressedButton **pressedButton)
```

**Description**

Destroys the [GamePad_PressedButton](#gamepad_pressedbutton) instance when it is no longer in use.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| pressedButton | Level-2 pointer to the [GamePad_PressedButton](#gamepad_pressedbutton) instance. The pointer cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **pressedButton** is null.


### OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_DownButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Down Directional button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_DownButton_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Down Directional button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_LeftButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Directional button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_LeftButton_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Directional button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_Dpad_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Directional Pad button axis event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RightButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Directional button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_RightButton_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Directional button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_Dpad_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UnregisterAxisInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Directional Pad button axis event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UpButton_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Up Directional button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_Dpad_UpButton_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Up Directional button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_LeftShoulder_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftShoulder_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Shoulder button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftShoulder_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Shoulder button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Thumbstick axis event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Thumbstick button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_UnregisterAxisInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Thumbstick axis event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftThumbstick_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Thumbstick button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_LeftTrigger_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Trigger axis event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_LeftTrigger_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Left Trigger button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_UnregisterAxisInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Trigger axis event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_LeftTrigger_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Left Trigger button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_PressedButton_GetButtonCode()

```c
GameController_ErrorCode OH_GamePad_PressedButton_GetButtonCode (const struct GamePad_PressedButton *pressedButton, int32_t *code)
```

**Description**

Obtains the button code from [GamePad_PressedButton](#gamepad_pressedbutton).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| pressedButton | Pointer to the [GamePad_PressedButton](#gamepad_pressedbutton) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| code | Output parameter. Button code.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **pressedButton** is null.


### OH_GamePad_PressedButton_GetButtonCodeName()

```c
GameController_ErrorCode OH_GamePad_PressedButton_GetButtonCodeName (const struct GamePad_PressedButton *pressedButton, char **codeName)
```

**Description**

Obtains the button name from [GamePad_PressedButton](#gamepad_pressedbutton).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| pressedButton | Pointer to the [GamePad_PressedButton](#gamepad_pressedbutton) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| codeName | Output parameter. The level-2 pointer points to the button name.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **pressedButton** or **codeName** is null.

- **GAME_CONTROLLER_NO_MEMORY**: Insufficient game device memory.


### OH_GamePad_PressedButtons_GetButtonInfo()

```c
GameController_ErrorCode OH_GamePad_PressedButtons_GetButtonInfo (const struct GamePad_ButtonEvent *buttonEvent, const int32_t index, GamePad_PressedButton **pressedButton)
```

**Description**

Obtains the pressed button with a given index from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| index | Button index.| 
| pressedButton | Output parameter. The level-2 pointer points to the pressed button.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** is null, or the index is less than 0 or greater than or equal to the number of all buttons.


### OH_GamePad_PressedButtons_GetCount()

```c
GameController_ErrorCode OH_GamePad_PressedButtons_GetCount (const struct GamePad_ButtonEvent *buttonEvent, int32_t *count)
```

**Description**

Obtains the number of pressed buttons from [GamePad_ButtonEvent](#gamepad_buttonevent).

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| buttonEvent | Pointer to the [GamePad_ButtonEvent](#gamepad_buttonevent) instance. The pointer cannot be null. Otherwise, an error code is returned.| 
| count | Output parameter. Number of pressed buttons.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **buttonEvent** is null.


### OH_GamePad_RightShoulder_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightShoulder_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Shoulder button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_RightShoulder_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightShoulder_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Shoulder button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_RightThumbstick_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Thumbstick axis event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_RightThumbstick_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Thumbstick button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_UnregisterAxisInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Thumbstick axis event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightThumbstick_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Thumbstick button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_RightTrigger_RegisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_RegisterAxisInputMonitor (GamePad_AxisInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Trigger axis event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_AxisInputMonitorCallback](#gamepad_axisinputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_RightTrigger_RegisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_RegisterButtonInputMonitor (GamePad_ButtonInputMonitorCallback inputMonitorCallback)
```

**Description**

Registers the listening callback for the Right Trigger button event.

**Since**: 21

**Parameters**

| Name| Description| 
| -------- | -------- |
| inputMonitorCallback | Callback function [GamePad_ButtonInputMonitorCallback](#gamepad_buttoninputmonitorcallback). The callback function cannot be null. Otherwise, an error code is returned.| 

**Returns**

Execution result of the function, with the error code [GameController_ErrorCode](#gamecontroller_errorcode):

- **GAME_CONTROLLER_SUCCESS**: Success.

- **GAME_CONTROLLER_PARAM_ERROR**: **inputMonitorCallback** is null.


### OH_GamePad_RightTrigger_UnregisterAxisInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_UnregisterAxisInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Trigger axis event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.


### OH_GamePad_RightTrigger_UnregisterButtonInputMonitor()

```c
GameController_ErrorCode OH_GamePad_RightTrigger_UnregisterButtonInputMonitor (void)
```

**Description**

Unregisters the listening callback for the Right Trigger button event.

**Since**: 21

**Returns**

Execution result of the function. If the execution is successful, **GAME_CONTROLLER_SUCCESS** is returned.
