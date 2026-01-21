# game_pad_event.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## Overview

Defines APIs for game controller events.

**Library:** libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-game-controller.md)


## Summary


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) | Defines source types of game controller axis events.| 
| typedef enum [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) | Defines button action types of the game controller.| 
| typedef struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) | Defines game controller button events.| 
| typedef struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) | Defines game controller axis events.| 
| typedef struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) | Defines pressed buttons.| 
| typedef void(\*[GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback)) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent) | Defines the callback function used in the button event registration listening API. Called when a player presses a button.| 
| typedef void(\*[GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback)) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent) | Defines the callback function used in the axis event registration listening API. Called when a player operates a joystick.| 


### Enums

| Name| Description| 
| -------- | -------- |
| [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) {<br>DPAD = 0,<br>LEFT_THUMBSTICK = 1,<br>RIGHT_THUMBSTICK = 2,<br>LEFT_TRIGGER = 3,<br>RIGHT_TRIGGER = 4<br>} | Source types of game controller axis events.| 
| [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) {<br>DOWN = 0,<br>UP = 1<br>} | Button action types of the game controller.| 


### Functions

| Name| Description| 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetDeviceId](capi-game-controller.md#oh_gamepad_buttonevent_getdeviceid) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, char \*\*deviceId) | Obtains the game device ID from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonAction](capi-game-controller.md#oh_gamepad_buttonevent_getbuttonaction) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) \*actionType) | Obtains the button action type from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCode](capi-game-controller.md#oh_gamepad_buttonevent_getbuttoncode) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int32_t \*code) | Obtains the button code from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCodeName](capi-game-controller.md#oh_gamepad_buttonevent_getbuttoncodename) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, char \*\*codeName) | Obtains the button name from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetCount](capi-game-controller.md#oh_gamepad_pressedbuttons_getcount) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int32_t \*count) | Obtains the number of buttons that are pressed from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetButtonInfo](capi-game-controller.md#oh_gamepad_pressedbuttons_getbuttoninfo) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, const int32_t index, [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*\*pressedButton) | Obtains the pressed button with a given index from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_DestroyPressedButton](capi-game-controller.md#oh_gamepad_destroypressedbutton) ([GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*\*pressedButton) | Destroys the [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) instance when it is no longer in use.| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCode](capi-game-controller.md#oh_gamepad_pressedbutton_getbuttoncode) (const struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*pressedButton, int32_t \*code) | Obtains the button code from [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCodeName](capi-game-controller.md#oh_gamepad_pressedbutton_getbuttoncodename) (const struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*pressedButton, char \*\*codeName) | Obtains the button name from [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetActionTime](capi-game-controller.md#oh_gamepad_buttonevent_getactiontime) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int64_t \*actionTime) | Obtains the time when the button action is performed from [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetDeviceId](capi-game-controller.md#oh_gamepad_axisevent_getdeviceid) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, char \*\*deviceId) | Obtains the game device ID from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetAxisSourceType](capi-game-controller.md#oh_gamepad_axisevent_getaxissourcetype) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) \*axisSourceType) | Obtains source type of the axis event from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetXAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getxaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the X-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetYAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getyaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Y-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetZAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getzaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Z-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetRZAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getrzaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the RZ-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatXAxisValue](capi-game-controller.md#oh_gamepad_axisevent_gethatxaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the HatX-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatYAxisValue](capi-game-controller.md#oh_gamepad_axisevent_gethatyaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the HatY-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetBrakeAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getbrakeaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Brake-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetGasAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getgasaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | Obtains the Gas-axis value from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetActionTime](capi-game-controller.md#oh_gamepad_axisevent_getactiontime) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, int64_t \*actionTime) | Obtains the action time from [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent).| 
