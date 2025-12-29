# game_pad_event.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

定义游戏手柄事件的接口。

**库：** libohgame_controller.z.so

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21

**相关模块：**[GameController](capi-game-controller.md)


## 汇总


### 类型定义

| 名称 | 描述 | 
| -------- | -------- |
| typedef enum [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) | 此枚举定义手柄轴事件来源类型。 | 
| typedef enum [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) | 此枚举定义手柄按键动作类型。 | 
| typedef struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) | 定义手柄按键事件。 | 
| typedef struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) | 定义手柄轴事件。 | 
| typedef struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) | 定义手柄按下的按键。 | 
| typedef void(\*[GamePad_ButtonInputMonitorCallback](capi-game-controller.md#gamepad_buttoninputmonitorcallback)) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent) | 定义在按键事件注册监听接口中使用的回调函数。当玩家按下按键时，该回调函数将被调用。 | 
| typedef void(\*[GamePad_AxisInputMonitorCallback](capi-game-controller.md#gamepad_axisinputmonitorcallback)) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent) | 定义在轴事件注册监听接口中使用的回调函数。当玩家操作摇杆时，该回调函数将被调用。 | 


### 枚举

| 名称 | 描述 | 
| -------- | -------- |
| [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) {<br/>DPAD = 0,<br/>LEFT_THUMBSTICK = 1,<br/>RIGHT_THUMBSTICK = 2,<br/>LEFT_TRIGGER = 3,<br/>RIGHT_TRIGGER = 4<br/>} | 手柄轴事件来源类型。 | 
| [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) {<br/>DOWN = 0,<br/>UP = 1<br/>} | 手柄按键动作类型。 | 


### 函数

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetDeviceId](capi-game-controller.md#oh_gamepad_buttonevent_getdeviceid) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, char \*\*deviceId) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取设备ID。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonAction](capi-game-controller.md#oh_gamepad_buttonevent_getbuttonaction) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, [GamePad_Button_ActionType](capi-game-controller.md#gamepad_button_actiontype) \*actionType) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取按键动作类型。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCode](capi-game-controller.md#oh_gamepad_buttonevent_getbuttoncode) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int32_t \*code) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取按键编码。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetButtonCodeName](capi-game-controller.md#oh_gamepad_buttonevent_getbuttoncodename) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, char \*\*codeName) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取按键的名称。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetCount](capi-game-controller.md#oh_gamepad_pressedbuttons_getcount) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int32_t \*count) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取按下的按键数量。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButtons_GetButtonInfo](capi-game-controller.md#oh_gamepad_pressedbuttons_getbuttoninfo) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, const int32_t index, [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*\*pressedButton) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取指定序号的按下的按键。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_DestroyPressedButton](capi-game-controller.md#oh_gamepad_destroypressedbutton) ([GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*\*pressedButton) | 当[GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton)实例不再使用， 销毁该实例。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCode](capi-game-controller.md#oh_gamepad_pressedbutton_getbuttoncode) (const struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*pressedButton, int32_t \*code) | 从按下的按键[GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton)中获取按键编码。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_PressedButton_GetButtonCodeName](capi-game-controller.md#oh_gamepad_pressedbutton_getbuttoncodename) (const struct [GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton) \*pressedButton, char \*\*codeName) | 从按下的按键[GamePad_PressedButton](capi-game-controller.md#gamepad_pressedbutton)中获取按键的名称。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_ButtonEvent_GetActionTime](capi-game-controller.md#oh_gamepad_buttonevent_getactiontime) (const struct [GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent) \*buttonEvent, int64_t \*actionTime) | 从按键事件[GamePad_ButtonEvent](capi-game-controller.md#gamepad_buttonevent)中获取按键动作的时间。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetDeviceId](capi-game-controller.md#oh_gamepad_axisevent_getdeviceid) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, char \*\*deviceId) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取设备ID。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetAxisSourceType](capi-game-controller.md#oh_gamepad_axisevent_getaxissourcetype) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, [GamePad_AxisSourceType](capi-game-controller.md#gamepad_axissourcetype) \*axisSourceType) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取轴事件来源类型。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetXAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getxaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取X轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetYAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getyaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取Y轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetZAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getzaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取Z轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetRZAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getrzaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取RZ轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatXAxisValue](capi-game-controller.md#oh_gamepad_axisevent_gethatxaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取HatX轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetHatYAxisValue](capi-game-controller.md#oh_gamepad_axisevent_gethatyaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取HatY轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetBrakeAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getbrakeaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取Brake轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetGasAxisValue](capi-game-controller.md#oh_gamepad_axisevent_getgasaxisvalue) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, double \*axisValue) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取Gas轴的轴值。 | 
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [OH_GamePad_AxisEvent_GetActionTime](capi-game-controller.md#oh_gamepad_axisevent_getactiontime) (const struct [GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent) \*axisEvent, int64_t \*actionTime) | 从轴事件[GamePad_AxisEvent](capi-game-controller.md#gamepad_axisevent)中获取动作时间。 | 
