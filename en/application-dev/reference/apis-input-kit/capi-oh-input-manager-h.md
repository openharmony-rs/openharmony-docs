# oh_input_manager.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides functions such as event injection and status query.

**File to include**: <multimodalinput/oh_input_manager.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Input_InterceptorEventCallback](capi-input-input-interceptoreventcallback.md) | Input_InterceptorEventCallback | Defines the structure of interceptor callback events, including mouse events, touch events, and axis events.|
| [Input_DeviceListener](capi-input-input-devicelistener.md) | Input_DeviceListener | Defines a listener for device hot swap events.|
| [OH_PixelmapNative](capi-input-oh-pixelmapnative.md) | OH_PixelmapNative | Pixel map.|
| [Input_KeyState](capi-input-input-keystate.md) | Input_KeyState | Defines key information, which identifies a key pressing behavior. For example, the Ctrl key information contains the key value and key type.|
| [Input_KeyEvent](capi-input-input-keyevent.md) | Input_KeyEvent | Key event object.|
| [Input_MouseEvent](capi-input-input-mouseevent.md) | Input_MouseEvent | Mouse event object.|
| [Input_TouchEvent](capi-input-input-touchevent.md) | Input_TouchEvent | **TouchEvent** object.|
| [Input_AxisEvent](capi-input-input-axisevent.md) | Input_AxisEvent | Axis event object.|
| [Input_Hotkey](capi-input-input-hotkey.md) | Input_Hotkey | Defines the hotkey structure.|
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) | Input_DeviceInfo | Defines the input device information.|
| [Input_InterceptorOptions](capi-input-input-interceptoroptions.md) | Input_InterceptorOptions | Defines event interception options.|
| [Input_CustomCursor](capi-input-input-customcursor.md) | Input_CustomCursor | Defines the pixel map resource of the custom mouse pointer object.|
| [Input_CursorConfig](capi-input-input-cursorconfig.md) | Input_CursorConfig | Defines the custom mouse pointer configuration.|
| [Input_CursorInfo](capi-input-input-cursorinfo.md) | Input_CursorInfo | Defines the mouse pointer information.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Input_KeyStateAction](#input_keystateaction) | Input_KeyStateAction | Provides the enum values of the key status.|
| [Input_KeyEventAction](#input_keyeventaction) | Input_KeyEventAction | Provides the enum values of the key event type.|
| [Input_MouseEventAction](#input_mouseeventaction) | Input_MouseEventAction | Provides the enum values of mouse actions.|
| [InputEvent_MouseAxis](#inputevent_mouseaxis) | InputEvent_MouseAxis | Provides the enum values of mouse axis event types.|
| [Input_MouseEventButton](#input_mouseeventbutton) | Input_MouseEventButton | Provides the enum values of mouse buttons.|
| [Input_TouchEventAction](#input_toucheventaction) | Input_TouchEventAction | Provides the enum values of touch actions.|
| [Input_InjectionStatus](#input_injectionstatus) | Input_InjectionStatus | Provides the enum values of injection permission states.|
| [InputEvent_SourceType](#inputevent_sourcetype) | InputEvent_SourceType | Provides the enum values of event source types.|
| [Input_KeyboardType](#input_keyboardtype) | Input_KeyboardType | Provides the enum values of keyboard types of the input device.|
| [Input_Result](#input_result) | Input_Result | Provides the enum values of error codes.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Input_HotkeyCallback)(Input_Hotkey* hotkey)](#input_hotkeycallback) | Input_HotkeyCallback | Defines the callback used to return hotkey events.|
| [typedef void (\*Input_KeyEventCallback)(const Input_KeyEvent* keyEvent)](#input_keyeventcallback) | Input_KeyEventCallback | Defines a lifecycle callback for **keyEvent**. If the callback is triggered, **keyEvent** will be destroyed.|
| [typedef void (\*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)](#input_mouseeventcallback) | Input_MouseEventCallback | Defines a lifecycle callback for **mouseEvent**. If the callback is triggered, **mouseEvent** will be destroyed.|
| [typedef void (\*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)](#input_toucheventcallback) | Input_TouchEventCallback | Defines the lifecycle callback for **TouchEvent**. If the callback is triggered, **TouchEvent** will be destroyed.|
| [typedef void (\*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)](#input_axiseventcallback) | Input_AxisEventCallback | Defines a lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.|
| [typedef void (\*Input_DeviceAddedCallback)(int32_t deviceId)](#input_deviceaddedcallback) | Input_DeviceAddedCallback | Defines a callback used to receive device insertion events.|
| [typedef void (\*Input_DeviceRemovedCallback)(int32_t deviceId)](#input_deviceremovedcallback) | Input_DeviceRemovedCallback | Defines a callback used to receive device removal events.|
| [typedef void (\*Input_InjectAuthorizeCallback)(Input_InjectionStatus authorizedStatus)](#input_injectauthorizecallback) | Input_InjectAuthorizeCallback | Defines a callback used to receive the injection permission authorization status.|
| [Input_Result OH_Input_GetKeyState(struct Input_KeyState* keyState)](#oh_input_getkeystate) | - | Queries a key status enum object.|
| [struct Input_KeyState* OH_Input_CreateKeyState()](#oh_input_createkeystate) | - | Creates a key status enum object. You can call [OH_Input_DestroyKeyState](#oh_input_destroykeystate) to destroy a key status enum object.|
| [void OH_Input_DestroyKeyState(struct Input_KeyState** keyState)](#oh_input_destroykeystate) | - | Destroys a key status enum object.|
| [void OH_Input_SetKeyCode(struct Input_KeyState* keyState, int32_t keyCode)](#oh_input_setkeycode) | - | Sets the key value of a key status enum object.|
| [int32_t OH_Input_GetKeyCode(const struct Input_KeyState* keyState)](#oh_input_getkeycode) | - | Obtains the key value of a key status enum object.|
| [void OH_Input_SetKeyPressed(struct Input_KeyState* keyState, int32_t keyAction)](#oh_input_setkeypressed) | - | Sets whether the key specific to a key status enum object is pressed.|
| [int32_t OH_Input_GetKeyPressed(const struct Input_KeyState* keyState)](#oh_input_getkeypressed) | - | Checks whether the key specific to a key status enum object is pressed.|
| [void OH_Input_SetKeySwitch(struct Input_KeyState* keyState, int32_t keySwitch)](#oh_input_setkeyswitch) | - | Sets the key switch of the key status enum object.|
| [int32_t OH_Input_GetKeySwitch(const struct Input_KeyState* keyState)](#oh_input_getkeyswitch) | - | Obtains the key switch of the key status enum object.|
| [int32_t OH_Input_InjectKeyEvent(const struct Input_KeyEvent* keyEvent)](#oh_input_injectkeyevent) | - | Injects a key event.|
| [struct Input_KeyEvent* OH_Input_CreateKeyEvent()](#oh_input_createkeyevent) | - | Creates a key event object. You can call [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent) to destroy a key event object.|
| [void OH_Input_DestroyKeyEvent(struct Input_KeyEvent** keyEvent)](#oh_input_destroykeyevent) | - | Destroys a key event object.|
| [void OH_Input_SetKeyEventAction(struct Input_KeyEvent* keyEvent, int32_t action)](#oh_input_setkeyeventaction) | - | Sets the key event type.|
| [int32_t OH_Input_GetKeyEventAction(const struct Input_KeyEvent* keyEvent)](#oh_input_getkeyeventaction) | - | Obtains the key event type.|
| [void OH_Input_SetKeyEventKeyCode(struct Input_KeyEvent* keyEvent, int32_t keyCode)](#oh_input_setkeyeventkeycode) | - | Sets the key code value for a key event.|
| [int32_t OH_Input_GetKeyEventKeyCode(const struct Input_KeyEvent* keyEvent)](#oh_input_getkeyeventkeycode) | - | Obtains the key code value of a key event.|
| [void OH_Input_SetKeyEventActionTime(struct Input_KeyEvent* keyEvent, int64_t actionTime)](#oh_input_setkeyeventactiontime) | - | Sets the time when a key event occurs.|
| [int64_t OH_Input_GetKeyEventActionTime(const struct Input_KeyEvent* keyEvent)](#oh_input_getkeyeventactiontime) | - | Obtains the time when a key event occurs.|
| [void OH_Input_SetKeyEventWindowId(struct Input_KeyEvent* keyEvent, int32_t windowId)](#oh_input_setkeyeventwindowid) | - | Sets the window ID of a key event.|
| [int32_t OH_Input_GetKeyEventWindowId(const struct Input_KeyEvent* keyEvent)](#oh_input_getkeyeventwindowid) | - | Obtains the window ID of a key event.|
| [void OH_Input_SetKeyEventDisplayId(struct Input_KeyEvent* keyEvent, int32_t displayId)](#oh_input_setkeyeventdisplayid) | - | Sets the screen ID of a key event.|
| [int32_t OH_Input_GetKeyEventDisplayId(const struct Input_KeyEvent* keyEvent)](#oh_input_getkeyeventdisplayid) | - | Obtains the screen ID of a key event.|
| [struct Input_MouseEvent* OH_Input_CreateMouseEvent()](#oh_input_createmouseevent) | - | Creates a mouse event object. You can call [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent) to destroy a mouse event object.|
| [void OH_Input_DestroyMouseEvent(struct Input_MouseEvent** mouseEvent)](#oh_input_destroymouseevent) | - | Destroys a mouse event object.|
| [void OH_Input_SetMouseEventAction(struct Input_MouseEvent* mouseEvent, int32_t action)](#oh_input_setmouseeventaction) | - | Sets the action for a mouse event.|
| [int32_t OH_Input_GetMouseEventAction(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventaction) | - | Obtains the action of a mouse event.|
| [void OH_Input_SetMouseEventDisplayX(struct Input_MouseEvent* mouseEvent, int32_t displayX)](#oh_input_setmouseeventdisplayx) | - | Sets the X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_GetMouseEventDisplayX(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventdisplayx) | - | Obtains the X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [void OH_Input_SetMouseEventDisplayY(struct Input_MouseEvent* mouseEvent, int32_t displayY)](#oh_input_setmouseeventdisplayy) | - | Sets the Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_GetMouseEventDisplayY(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventdisplayy) | - | Obtains the Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [void OH_Input_SetMouseEventButton(struct Input_MouseEvent* mouseEvent, int32_t button)](#oh_input_setmouseeventbutton) | - | Sets the button for a mouse event.|
| [int32_t OH_Input_GetMouseEventButton(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventbutton) | - | Obtains the button of a mouse event.|
| [void OH_Input_SetMouseEventAxisType(struct Input_MouseEvent* mouseEvent, int32_t axisType)](#oh_input_setmouseeventaxistype) | - | Sets the axis type for a mouse event.|
| [int32_t OH_Input_GetMouseEventAxisType(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventaxistype) | - | Obtains the axis type of a mouse event.|
| [void OH_Input_SetMouseEventAxisValue(struct Input_MouseEvent* mouseEvent, float axisValue)](#oh_input_setmouseeventaxisvalue) | - | Sets the axis value for a mouse axis event.|
| [float OH_Input_GetMouseEventAxisValue(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventaxisvalue) | - | Obtains the axis value of a mouse axis event.|
| [void OH_Input_SetMouseEventActionTime(struct Input_MouseEvent* mouseEvent, int64_t actionTime)](#oh_input_setmouseeventactiontime) | - | Sets the time when a mouse event occurs.|
| [int64_t OH_Input_GetMouseEventActionTime(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventactiontime) | - | Obtains the time when a mouse event occurs.|
| [void OH_Input_SetMouseEventWindowId(struct Input_MouseEvent* mouseEvent, int32_t windowId)](#oh_input_setmouseeventwindowid) | - | Sets the window ID of a mouse event.|
| [int32_t OH_Input_GetMouseEventWindowId(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventwindowid) | - | Obtains the window ID of a mouse event.|
| [void OH_Input_SetMouseEventDisplayId(struct Input_MouseEvent* mouseEvent, int32_t displayId)](#oh_input_setmouseeventdisplayid) | - | Sets the screen ID of a mouse event.|
| [struct Input_TouchEvent* OH_Input_CreateTouchEvent()](#oh_input_createtouchevent) | - | Creates a **TouchEvent** object. You can call [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent) to destroy a touch event object.|
| [void OH_Input_DestroyTouchEvent(struct Input_TouchEvent** touchEvent)](#oh_input_destroytouchevent) | - | Destroys a **TouchEvent** object.|
| [void OH_Input_SetTouchEventAction(struct Input_TouchEvent* touchEvent, int32_t action)](#oh_input_settoucheventaction) | - | Sets the action of a touch event.|
| [int32_t OH_Input_GetTouchEventAction(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventaction) | - | Obtains the action of a touch event.|
| [void OH_Input_SetTouchEventFingerId(struct Input_TouchEvent* touchEvent, int32_t id)](#oh_input_settoucheventfingerid) | - | Sets the finger ID of a touch event.|
| [int32_t OH_Input_GetTouchEventFingerId(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventfingerid) | - | Obtains the finger ID of a touch event.|
| [void OH_Input_SetTouchEventDisplayX(struct Input_TouchEvent* touchEvent, int32_t displayX)](#oh_input_settoucheventdisplayx) | - | Sets the X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_GetTouchEventDisplayX(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventdisplayx) | - | Obtains the X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [void OH_Input_SetTouchEventDisplayY(struct Input_TouchEvent* touchEvent, int32_t displayY)](#oh_input_settoucheventdisplayy) | - | Sets the Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_GetTouchEventDisplayY(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventdisplayy) | - | Obtains the Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [void OH_Input_SetTouchEventActionTime(struct Input_TouchEvent* touchEvent, int64_t actionTime)](#oh_input_settoucheventactiontime) | - | Sets the time when a touch event occurs.|
| [int64_t OH_Input_GetTouchEventActionTime(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventactiontime) | - | Obtains the time when a touch event occurs.|
| [void OH_Input_SetTouchEventWindowId(struct Input_TouchEvent* touchEvent, int32_t windowId)](#oh_input_settoucheventwindowid) | - | Sets the window ID of a touch event.|
| [int32_t OH_Input_GetTouchEventWindowId(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventwindowid) | - | Obtains the window ID of a touch event.|
| [void OH_Input_SetTouchEventDisplayId(struct Input_TouchEvent* touchEvent, int32_t displayId)](#oh_input_settoucheventdisplayid) | - | Sets the screen ID of a touch event.|
| [int32_t OH_Input_GetTouchEventDisplayId(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventdisplayid) | - | Obtains the screen ID of a touch event.|
| [void OH_Input_CancelInjection()](#oh_input_cancelinjection) | - | Stops event injection and revokes authorization.|
| [Input_Result OH_Input_RequestInjection(Input_InjectAuthorizeCallback callback)](#oh_input_requestinjection) | - | Requests the permission for [OH_Input_InjectKeyEvent](capi-oh-input-manager-h.md#oh_input_injectkeyevent), [OH_Input_InjectTouchEvent](capi-oh-input-manager-h.md#oh_input_injecttouchevent), and [OH_Input_InjectMouseEvent](capi-oh-input-manager-h.md#oh_input_injectmouseevent).|
| [Input_Result OH_Input_QueryAuthorizedStatus(Input_InjectionStatus* status)](#oh_input_queryauthorizedstatus) | - | Queries the injection permission authorization status of the current application.|
| [Input_AxisEvent* OH_Input_CreateAxisEvent(void)](#oh_input_createaxisevent) | - | Creates an axis event object. You can call [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent) to destroy an axis event object.|
| [Input_Result OH_Input_DestroyAxisEvent(Input_AxisEvent** axisEvent)](#oh_input_destroyaxisevent) | - | Destroys an axis event object.|
| [Input_Result OH_Input_SetAxisEventAction(Input_AxisEvent* axisEvent, InputEvent_AxisAction action)](#oh_input_setaxiseventaction) | - | Sets the action for an axis event.|
| [Input_Result OH_Input_GetAxisEventAction(const Input_AxisEvent* axisEvent, InputEvent_AxisAction *action)](#oh_input_getaxiseventaction) | - | Obtains the action of an axis event.|
| [Input_Result OH_Input_SetAxisEventDisplayX(Input_AxisEvent* axisEvent, float displayX)](#oh_input_setaxiseventdisplayx) | - | Sets the X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [Input_Result OH_Input_GetAxisEventDisplayX(const Input_AxisEvent* axisEvent, float* displayX)](#oh_input_getaxiseventdisplayx) | - | Obtains the X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [Input_Result OH_Input_SetAxisEventDisplayY(Input_AxisEvent* axisEvent, float displayY)](#oh_input_setaxiseventdisplayy) | - | Sets the Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [Input_Result OH_Input_GetAxisEventDisplayY(const Input_AxisEvent* axisEvent, float* displayY)](#oh_input_getaxiseventdisplayy) | - | Obtains the Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [Input_Result OH_Input_SetAxisEventAxisValue(Input_AxisEvent* axisEvent,InputEvent_AxisType axisType, double axisValue)](#oh_input_setaxiseventaxisvalue) | - | Sets the axis value of the axis type specified by the axis event.|
| [Input_Result OH_Input_GetAxisEventAxisValue(const Input_AxisEvent* axisEvent,InputEvent_AxisType axisType, double* axisValue)](#oh_input_getaxiseventaxisvalue) | - | Obtains the axis value for the specified axis type of the axis event.|
| [Input_Result OH_Input_SetAxisEventActionTime(Input_AxisEvent* axisEvent, int64_t actionTime)](#oh_input_setaxiseventactiontime) | - | Sets the time when an axis event occurs.|
| [Input_Result OH_Input_GetAxisEventActionTime(const Input_AxisEvent* axisEvent, int64_t* actionTime)](#oh_input_getaxiseventactiontime) | - | Obtains the time when an axis event occurs.|
| [Input_Result OH_Input_SetAxisEventType(Input_AxisEvent* axisEvent, InputEvent_AxisEventType axisEventType)](#oh_input_setaxiseventtype) | - | Sets the axis event type.|
| [Input_Result OH_Input_GetAxisEventType(const Input_AxisEvent* axisEvent, InputEvent_AxisEventType* axisEventType)](#oh_input_getaxiseventtype) | - | Obtains the axis event type.|
| [Input_Result OH_Input_SetAxisEventSourceType(Input_AxisEvent* axisEvent, InputEvent_SourceType sourceType)](#oh_input_setaxiseventsourcetype) | - | Sets the axis event source type.|
| [Input_Result OH_Input_GetAxisEventSourceType(const Input_AxisEvent* axisEvent, InputEvent_SourceType* sourceType)](#oh_input_getaxiseventsourcetype) | - | Obtains the axis event source type.|
| [Input_Result OH_Input_SetAxisEventWindowId(Input_AxisEvent* axisEvent, int32_t windowId)](#oh_input_setaxiseventwindowid) | - | Sets the window ID of an axis event.|
| [Input_Result OH_Input_GetAxisEventWindowId(const Input_AxisEvent* axisEvent, int32_t* windowId)](#oh_input_getaxiseventwindowid) | - | Obtains the window ID of an axis event.|
| [Input_Result OH_Input_SetAxisEventDisplayId(Input_AxisEvent* axisEvent, int32_t displayId)](#oh_input_setaxiseventdisplayid) | - | Sets the screen ID of an axis event.|
| [Input_Result OH_Input_GetAxisEventDisplayId(const Input_AxisEvent* axisEvent, int32_t* displayId)](#oh_input_getaxiseventdisplayid) | - | Obtains the screen ID of an axis event.|
| [Input_Result OH_Input_AddKeyEventMonitor(Input_KeyEventCallback callback)](#oh_input_addkeyeventmonitor) | - | Adds a listener for key events.|
| [Input_Result OH_Input_AddMouseEventMonitor(Input_MouseEventCallback callback)](#oh_input_addmouseeventmonitor) | - | Adds a listener for mouse events, including mouse click and movement events, but not scroll wheel events. Scroll wheel events are axis events.|
| [Input_Result OH_Input_AddTouchEventMonitor(Input_TouchEventCallback callback)](#oh_input_addtoucheventmonitor) | - | Adds a listener for touch events.|
| [Input_Result OH_Input_AddAxisEventMonitorForAll(Input_AxisEventCallback callback)](#oh_input_addaxiseventmonitorforall) | - | Adds a listener for all types of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|
| [Input_Result OH_Input_AddAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback)](#oh_input_addaxiseventmonitor) | - | Adds a listener for the specified type of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|
| [Input_Result OH_Input_RemoveKeyEventMonitor(Input_KeyEventCallback callback)](#oh_input_removekeyeventmonitor) | - | Removes the listener for key events.|
| [Input_Result OH_Input_RemoveMouseEventMonitor(Input_MouseEventCallback callback)](#oh_input_removemouseeventmonitor) | - | Removes the listener for mouse events.|
| [Input_Result OH_Input_RemoveTouchEventMonitor(Input_TouchEventCallback callback)](#oh_input_removetoucheventmonitor) | - | Removes the listener for touch events.|
| [Input_Result OH_Input_RemoveAxisEventMonitorForAll(Input_AxisEventCallback callback)](#oh_input_removeaxiseventmonitorforall) | - | Removes the listener for all types of axis events.|
| [Input_Result OH_Input_RemoveAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback)](#oh_input_removeaxiseventmonitor) | - | Removes the listener for the specified type of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|
| [Input_Result OH_Input_AddKeyEventInterceptor(Input_KeyEventCallback callback, Input_InterceptorOptions *option)](#oh_input_addkeyeventinterceptor) | - | Adds an interceptor for key events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application gains focus.|
| [Input_Result OH_Input_AddInputEventInterceptor(Input_InterceptorEventCallback *callback,Input_InterceptorOptions *option)](#oh_input_addinputeventinterceptor) | - | Adds an interceptor for input events, including mouse, touch, and axis events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application window is hit.|
| [Input_Result OH_Input_RemoveKeyEventInterceptor(void)](#oh_input_removekeyeventinterceptor) | - | Removes the interceptor for key events.|
| [Input_Result OH_Input_RemoveInputEventInterceptor(void)](#oh_input_removeinputeventinterceptor) | - | Removes the interceptor for input events, including mouse, touch, and axis events.|
| [Input_Result OH_Input_GetIntervalSinceLastInput(int64_t *timeInterval)](#oh_input_getintervalsincelastinput) | - | Obtains the interval since the last system input event.|
| [Input_Hotkey *OH_Input_CreateHotkey(void)](#oh_input_createhotkey) | - | Creates a hotkey object. You can call [OH_Input_DestroyHotkey](#oh_input_destroyhotkey) to destroy a hotkey object.|
| [void OH_Input_DestroyHotkey(Input_Hotkey **hotkey)](#oh_input_destroyhotkey) | - | Destroys a hotkey object.|
| [void OH_Input_SetPreKeys(Input_Hotkey *hotkey, int32_t *preKeys, int32_t size)](#oh_input_setprekeys) | - | Sets the modifier key.|
| [Input_Result OH_Input_GetPreKeys(const Input_Hotkey *hotkey, int32_t **preKeys, int32_t *preKeyCount)](#oh_input_getprekeys) | - | Obtains the modifier key.|
| [void OH_Input_SetFinalKey(Input_Hotkey* hotkey, int32_t finalKey)](#oh_input_setfinalkey) | - | Sets the modified key.|
| [Input_Result OH_Input_GetFinalKey(const Input_Hotkey* hotkey, int32_t *finalKeyCode)](#oh_input_getfinalkey) | - | Obtains the modified key.|
| [Input_Hotkey **OH_Input_CreateAllSystemHotkeys(int32_t count)](#oh_input_createallsystemhotkeys) | - | Creates an [Input_Hotkey](capi-input-input-hotkey.md) array. You can call [OH_Input_DestroyAllSystemHotkeys](#oh_input_destroyallsystemhotkeys) to destroy the array of the [Input_Hotkey](capi-input-input-hotkey.md) instance and reclaim the memory.|
| [void OH_Input_DestroyAllSystemHotkeys(Input_Hotkey **hotkeys, int32_t count)](#oh_input_destroyallsystemhotkeys) | - | Destroys an [Input_Hotkey](capi-input-input-hotkey.md) array and reclaims the memory.|
| [Input_Result OH_Input_GetAllSystemHotkeys(Input_Hotkey **hotkey, int32_t *count)](#oh_input_getallsystemhotkeys) | - | Obtains all configured hotkeys.|
| [void OH_Input_SetRepeat(Input_Hotkey* hotkey, bool isRepeat)](#oh_input_setrepeat) | - | Specifies whether to report repeated key events.|
| [Input_Result OH_Input_GetRepeat(const Input_Hotkey* hotkey, bool *isRepeat)](#oh_input_getrepeat) | - | Checks whether to report repeated key events.|
| [Input_Result OH_Input_AddHotkeyMonitor(const Input_Hotkey* hotkey, Input_HotkeyCallback callback)](#oh_input_addhotkeymonitor) | - | Subscribes to hotkey events. This API is not applicable to wearables and lite wearables.|
| [Input_Result OH_Input_RemoveHotkeyMonitor(const Input_Hotkey* hotkey, Input_HotkeyCallback callback)](#oh_input_removehotkeymonitor) | - | Unsubscribes from hotkey events.|
| [Input_Result OH_Input_RegisterDeviceListener(Input_DeviceListener* listener)](#oh_input_registerdevicelistener) | - | Registers a listener for device hot swap events.|
| [Input_Result OH_Input_UnregisterDeviceListener(Input_DeviceListener* listener)](#oh_input_unregisterdevicelistener) | - | Unregisters the listener for device hot swap events.|
| [Input_Result OH_Input_UnregisterDeviceListeners()](#oh_input_unregisterdevicelisteners) | - | Unregisters the listener for all device hot swap events.|
| [Input_Result OH_Input_GetDeviceIds(int32_t *deviceIds, int32_t inSize, int32_t *outSize)](#oh_input_getdeviceids) | - | Obtains the IDs of all input devices.|
| [Input_Result OH_Input_GetDevice(int32_t deviceId, Input_DeviceInfo **deviceInfo)](#oh_input_getdevice) | - | Obtains information about the input device.|
| [Input_DeviceInfo* OH_Input_CreateDeviceInfo(void)](#oh_input_createdeviceinfo) | - | Creates a **deviceInfo** object. You can call [OH_Input_DestroyDeviceInfo](#oh_input_destroydeviceinfo) to destroy an input device information object.|
| [void OH_Input_DestroyDeviceInfo(Input_DeviceInfo **deviceInfo)](#oh_input_destroydeviceinfo) | - | Destroys a **deviceInfo** object.|
| [Input_Result OH_Input_GetKeyboardType(int32_t deviceId, int32_t *keyboardType)](#oh_input_getkeyboardtype) | - | Obtains the keyboard type of the input device.|
| [Input_Result OH_Input_GetDeviceId(Input_DeviceInfo *deviceInfo, int32_t *id)](#oh_input_getdeviceid) | - | Obtains the ID of an input device.|
| [Input_Result OH_Input_GetDeviceName(Input_DeviceInfo *deviceInfo, char **name)](#oh_input_getdevicename) | - | Obtains the name of an input device.|
| [Input_Result OH_Input_GetCapabilities(Input_DeviceInfo *deviceInfo, int32_t *capabilities)](#oh_input_getcapabilities) | - | Obtains the capabilities of an input device, for example, a touchscreen, touchpad, or keyboard.|
| [Input_Result OH_Input_GetDeviceVersion(Input_DeviceInfo *deviceInfo, int32_t *version)](#oh_input_getdeviceversion) | - | Obtains the version information of an input device.|
| [Input_Result OH_Input_GetDeviceProduct(Input_DeviceInfo *deviceInfo, int32_t *product)](#oh_input_getdeviceproduct) | - | Obtains the product information of an input device.|
| [Input_Result OH_Input_GetDeviceVendor(Input_DeviceInfo *deviceInfo, int32_t *vendor)](#oh_input_getdevicevendor) | - | Obtains the vendor information of an input device.|
| [Input_Result OH_Input_GetDeviceAddress(Input_DeviceInfo *deviceInfo, char **address)](#oh_input_getdeviceaddress) | - | Obtains the physical address of an input device.|
| [Input_Result OH_Input_GetFunctionKeyState(int32_t keyCode, int32_t *state)](#oh_input_getfunctionkeystate) | - | Obtains the function key status.|
| [int32_t OH_Input_InjectTouchEvent(const struct Input_TouchEvent* touchEvent)](#oh_input_injecttouchevent) | - | Injects a touch event by using coordinates in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_InjectMouseEvent(const struct Input_MouseEvent* mouseEvent)](#oh_input_injectmouseevent) | - | Injects a mouse event by using coordinates in the relative coordinate system with the upper-left corner of the specified screen as the origin.|
| [int32_t OH_Input_GetMouseEventDisplayId(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventdisplayid) | - | Obtains the screen ID of a mouse event.|
| [Input_Result OH_Input_QueryMaxTouchPoints(int32_t *count)](#oh_input_querymaxtouchpoints) | - | Queries the maximum number of touch points supported by the device.|
| [int32_t OH_Input_InjectMouseEventGlobal(const struct Input_MouseEvent* mouseEvent)](#oh_input_injectmouseeventglobal) | - | Injects a mouse event by using coordinates in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [void OH_Input_SetMouseEventGlobalX(struct Input_MouseEvent* mouseEvent, int32_t globalX)](#oh_input_setmouseeventglobalx) | - | Sets the X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [int32_t OH_Input_GetMouseEventGlobalX(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventglobalx) | - | Obtains the X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [void OH_Input_SetMouseEventGlobalY(struct Input_MouseEvent* mouseEvent, int32_t globalY)](#oh_input_setmouseeventglobaly) | - | Sets the Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [int32_t OH_Input_GetMouseEventGlobalY(const struct Input_MouseEvent* mouseEvent)](#oh_input_getmouseeventglobaly) | - | Obtains the Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [int32_t OH_Input_InjectTouchEventGlobal(const struct Input_TouchEvent* touchEvent)](#oh_input_injecttoucheventglobal) | - | Injects a touch event by using coordinates in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [void OH_Input_SetTouchEventGlobalX(struct Input_TouchEvent* touchEvent, int32_t globalX)](#oh_input_settoucheventglobalx) | - | Sets the X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [int32_t OH_Input_GetTouchEventGlobalX(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventglobalx) | - | Obtains the X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [void OH_Input_SetTouchEventGlobalY(struct Input_TouchEvent* touchEvent, int32_t globalY)](#oh_input_settoucheventglobaly) | - | Sets the Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [int32_t OH_Input_GetTouchEventGlobalY(const struct Input_TouchEvent* touchEvent)](#oh_input_gettoucheventglobaly) | - | Obtains the Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [Input_Result OH_Input_SetAxisEventGlobalX(struct Input_AxisEvent* axisEvent, int32_t globalX)](#oh_input_setaxiseventglobalx) | - | Sets the X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [Input_Result OH_Input_GetAxisEventGlobalX(const Input_AxisEvent* axisEvent, int32_t* globalX)](#oh_input_getaxiseventglobalx) | - | Obtains the X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [Input_Result OH_Input_SetAxisEventGlobalY(struct Input_AxisEvent* axisEvent, int32_t globalY)](#oh_input_setaxiseventglobaly) | - | Sets the Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [Input_Result OH_Input_GetAxisEventGlobalY(const Input_AxisEvent* axisEvent, int32_t* globalY)](#oh_input_getaxiseventglobaly) | - | Obtains the Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|
| [Input_Result OH_Input_GetPointerLocation(int32_t *displayId, double *displayX, double *displayY)](#oh_input_getpointerlocation) | - | Obtains the coordinates of the mouse pointer on the screen.|
| [Input_Result OH_Input_GetKeyEventId(const struct Input_KeyEvent* keyEvent, int32_t* eventId)](#oh_input_getkeyeventid) | - | Obtains the ID of a key event.|
| [Input_Result OH_Input_AddKeyEventHook(Input_KeyEventCallback callback)](#oh_input_addkeyeventhook) | - | Adds a hook function for key event interception.|
| [Input_Result OH_Input_RemoveKeyEventHook(Input_KeyEventCallback callback)](#oh_input_removekeyeventhook) | - | Removes the hook function for key event interception.|
| [Input_Result OH_Input_DispatchToNextHandler(int32_t eventId)](#oh_input_dispatchtonexthandler) | - | Redispatches key events.|
| [Input_Result OH_Input_SetPointerVisible(bool visible)](#oh_input_setpointervisible) | - | Sets the visible status of the mouse pointer in the current window.|
| [Input_Result OH_Input_GetPointerStyle(int32_t windowId, int32_t *pointerStyle)](#oh_input_getpointerstyle) | - | Obtains the mouse pointer style of the specified window.|
| [Input_Result OH_Input_SetPointerStyle(int32_t windowId, int32_t pointerStyle)](#oh_input_setpointerstyle) | - | Sets the mouse pointer style of the specified window.|
| [Input_CustomCursor* OH_Input_CustomCursor_Create(OH_PixelmapNative* pixelMap, int32_t anchorX, int32_t anchorY)](#oh_input_customcursor_create) | - | Creates a custom mouse pointer object. You can call [OH_Input_CustomCursor_Destroy](#oh_input_customcursor_destroy) to destroy a custom mouse pointer resource object.|
| [void OH_Input_CustomCursor_Destroy(Input_CustomCursor** customCursor)](#oh_input_customcursor_destroy) | - | Destroys a custom mouse pointer object.|
| [Input_Result OH_Input_CustomCursor_GetPixelMap(Input_CustomCursor* customCursor, OH_PixelmapNative** pixelMap)](#oh_input_customcursor_getpixelmap) | - | Obtains the pixel map of a custom mouse pointer object.|
| [Input_Result OH_Input_CustomCursor_GetAnchor(Input_CustomCursor* customCursor, int32_t* anchorX, int32_t* anchorY)](#oh_input_customcursor_getanchor) | - | Obtains the focus coordinates of a custom mouse pointer object.|
| [Input_CursorConfig* OH_Input_CursorConfig_Create(bool followSystem)](#oh_input_cursorconfig_create) | - | Creates a custom mouse pointer configuration object. You can call [OH_Input_CursorConfig_Destroy](#oh_input_cursorconfig_destroy) to destroy a custom mouse pointer configuration object.|
| [void OH_Input_CursorConfig_Destroy(Input_CursorConfig** cursorConfig)](#oh_input_cursorconfig_destroy) | - | Destroys a custom mouse pointer configuration object.|
| [Input_Result OH_Input_CursorConfig_IsFollowSystem(Input_CursorConfig *cursorConfig, bool *followSystem)](#oh_input_cursorconfig_isfollowsystem) | - | Queries whether the custom mouse pointer configuration follows the system setting to adjust the pointer size.|
| [Input_Result OH_Input_SetCustomCursor(int32_t windowId, Input_CustomCursor* customCursor, Input_CursorConfig* cursorConfig)](#oh_input_setcustomcursor) | - | Sets the custom mouse pointer style.|
| [struct Input_CursorInfo* OH_Input_CursorInfo_Create()](#oh_input_cursorinfo_create) | - | Creates a mouse pointer information object. You can call [OH_Input_CursorInfo_Destroy](#oh_input_cursorinfo_destroy) to destroy a mouse pointer information object.|
| [void OH_Input_CursorInfo_Destroy(Input_CursorInfo** cursorInfo)](#oh_input_cursorinfo_destroy) | - | Destroys the mouse pointer information object.|
| [Input_Result OH_Input_CursorInfo_IsVisible(Input_CursorInfo* cursorInfo, bool* visible)](#oh_input_cursorinfo_isvisible) | - | Obtains the pointer visible status of the specified mouse pointer information object.|
| [Input_Result OH_Input_CursorInfo_GetStyle(Input_CursorInfo* cursorInfo, Input_PointerStyle* style)](#oh_input_cursorinfo_getstyle) | - |Obtains the pointer style of the specified mouse pointer information object.|
| [Input_Result OH_Input_CursorInfo_GetSizeLevel(Input_CursorInfo* cursorInfo, int32_t* sizeLevel)](#oh_input_cursorinfo_getsizelevel) | - | Obtains the pointer size level of the specified mouse pointer information object.|
| [Input_Result OH_Input_CursorInfo_GetColor(Input_CursorInfo* cursorInfo, uint32_t* color)](#oh_input_cursorinfo_getcolor) | - | Obtains the pointer color of the specified mouse pointer information object.|
| [Input_Result OH_Input_GetMouseEventCursorInfo(const struct Input_MouseEvent* mouseEvent, Input_CursorInfo* cursorInfo)](#oh_input_getmouseeventcursorinfo) | - | Obtains the mouse pointer information of the mouse event, including the pointer visible status, pointer style, pointer size level, and pointer color.|
| [Input_Result OH_Input_GetCursorInfo(Input_CursorInfo* cursorInfo, OH_PixelmapNative** pixelmap)](#oh_input_getcursorinfo) | - | Obtains the mouse pointer information, including the pointer visible status, pointer style, pointer size level, and pointer color. If the **pixelmap** parameter is not empty and the pointer style is [DEVELOPER_DEFINED_ICON](./capi-oh-pointer-style-h.md#input_pointerstyle), the **PixelMap** object of the pointer is returned.|

## Enum Description

### Input_KeyStateAction

```c
enum Input_KeyStateAction
```

**Description**

Provides the enum values of the key status.

**Since**: 12

| Enum| Description|
| -- | -- |
| KEY_DEFAULT = -1 | Default state.|
| KEY_PRESSED = 0 | Key press.|
| KEY_RELEASED = 1 | Key release.|
| KEY_SWITCH_ON = 2 | Key switch enabled.|
| KEY_SWITCH_OFF = 3 | Key switch disabled.|

### Input_KeyEventAction

```c
enum Input_KeyEventAction
```

**Description**

Provides the enum values of the key event type.

**Since**: 12

| Enum| Description|
| -- | -- |
| KEY_ACTION_CANCEL = 0 | Button action canceled.|
| KEY_ACTION_DOWN = 1 | Key press.|
| KEY_ACTION_UP = 2 | Key release.|

### Input_MouseEventAction

```c
enum Input_MouseEventAction
```

**Description**

Provides the enum values of mouse actions.

**Since**: 12

| Enum| Description|
| -- | -- |
| MOUSE_ACTION_CANCEL = 0 | Cancellation of the mouse action.|
| MOUSE_ACTION_MOVE = 1 | Moving of the mouse pointer.|
| MOUSE_ACTION_BUTTON_DOWN = 2 | Pressing of the mouse button.|
| MOUSE_ACTION_BUTTON_UP = 3 | Release of the mouse button.|
| MOUSE_ACTION_AXIS_BEGIN = 4 | Beginning of the mouse axis event.|
| MOUSE_ACTION_AXIS_UPDATE = 5 | Updating of the mouse axis event.|
| MOUSE_ACTION_AXIS_END = 6 | End of the mouse axis event.|

### InputEvent_MouseAxis

```c
enum InputEvent_MouseAxis
```

**Description**

Provides the enum values of mouse axis event types.

**Since**: 12

| Enum| Description|
| -- | -- |
| MOUSE_AXIS_SCROLL_VERTICAL = 0 | Vertical scroll axis.|
| MOUSE_AXIS_SCROLL_HORIZONTAL = 1 | Horizontal scroll axis.|

### Input_MouseEventButton

```c
enum Input_MouseEventButton
```

**Description**

Provides the enum values of mouse buttons.

**Since**: 12

| Enum| Description|
| -- | -- |
| MOUSE_BUTTON_NONE = -1 | Invalid button.|
| MOUSE_BUTTON_LEFT = 0 | Left button.|
| MOUSE_BUTTON_MIDDLE = 1 | Middle button.|
| MOUSE_BUTTON_RIGHT = 2 | Right button.|
| MOUSE_BUTTON_FORWARD = 3 | Forward button.|
| MOUSE_BUTTON_BACK = 4 | Back button.|

### Input_TouchEventAction

```c
enum Input_TouchEventAction
```

**Description**

Provides the enum values of touch actions.

**Since**: 12

| Enum| Description|
| -- | -- |
| TOUCH_ACTION_CANCEL = 0 | Touch cancellation.|
| TOUCH_ACTION_DOWN = 1 | Touch press.|
| TOUCH_ACTION_MOVE = 2 | Touch moving.|
| TOUCH_ACTION_UP = 3 | Touch release.|

### Input_InjectionStatus

```c
enum Input_InjectionStatus
```

**Description**

Provides the enum values of injection permission states.

**Since**: 20

| Enum| Description|
| -- | -- |
| UNAUTHORIZED = 0 | Permission not granted.|
| AUTHORIZING = 1 | Permission being granted.|
| AUTHORIZED = 2 | Permission granted.|

### InputEvent_SourceType

```c
enum InputEvent_SourceType
```

**Description**

Provides the enum values of event source types.

**Since**: 12

| Enum| Description|
| -- | -- |
| SOURCE_TYPE_MOUSE = 1 | Source that generates events similar to mouse pointer movement, button press and release, and wheel scrolling.|
| SOURCE_TYPE_TOUCHSCREEN = 2 | Source that generates a touchscreen multi-touch event.|
| SOURCE_TYPE_TOUCHPAD = 3 | Source that generates a touchpad multi-touch event.|

### Input_KeyboardType

```c
enum Input_KeyboardType
```

**Description**

Provides the enum values of keyboard types of the input device.

**Since**: 13

| Enum| Description|
| -- | -- |
| KEYBOARD_TYPE_NONE = 0 | Keyboard without keys.|
| KEYBOARD_TYPE_UNKNOWN = 1 | Keyboard with unknown keys.|
| KEYBOARD_TYPE_ALPHABETIC = 2 | Full keyboard.|
| KEYBOARD_TYPE_DIGITAL = 3 | Numeric keypad.|
| KEYBOARD_TYPE_STYLUS = 4 | Stylus.|
| KEYBOARD_TYPE_REMOTE_CONTROL = 5 | Remote control.|

### Input_Result

```c
enum Input_Result
```

**Description**

Provides the enum values of error codes.

**Since**: 12

| Enum| Description|
| -- | -- |
| INPUT_SUCCESS = 0 | Operation succeeded.|
| INPUT_PERMISSION_DENIED = 201 | Permission verification failed.|
| INPUT_NOT_SYSTEM_APPLICATION = 202 | Non-system application.|
| INPUT_PARAMETER_ERROR = 401 | Parameter check fails.|
| INPUT_DEVICE_NOT_SUPPORTED = 801 | Function not supported.|
| INPUT_SERVICE_EXCEPTION = 3800001 | Service error.|
| INPUT_REPEAT_INTERCEPTOR = 4200001 | Interceptor repeatedly created.|
| INPUT_OCCUPIED_BY_SYSTEM = 4200002 | Input device occupied by a system application.<br>**Since**: 14|
| INPUT_OCCUPIED_BY_OTHER = 4200003 | Input device occupied by another application.<br>**Since**: 14|
| INPUT_KEYBOARD_DEVICE_NOT_EXIST = 3900002 |  Keyboard not connected.<br>**Since**: 15|
| INPUT_INJECTION_AUTHORIZING = 3900005 |  Authorization in progress.<br>**Since**: 20|
| INPUT_INJECTION_OPERATION_FREQUENT = 3900006 |  Repeated request.<br>**Since**: 20|
| INPUT_INJECTION_AUTHORIZED = 3900007 |  Permission granted to the current application.<br>**Since**: 20|
| INPUT_INJECTION_AUTHORIZED_OTHERS = 3900008 |  Permission granted to other applications.<br>**Since**: 20|
| INPUT_APP_NOT_FOCUSED = 3900009 |  Application not in focus.<br>**Since**: 20|
| INPUT_DEVICE_NO_POINTER = 3900010 |  No mouse device.<br>**Since**: 20|
| INPUT_INVALID_WINDOWID = 26500001 |  Invalid window ID.<br>**Since**: 22|

## Function Description

### Input_HotkeyCallback()

```c
typedef void (*Input_HotkeyCallback)(Input_Hotkey* hotkey)
```

**Description**

Defines the callback used to return hotkey events.

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|

### Input_KeyEventCallback()

```c
typedef void (*Input_KeyEventCallback)(const Input_KeyEvent* keyEvent)
```

**Description**

Defines a lifecycle callback for **keyEvent**. If the callback is triggered, **keyEvent** will be destroyed.

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

### Input_MouseEventCallback()

```c
typedef void (*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)
```

**Description**

Defines a lifecycle callback for **mouseEvent**. If the callback is triggered, **mouseEvent** will be destroyed.

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

### Input_TouchEventCallback()

```c
typedef void (*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)
```

**Description**

Defines the lifecycle callback for **TouchEvent**. If the callback is triggered, **TouchEvent** will be destroyed.

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

### Input_AxisEventCallback()

```c
typedef void (*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)
```

**Description**

Defines a lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|

### Input_DeviceAddedCallback()

```c
typedef void (*Input_DeviceAddedCallback)(int32_t deviceId)
```

**Description**

Defines a callback used to receive device insertion events.

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|

### Input_DeviceRemovedCallback()

```c
typedef void (*Input_DeviceRemovedCallback)(int32_t deviceId)
```

**Description**

Defines a callback used to receive device removal events.

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|

### Input_InjectAuthorizeCallback()

```c
typedef void (*Input_InjectAuthorizeCallback)(Input_InjectionStatus authorizedStatus)
```

**Description**

Defines a callback used to receive the injection permission authorization status.

**Since**: 20


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_InjectionStatus](capi-oh-input-manager-h.md#input_injectionstatus) authorizedStatus | Injection permission authorization status.|

### OH_Input_GetKeyState()

```c
Input_Result OH_Input_GetKeyState(struct Input_KeyState* keyState)
```

**Description**

Queries a key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](#input_keystateaction).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br> an error code defined in [Input_Result](#input_result) otherwise.|

### OH_Input_CreateKeyState()

```c
struct Input_KeyState* OH_Input_CreateKeyState()
```

**Description**

Creates a key status enum object. You can call [OH_Input_DestroyKeyState](#oh_input_destroykeystate) to destroy a key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| struct | [Input_KeyState](capi-input-input-keystate.md) pointer object if the operation is successful; a null pointer otherwise.|

### OH_Input_DestroyKeyState()

```c
void OH_Input_DestroyKeyState(struct Input_KeyState** keyState)
```

**Description**

Destroys a key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyState](capi-input-input-keystate.md)** keyState | Key status enum object. For details, see [Input_KeyStateAction](#input_keystateaction).|

### OH_Input_SetKeyCode()

```c
void OH_Input_SetKeyCode(struct Input_KeyState* keyState, int32_t keyCode)
```

**Description**

Sets the key value of a key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](#input_keystateaction).|
| int32_t keyCode | Key code.|

### OH_Input_GetKeyCode()

```c
int32_t OH_Input_GetKeyCode(const struct Input_KeyState* keyState)
```

**Description**

Obtains the key value of a key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](capi-oh-input-manager-h.md#input_keystateaction).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Key value of the key status enum object.|

### OH_Input_SetKeyPressed()

```c
void OH_Input_SetKeyPressed(struct Input_KeyState* keyState, int32_t keyAction)
```

**Description**

Sets whether the key specific to a key status enum object is pressed.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](#input_keystateaction).|
| int32_t keyAction | Whether a key is pressed. For details, see [Input_KeyEventAction](#input_keyeventaction).|

### OH_Input_GetKeyPressed()

```c
int32_t OH_Input_GetKeyPressed(const struct Input_KeyState* keyState)
```

**Description**

Checks whether the key specific to a key status enum object is pressed.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](capi-oh-input-manager-h.md#input_keystateaction).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Key pressing status of the key status enum object.|

### OH_Input_SetKeySwitch()

```c
void OH_Input_SetKeySwitch(struct Input_KeyState* keyState, int32_t keySwitch)
```

**Description**

Sets the key switch of the key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](#input_keystateaction).|
| int32_t keySwitch | Key switch.|

### OH_Input_GetKeySwitch()

```c
int32_t OH_Input_GetKeySwitch(const struct Input_KeyState* keyState)
```

**Description**

Obtains the key switch of the key status enum object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyState](capi-input-input-keystate.md)* keyState | Key status enum object. For details, see [Input_KeyStateAction](capi-oh-input-manager-h.md#input_keystateaction).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Key switch of the key status enum object.|

### OH_Input_InjectKeyEvent()

```c
int32_t OH_Input_InjectKeyEvent(const struct Input_KeyEvent* keyEvent)
```

**Description**

Injects a key event.

This API does not take effect if the event injection permission is not granted.

Since API version 20, you are advised to use [OH_Input_RequestInjection](#oh_input_requestinjection) to request the required permission before calling this API. If the status returned by [OH_Input_QueryAuthorizedStatus](#oh_input_queryauthorizedstatus) is [AUTHORIZED](capi-oh-input-manager-h.md#input_injectionstatus), then you can call this API.<br>Since API version 22, if the key press event (**KEY_ACTION_DOWN**) of a modifier key (**KEYCODE_META_LEFT**, **KEYCODE_META_RIGHT**, **KEYCODE_CTRL_LEFT**, **KEYCODE_CTRL_RIGHT**, **KEYCODE_ALT_LEFT**, **KEYCODE_ALT_RIGHT**, **KEYCODE_SHIFT_LEFT**, **KEYCODE_SHIFT_RIGHT**, **KEYCODE_CAPS_LOCK**, **KEYCODE_SCROLL_LOCK**, or **KEYCODE_NUM_LOCK**) is injected, the release event (**KEY_ACTION_UP**) of the key needs to be injected in a timely manner to avoid the key being pressed for a long time.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent). You can call [OH_Input_SetKeyEventKeyCode](#oh_input_setkeyeventkeycode) and [OH_Input_SetKeyEventAction](#oh_input_setkeyeventaction) to set the key value and key event type of the key event object.<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Error code of the **OH_Input_InjectKeyEvent** function:<br>         - [INPUT_SUCCESS](capi-oh-input-manager-h.md#input_result) if the operation is successful;<br>         - [INPUT_PERMISSION_DENIED](capi-oh-input-manager-h.md#input_result) if the required permission is missing;<br>         - [INPUT_PARAMETER_ERROR](capi-oh-input-manager-h.md#input_result) if the input parameter is incorrect.|

### OH_Input_CreateKeyEvent()

```c
struct Input_KeyEvent* OH_Input_CreateKeyEvent()
```

**Description**

Creates a key event object. You can call [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent) to destroy a key event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| struct | [Input_KeyEvent](capi-input-input-keyevent.md) pointer object if the operation is successful; a null pointer otherwise.|

### OH_Input_DestroyKeyEvent()

```c
void OH_Input_DestroyKeyEvent(struct Input_KeyEvent** keyEvent)
```

**Description**

Destroys a key event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)** keyEvent | Key event object.|

### OH_Input_SetKeyEventAction()

```c
void OH_Input_SetKeyEventAction(struct Input_KeyEvent* keyEvent, int32_t action)
```

**Description**

Sets the key event type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int32_t action | Key event type. For details, see [Input_KeyEventAction](#input_keyeventaction).|

### OH_Input_GetKeyEventAction()

```c
int32_t OH_Input_GetKeyEventAction(const struct Input_KeyEvent* keyEvent)
```

**Description**

Obtains the key event action.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Key event type. For details, see [Input_KeyEventAction](#input_keyeventaction).|

### OH_Input_SetKeyEventKeyCode()

```c
void OH_Input_SetKeyEventKeyCode(struct Input_KeyEvent* keyEvent, int32_t keyCode)
```

**Description**

Sets the key code value for a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int32_t keyCode | Key value.|

### OH_Input_GetKeyEventKeyCode()

```c
int32_t OH_Input_GetKeyEventKeyCode(const struct Input_KeyEvent* keyEvent)
```

**Description**

Obtains the key code value of a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Key code. |

### OH_Input_SetKeyEventActionTime()

```c
void OH_Input_SetKeyEventActionTime(struct Input_KeyEvent* keyEvent, int64_t actionTime)
```

**Description**

Sets the time when a key event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int64_t actionTime | Key event timestamp, which is measured as the number of milliseconds that have elapsed since the Unix epoch.|

### OH_Input_GetKeyEventActionTime()

```c
int64_t OH_Input_GetKeyEventActionTime(const struct Input_KeyEvent* keyEvent)
```

**Description**

Obtains the time when a key event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when a key event occurs.|

### OH_Input_SetKeyEventWindowId()

```c
void OH_Input_SetKeyEventWindowId(struct Input_KeyEvent* keyEvent, int32_t windowId)
```

**Description**

Sets the window ID of a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int32_t windowId | Window ID of the key event.|

### OH_Input_GetKeyEventWindowId()

```c
int32_t OH_Input_GetKeyEventWindowId(const struct Input_KeyEvent* keyEvent)
```

**Description**

Obtains the window ID of a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Window ID of the key event.|

### OH_Input_GetKeyEventDisplayId()

```c
int32_t OH_Input_GetKeyEventDisplayId(const struct Input_KeyEvent* keyEvent)
```

**Description**

Obtains the screen ID of a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Screen ID of the key event.|

### OH_Input_SetKeyEventDisplayId()

```c
void OH_Input_SetKeyEventDisplayId(struct Input_KeyEvent* keyEvent, int32_t displayId)
```

**Description**

Sets the screen ID of a key event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int32_t displayId | Screen ID of the key event.|

### OH_Input_CreateMouseEvent()

```c
struct Input_MouseEvent* OH_Input_CreateMouseEvent()
```

**Description**

Creates a mouse event object. You can call [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent) to destroy a mouse event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| struct | [Input_MouseEvent](capi-input-input-mouseevent.md) pointer object if the operation is successful; a null pointer otherwise.|

### OH_Input_DestroyMouseEvent()

```c
void OH_Input_DestroyMouseEvent(struct Input_MouseEvent** mouseEvent)
```

**Description**

Destroys a mouse event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)** mouseEvent | Mouse event object.|

### OH_Input_SetMouseEventAction()

```c
void OH_Input_SetMouseEventAction(struct Input_MouseEvent* mouseEvent, int32_t action)
```

**Description**

Sets the action for a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t action | Mouse action. For details, see [Input_MouseEventAction](#input_mouseeventaction).|

### OH_Input_GetMouseEventAction()

```c
int32_t OH_Input_GetMouseEventAction(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the action of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Mouse action.|

### OH_Input_SetMouseEventDisplayX()

```c
void OH_Input_SetMouseEventDisplayX(struct Input_MouseEvent* mouseEvent, int32_t displayX)
```

**Description**

Sets the X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t displayX | X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_GetMouseEventDisplayX()

```c
int32_t OH_Input_GetMouseEventDisplayX(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | X coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_SetMouseEventDisplayY()

```c
void OH_Input_SetMouseEventDisplayY(struct Input_MouseEvent* mouseEvent, int32_t displayY)
```

**Description**

Sets the Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t displayY | Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_GetMouseEventDisplayY()

```c
int32_t OH_Input_GetMouseEventDisplayY(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Y coordinate of the mouse event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_SetMouseEventButton()

```c
void OH_Input_SetMouseEventButton(struct Input_MouseEvent* mouseEvent, int32_t button)
```

**Description**

Sets the button for a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t button | Mouse button. For details, see [Input_MouseEventButton](#input_mouseeventbutton).|

### OH_Input_GetMouseEventButton()

```c
int32_t OH_Input_GetMouseEventButton(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the button of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Mouse button. For details, see [Input_MouseEventButton](#input_mouseeventbutton).|

### OH_Input_SetMouseEventAxisType()

```c
void OH_Input_SetMouseEventAxisType(struct Input_MouseEvent* mouseEvent, int32_t axisType)
```

**Description**

Sets the axis type for a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t axisType | Mouse axis type, such as vertical axis and horizontal axis. For details, see [InputEvent_MouseAxis](#inputevent_mouseaxis).|

### OH_Input_GetMouseEventAxisType()

```c
int32_t OH_Input_GetMouseEventAxisType(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the axis type of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Enumerates mouse axis types. For details, see [InputEvent_MouseAxis](#inputevent_mouseaxis).|

### OH_Input_SetMouseEventAxisValue()

```c
void OH_Input_SetMouseEventAxisValue(struct Input_MouseEvent* mouseEvent, float axisValue)
```

**Description**

Sets the axis value for a mouse axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| float axisValue | Axis event value. A positive number means scrolling forward (for example, 1.0 equals one unit forward), and a negative number means scrolling backward (for example, -1.0 equals one unit backward).|

### OH_Input_GetMouseEventAxisValue()

```c
float OH_Input_GetMouseEventAxisValue(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the axis value of a mouse axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| float | Axis event value.|

### OH_Input_SetMouseEventActionTime()

```c
void OH_Input_SetMouseEventActionTime(struct Input_MouseEvent* mouseEvent, int64_t actionTime)
```

**Description**

Sets the time when a mouse event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int64_t actionTime | Mouse event timestamp, which is measured as the number of milliseconds that have elapsed since the Unix epoch.|

### OH_Input_GetMouseEventActionTime()

```c
int64_t OH_Input_GetMouseEventActionTime(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the time when a mouse event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when the mouse event occurs.|

### OH_Input_SetMouseEventWindowId()

```c
void OH_Input_SetMouseEventWindowId(struct Input_MouseEvent* mouseEvent, int32_t windowId)
```

**Description**

Sets the window ID of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t windowId | Window ID of the mouse event.|

### OH_Input_GetMouseEventWindowId()

```c
int32_t OH_Input_GetMouseEventWindowId(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the window ID of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Window ID of the mouse event.|

### OH_Input_SetMouseEventDisplayId()

```c
void OH_Input_SetMouseEventDisplayId(struct Input_MouseEvent* mouseEvent, int32_t displayId)
```

**Description**

Sets the screen ID of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t displayId | Screen ID of the mouse event.|

### OH_Input_CreateTouchEvent()

```c
struct Input_TouchEvent* OH_Input_CreateTouchEvent()
```

**Description**

Creates a **TouchEvent** object. You can call [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent) to destroy a touch event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| struct | [Input_TouchEvent](capi-input-input-touchevent.md) pointer object if the operation is successful; a null pointer otherwise.|

### OH_Input_DestroyTouchEvent()

```c
void OH_Input_DestroyTouchEvent(struct Input_TouchEvent** touchEvent)
```

**Description**

Destroys a **TouchEvent** object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)** touchEvent | **TouchEvent** object.|

### OH_Input_SetTouchEventAction()

```c
void OH_Input_SetTouchEventAction(struct Input_TouchEvent* touchEvent, int32_t action)
```

**Description**

Sets the action of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t action | Action of the touch event. For details, see [Input_TouchEventAction](#input_toucheventaction).|

### OH_Input_GetTouchEventAction()

```c
int32_t OH_Input_GetTouchEventAction(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the action of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Action of the touch event. For details, see [Input_TouchEventAction](#input_toucheventaction).|

### OH_Input_SetTouchEventFingerId()

```c
void OH_Input_SetTouchEventFingerId(struct Input_TouchEvent* touchEvent, int32_t id)
```

**Description**

Sets the finger ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t id | Finger ID of a touch event. The ID of the first finger touching the screen is 0, the second is 1, and so on incrementally.|

### OH_Input_GetTouchEventFingerId()

```c
int32_t OH_Input_GetTouchEventFingerId(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the finger ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Finger ID of a touch event. The ID of the first finger touching the screen is 0, the second is 1, and so on incrementally.|

### OH_Input_SetTouchEventDisplayX()

```c
void OH_Input_SetTouchEventDisplayX(struct Input_TouchEvent* touchEvent, int32_t displayX)
```

**Description**

Sets the X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t displayX | X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_GetTouchEventDisplayX()

```c
int32_t OH_Input_GetTouchEventDisplayX(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | X coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_SetTouchEventDisplayY()

```c
void OH_Input_SetTouchEventDisplayY(struct Input_TouchEvent* touchEvent, int32_t displayY)
```

**Description**

Sets the Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t displayY | Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_GetTouchEventDisplayY()

```c
int32_t OH_Input_GetTouchEventDisplayY(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Y coordinate of the touch event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

### OH_Input_SetTouchEventActionTime()

```c
void OH_Input_SetTouchEventActionTime(struct Input_TouchEvent* touchEvent, int64_t actionTime)
```

**Description**

Sets the time when the touch event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int64_t actionTime | Timestamp of the touch event, which is measured as the number of microseconds that have elapsed since the Unix epoch.|

### OH_Input_GetTouchEventActionTime()

```c
int64_t OH_Input_GetTouchEventActionTime(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the time when the touch event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int64_t | Time when a touch event occurs.|

### OH_Input_SetTouchEventWindowId()

```c
void OH_Input_SetTouchEventWindowId(struct Input_TouchEvent* touchEvent, int32_t windowId)
```

**Description**

Sets the window ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t windowId | Window ID of a touch event.|

### OH_Input_GetTouchEventWindowId()

```c
int32_t OH_Input_GetTouchEventWindowId(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the window ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Window ID of a touch event.|

### OH_Input_SetTouchEventDisplayId()

```c
void OH_Input_SetTouchEventDisplayId(struct Input_TouchEvent* touchEvent, int32_t displayId)
```

**Description**

Sets the screen ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|
| int32_t displayId | Screen ID of a touch event.|

### OH_Input_GetTouchEventDisplayId()

```c
int32_t OH_Input_GetTouchEventDisplayId(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the screen ID of a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Screen ID of a touch event.|

### OH_Input_CancelInjection()

```c
void OH_Input_CancelInjection()
```

**Description**

Stops event injection and revokes authorization.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

### OH_Input_RequestInjection()

```c
Input_Result OH_Input_RequestInjection(Input_InjectAuthorizeCallback callback)
```

**Description**

Requests the permission for [OH_Input_InjectKeyEvent](capi-oh-input-manager-h.md#oh_input_injectkeyevent), [OH_Input_InjectTouchEvent](capi-oh-input-manager-h.md#oh_input_injecttouchevent), and [OH_Input_InjectMouseEvent](capi-oh-input-manager-h.md#oh_input_injectmouseevent).

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Device behavior differences**: This API takes effect only on PCs/2-in-1 devices. If this API is called on other devices, error code 801 is returned.

**Since**: 20


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_InjectAuthorizeCallback](capi-oh-input-manager-h.md#input_injectauthorizecallback) callback | Callback used to return the permission authorization status. For details, see [Input_InjectAuthorizeCallback](capi-oh-input-manager-h.md#input_injectauthorizecallback).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](capi-oh-input-manager-h.md#input_result) | Result code. For details, see [Input_Result](capi-oh-input-manager-h.md#input_result).<br>      INPUT_SUCCESS = 0: Operation success. The application waits for the user authorization result and returns the authorization status through a callback.<br>      INPUT_PARAMETER_ERROR = 401: Parameter error. The callback parameter is empty.<br>      INPUT_DEVICE_NOT_SUPPORTED = 801: Function not supported.<br>      INPUT_SERVICE_EXCEPTION = 3800001: Service error.<br>      INPUT_INJECTION_AUTHORIZING = 3900005: Permission being granted.<br>      INPUT_INJECTION_OPERATION_FREQUENT = 3900006: Repeated request. The application continuously requests permission authorization at an interval of no more than 3 seconds.<br>      INPUT_INJECTION_AUTHORIZED = 3900007: Permission granted.<br>      INPUT_INJECTION_AUTHORIZED_OTHERS = 3900008: Permission granted to other applications.|

### OH_Input_QueryAuthorizedStatus()

```c
Input_Result OH_Input_QueryAuthorizedStatus(Input_InjectionStatus* status)
```

**Description**

Queries the injection permission authorization status of the current application.

**Since**: 20


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_InjectionStatus](capi-oh-input-manager-h.md#input_injectionstatus)* status | Injection permission authorization status of the current application. See [Input_InjectionStatus](capi-oh-input-manager-h.md#input_injectionstatus).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](capi-oh-input-manager-h.md#input_result) | Result code. For details, see [Input_Result](capi-oh-input-manager-h.md#input_result).<br>      INPUT_SUCCESS = 0: Operation success.<br>      INPUT_PARAMETER_ERROR = 401: Parameter error. The status parameter is empty.<br>      INPUT_SERVICE_EXCEPTION = 3800001: Service error.|

### OH_Input_CreateAxisEvent()

```c
Input_AxisEvent* OH_Input_CreateAxisEvent(void)
```

**Description**

Creates an axis event object. You can call [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent) to destroy an axis event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| Input_AxisEvent* | [Input_AxisEvent](capi-input-input-axisevent.md) object if the operation is successful; **null** otherwise.|

### OH_Input_DestroyAxisEvent()

```c
Input_Result OH_Input_DestroyAxisEvent(Input_AxisEvent** axisEvent)
```

**Description**

Destroys an axis event object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)** axisEvent | Pointer to the axis event object.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_SetAxisEventAction()

```c
Input_Result OH_Input_SetAxisEventAction(Input_AxisEvent* axisEvent, InputEvent_AxisAction action)
```

**Description**

Sets the action for an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisAction](capi-oh-axis-type-h.md#inputevent_axisaction) action | Axis event action. For details, see [InputEvent_AxisAction](capi-oh-axis-type-h.md#inputevent_axisaction).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventAction()

```c
Input_Result OH_Input_GetAxisEventAction(const Input_AxisEvent* axisEvent, InputEvent_AxisAction *action)
```

**Description**

Obtains the action of an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisAction](capi-oh-axis-type-h.md#inputevent_axisaction) *action | Axis event action. For details, see [InputEvent_AxisAction](capi-oh-axis-type-h.md#inputevent_axisaction).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **action** is null.|

### OH_Input_SetAxisEventDisplayX()

```c
Input_Result OH_Input_SetAxisEventDisplayX(Input_AxisEvent* axisEvent, float displayX)
```

**Description**

Sets the X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| float displayX | X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventDisplayX()

```c
Input_Result OH_Input_GetAxisEventDisplayX(const Input_AxisEvent* axisEvent, float* displayX)
```

**Description**

Obtains the X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| float* displayX | X coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **displayX** is null.|

### OH_Input_SetAxisEventDisplayY()

```c
Input_Result OH_Input_SetAxisEventDisplayY(Input_AxisEvent* axisEvent, float displayY)
```

**Description**

Sets the Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| float displayY | Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventDisplayY()

```c
Input_Result OH_Input_GetAxisEventDisplayY(const Input_AxisEvent* axisEvent, float* displayY)
```

**Description**

Obtains the Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| float* displayY | Y coordinate of the axis event in the relative coordinate system with the upper-left corner of the specified screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **displayY** is null.|

### OH_Input_SetAxisEventAxisValue()

```c
Input_Result OH_Input_SetAxisEventAxisValue(Input_AxisEvent* axisEvent,InputEvent_AxisType axisType, double axisValue)
```

**Description**

Sets the axis value of the axis type specified by the axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype) axisType | Axis type. For details, see [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype).|
| double axisValue | Axis event value. A positive number means scrolling forward (for example, 1.0 equals one unit forward), and a negative number means scrolling backward (for example, -1.0 equals one unit backward).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventAxisValue()

```c
Input_Result OH_Input_GetAxisEventAxisValue(const Input_AxisEvent* axisEvent,InputEvent_AxisType axisType, double* axisValue)
```

**Description**

Obtains the axis value for the specified axis type of the axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype) axisType | Axis type. For details, see [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype).|
| double* axisValue | Axis event value. A positive number means scrolling forward (for example, 1.0 equals one unit forward), and a negative number means scrolling backward (for example, -1.0 equals one unit backward).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **axisValue** is null.|

### OH_Input_SetAxisEventActionTime()

```c
Input_Result OH_Input_SetAxisEventActionTime(Input_AxisEvent* axisEvent, int64_t actionTime)
```

**Description**

Sets the time when an axis event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int64_t actionTime | Axis event timestamp, which is measured as the number of milliseconds that have elapsed since the Unix epoch.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventActionTime()

```c
Input_Result OH_Input_GetAxisEventActionTime(const Input_AxisEvent* axisEvent, int64_t* actionTime)
```

**Description**

Obtains the time when an axis event occurs.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int64_t* actionTime | Axis event timestamp, which is measured as the number of milliseconds that have elapsed since the Unix epoch.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **actionTime** is null.|

### OH_Input_SetAxisEventType()

```c
Input_Result OH_Input_SetAxisEventType(Input_AxisEvent* axisEvent, InputEvent_AxisEventType axisEventType)
```

**Description**

Sets the axis event type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype) axisEventType | Axis event type. For details, see [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventType()

```c
Input_Result OH_Input_GetAxisEventType(const Input_AxisEvent* axisEvent, InputEvent_AxisEventType* axisEventType)
```

**Description**

Obtains the axis event type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype)* axisEventType | Axis event type. For details, see [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **axisEventType** is null.|

### OH_Input_SetAxisEventSourceType()

```c
Input_Result OH_Input_SetAxisEventSourceType(Input_AxisEvent* axisEvent, InputEvent_SourceType sourceType)
```

**Description**

Sets the axis event source type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_SourceType](#inputevent_sourcetype) sourceType | Axis event source type. For details, see [InputEvent_SourceType](#inputevent_sourcetype).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventSourceType()

```c
Input_Result OH_Input_GetAxisEventSourceType(const Input_AxisEvent* axisEvent, InputEvent_SourceType* sourceType)
```

**Description**

Obtains the axis event source type.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| [InputEvent_SourceType](#inputevent_sourcetype)* sourceType | Axis event source type. For details, see [InputEvent_SourceType](#inputevent_sourcetype).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **sourceType** is null.|

### OH_Input_SetAxisEventWindowId()

```c
Input_Result OH_Input_SetAxisEventWindowId(Input_AxisEvent* axisEvent, int32_t windowId)
```

**Description**

Sets the window ID of an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t windowId | Window ID of an axis event.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventWindowId()

```c
Input_Result OH_Input_GetAxisEventWindowId(const Input_AxisEvent* axisEvent, int32_t* windowId)
```

**Description**

Obtains the window ID of an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t* windowId | Window ID of the axis event.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **windowId** is null.|

### OH_Input_SetAxisEventDisplayId()

```c
Input_Result OH_Input_SetAxisEventDisplayId(Input_AxisEvent* axisEvent, int32_t displayId)
```

**Description**

Sets the screen ID of an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t displayId | Screen ID of an axis event.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is null.|

### OH_Input_GetAxisEventDisplayId()

```c
Input_Result OH_Input_GetAxisEventDisplayId(const Input_AxisEvent* axisEvent, int32_t* displayId)
```

**Description**

Obtains the screen ID of an axis event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t* displayId | Screen ID of the axis event.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **displayId** is null.|

### OH_Input_AddKeyEventMonitor()

```c
Input_Result OH_Input_AddKeyEventMonitor(Input_KeyEventCallback callback)
```

**Description**

Adds a listener for key events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEventCallback](#input_keyeventcallback) callback | Callback used to receive key events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddMouseEventMonitor()

```c
Input_Result OH_Input_AddMouseEventMonitor(Input_MouseEventCallback callback)
```

**Description**

Adds a listener for mouse events, including mouse click and movement events, but not scroll wheel events. Scroll wheel events are axis events.

This API can be called only when the screen recording scenario is in use. Otherwise, the call does not take effect.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_MouseEventCallback](#input_mouseeventcallback) callback | Callback used to receive mouse events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddTouchEventMonitor()

```c
Input_Result OH_Input_AddTouchEventMonitor(Input_TouchEventCallback callback)
```

**Description**

Adds a listener for touch input events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_TouchEventCallback](#input_toucheventcallback) callback | Callback used to receive touch events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddAxisEventMonitorForAll()

```c
Input_Result OH_Input_AddAxisEventMonitorForAll(Input_AxisEventCallback callback)
```

**Description**

Adds a listener for all types of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEventCallback](#input_axiseventcallback) callback | Callback used to receive axis events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddAxisEventMonitor()

```c
Input_Result OH_Input_AddAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback)
```

**Description**

Adds a listener for the specified type of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype) axisEventType | Axis event type, which is defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|
| [Input_AxisEventCallback](#input_axiseventcallback) callback | Callback used to receive the specified type of axis events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveKeyEventMonitor()

```c
Input_Result OH_Input_RemoveKeyEventMonitor(Input_KeyEventCallback callback)
```

**Description**

Removes the listener for key events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEventCallback](#input_keyeventcallback) callback | Callback for key events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveMouseEventMonitor()

```c
Input_Result OH_Input_RemoveMouseEventMonitor(Input_MouseEventCallback callback)
```

**Description**

Removes the listener for mouse events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_MouseEventCallback](#input_mouseeventcallback) callback | Callback for mouse events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveTouchEventMonitor()

```c
Input_Result OH_Input_RemoveTouchEventMonitor(Input_TouchEventCallback callback)
```

**Description**

Removes the listener for touch events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_TouchEventCallback](#input_toucheventcallback) callback | Callback for touch events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveAxisEventMonitorForAll()

```c
Input_Result OH_Input_RemoveAxisEventMonitorForAll(Input_AxisEventCallback callback)
```

**Description**

Removes the listener for all types of axis events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_AxisEventCallback](#input_axiseventcallback) callback | Callback for the all types of axis events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveAxisEventMonitor()

```c
Input_Result OH_Input_RemoveAxisEventMonitor(InputEvent_AxisEventType axisEventType, Input_AxisEventCallback callback)
```

**Description**

Removes the listener for the specified type of axis events, which are defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permissions**: ohos.permission.INPUT_MONITORING

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype) axisEventType | Axis event type, which is defined in [InputEvent_AxisEventType](capi-oh-axis-type-h.md#inputevent_axiseventtype).|
| [Input_AxisEventCallback](#input_axiseventcallback) callback | Callback for the specified type of axis events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddKeyEventInterceptor()

```c
Input_Result OH_Input_AddKeyEventInterceptor(Input_KeyEventCallback callback, Input_InterceptorOptions *option)
```

**Description**

Adds an interceptor for key events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application gains focus.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permission**: ohos.permission.INTERCEPT_INPUT_EVENT

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEventCallback](#input_keyeventcallback) callback | Callback used to receive key events.|
| [Input_InterceptorOptions](capi-input-input-interceptoroptions.md) *option | Options for event interception. If **null** is passed, the default value is used.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_REPEAT_INTERCEPTOR](#input_result) if an interceptor is repeatedly added;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_AddInputEventInterceptor()

```c
Input_Result OH_Input_AddInputEventInterceptor(Input_InterceptorEventCallback *callback,Input_InterceptorOptions *option)
```

**Description**

Adds an interceptor for input events, including mouse, touch, and axis events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application window is hit.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permission**: ohos.permission.INTERCEPT_INPUT_EVENT

<!--RP2--><!--RP2End-->

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_InterceptorEventCallback](capi-input-input-interceptoreventcallback.md) *callback | Pointer to the structure of the interceptor event callback. For details, see [Input_InterceptorEventCallback](capi-input-input-interceptoreventcallback.md).|
| [Input_InterceptorOptions](capi-input-input-interceptoroptions.md) *option | Options for event interception. If **null** is passed, the default value is used.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the callback is empty or no listener is added; [INPUT_REPEAT_INTERCEPTOR](#input_result) if an interceptor is repeatedly added;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveKeyEventInterceptor()

```c
Input_Result OH_Input_RemoveKeyEventInterceptor(void)
```

**Description**

Removes the interceptor for key events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permission**: ohos.permission.INTERCEPT_INPUT_EVENT

<!--RP2--><!--RP2End-->

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_RemoveInputEventInterceptor()

```c
Input_Result OH_Input_RemoveInputEventInterceptor(void)
```

**Description**

Removes the interceptor for input events, including mouse, touch, and axis events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Required permission**: ohos.permission.INTERCEPT_INPUT_EVENT

<!--RP2--><!--RP2End-->

**Since**: 12

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PERMISSION_DENIED](#input_result) if permission verification fails;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_GetIntervalSinceLastInput()

```c
Input_Result OH_Input_GetIntervalSinceLastInput(int64_t *timeInterval)
```

**Description**

Obtains the interval since the last system input event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| int64_t *timeInterval | Time interval, in μs.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Status code of the **OH_Input_GetIntervalSinceLastInput** function,<br>[INPUT_SUCCESS](#input_result) if the interval is obtained successfully; [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal; [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect.|

### OH_Input_CreateHotkey()

```c
Input_Hotkey *OH_Input_CreateHotkey(void)
```

**Description**

Creates a hotkey object. You can call [OH_Input_DestroyHotkey](#oh_input_destroyhotkey) to destroy a hotkey object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14

**Return value**

| Type| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) | [Input_Hotkey](capi-input-input-hotkey.md) pointer if the operation is successful; a null pointer otherwise (possibly because of a memory allocation failure).|

### OH_Input_DestroyHotkey()

```c
void OH_Input_DestroyHotkey(Input_Hotkey **hotkey)
```

**Description**

Destroys a hotkey object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) **hotkey | Hotkey object.|

### OH_Input_SetPreKeys()

```c
void OH_Input_SetPreKeys(Input_Hotkey *hotkey, int32_t *preKeys, int32_t size)
```

**Description**

Sets the modifier keys.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) *hotkey | Hotkey object.|
| int32_t *preKeys | List of modifier keys.|
| int32_t size | Number of modifier keys. One or two modifier keys are supported.|

### OH_Input_GetPreKeys()

```c
Input_Result OH_Input_GetPreKeys(const Input_Hotkey *hotkey, int32_t **preKeys, int32_t *preKeyCount)
```

**Description**

Obtains the modifier key.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_Hotkey](capi-input-input-hotkey.md) *hotkey | Hotkey object.|
| int32_t **preKeys | List of modifier keys.|
| int32_t *preKeyCount | Number of modifier keys.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Error code of the **OH_Input_GetPreKeys** function.<br>         [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) otherwise.|

### OH_Input_SetFinalKey()

```c
void OH_Input_SetFinalKey(Input_Hotkey* hotkey, int32_t finalKey)
```

**Description**

Sets the modified key.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| int32_t finalKey | Modifier key value. Only one modifier key value is allowed.|

### OH_Input_GetFinalKey()

```c
Input_Result OH_Input_GetFinalKey(const Input_Hotkey* hotkey, int32_t *finalKeyCode)
```

**Description**

Obtains the modified key.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| int32_t *finalKeyCode | Modified key.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Error code of the **OH_Input_GetFinalKey** function.<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) otherwise.|

### OH_Input_CreateAllSystemHotkeys()

```c
Input_Hotkey **OH_Input_CreateAllSystemHotkeys(int32_t count)
```

**Description**

Creates an [Input_Hotkey](capi-input-input-hotkey.md) array. You can call [OH_Input_DestroyAllSystemHotkeys](#oh_input_destroyallsystemhotkeys) to destroy the array of the [Input_Hotkey](capi-input-input-hotkey.md) instance and reclaim the memory.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t count | Number of [Input_Hotkey](capi-input-input-hotkey.md) instances.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) | Error codes of the **OH_Input_CreateAllSystemHotkeys** function.<br>         which is [INPUT_SUCCESS](#input_result) if the operation is successful.|

### OH_Input_DestroyAllSystemHotkeys()

```c
void OH_Input_DestroyAllSystemHotkeys(Input_Hotkey **hotkeys, int32_t count)
```

**Description**

Destroys an [Input_Hotkey](capi-input-input-hotkey.md) array and reclaims the memory.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) **hotkeys | Double pointer to the [Input_Hotkey](capi-input-input-hotkey.md) array.|
| int32_t count | Number of [Input_Hotkey](capi-input-input-hotkey.md) instances.|

### OH_Input_GetAllSystemHotkeys()

```c
Input_Result OH_Input_GetAllSystemHotkeys(Input_Hotkey **hotkey, int32_t *count)
```

**Description**

Obtains all configured hotkeys.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md) **hotkey | [Input_Hotkey](capi-input-input-hotkey.md) array. When calling this API for the first time, you can pass **NULL** to obtain the array length.|
| int32_t *count | Number of supported hotkeys.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Status code of the **OH_Input_GetAllSystemHotkeys** function, which is<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) otherwise.|

### OH_Input_SetRepeat()

```c
void OH_Input_SetRepeat(Input_Hotkey* hotkey, bool isRepeat)
```

**Description**

Specifies whether to report repeated key events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| bool isRepeat | Whether to report repeated key events. The value **true** means to report repeated key events, and the value **false** means the opposite.|

### OH_Input_GetRepeat()

```c
Input_Result OH_Input_GetRepeat(const Input_Hotkey* hotkey, bool *isRepeat)
```

**Description**

Checks whether to report repeated key events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| bool *isRepeat | Whether the reported key event is repeated. The value **true** indicates that the key event is repeated, and the value **false** indicates that the key event is not repeated.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Error code of the **OH_Input_GetRepeat** function.<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) otherwise.|

### OH_Input_AddHotkeyMonitor()

```c
Input_Result OH_Input_AddHotkeyMonitor(const Input_Hotkey* hotkey, Input_HotkeyCallback callback)
```

**Description**

Subscribes to hotkey events. This API is not applicable to wearables and lite wearables.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| [Input_HotkeyCallback](#input_hotkeycallback) callback | Defines the callback used to return hotkey events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | OH_Input_AddHotkeyMonitor status code, specifically,<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if parameter verification fails;<br>         [INPUT_OCCUPIED_BY_SYSTEM](#input_result) if the hotkey has been occupied by the system (you can use [OH_Input_GetAllSystemHotkeys](#oh_input_getallsystemhotkeys) to query allsystem hotkeys);<br>         [INPUT_OCCUPIED_BY_OTHER](#input_result) if the hotkey has been occupied by another application;<br>         [INPUT_DEVICE_NOT_SUPPORTED](#input_result) if the function is not supported.|

### OH_Input_RemoveHotkeyMonitor()

```c
Input_Result OH_Input_RemoveHotkeyMonitor(const Input_Hotkey* hotkey, Input_HotkeyCallback callback)
```

**Description**

Unsubscribes from hotkey events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 14


**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_Hotkey](capi-input-input-hotkey.md)* hotkey | Hotkey object.|
| [Input_HotkeyCallback](#input_hotkeycallback) callback | Defines the callback used to return hotkey events.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | OH_Input_RemoveHotkeyMonitor status code, specifically,<br>         [INPUT_SUCCESS](#input_result) if the operation is successful; [INPUT_PARAMETER_ERROR](#input_result) if parameter verification fails.|

### OH_Input_RegisterDeviceListener()

```c
Input_Result OH_Input_RegisterDeviceListener(Input_DeviceListener* listener)
```

**Description**

Registers a listener for device hot swap events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceListener](capi-input-input-devicelistener.md)* listener | Pointer to the [Input_DeviceListener](capi-input-input-devicelistener.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | **OH_Input_RegisterDeviceListener** status code, specifically:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the listener is null.|

### OH_Input_UnregisterDeviceListener()

```c
Input_Result OH_Input_UnregisterDeviceListener(Input_DeviceListener* listener)
```

**Description**

Unregisters the listener for device hot swap events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceListener](capi-input-input-devicelistener.md)* listener | Pointer to the [Input_DeviceListener](capi-input-input-devicelistener.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | **OH_Input_UnregisterDeviceListener** status code, specifically:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **listener** is null or the listener is not registered;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_UnregisterDeviceListeners()

```c
Input_Result OH_Input_UnregisterDeviceListeners()
```

**Description**

Unregisters the listener for all device hot swap events.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | **OH_Input_UnregisterDeviceListener** status code, specifically:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_GetDeviceIds()

```c
Input_Result OH_Input_GetDeviceIds(int32_t *deviceIds, int32_t inSize, int32_t *outSize)
```

**Description**

Obtains the IDs of all input devices.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t *deviceIds | List of input device IDs.|
| int32_t inSize | Size of the input device ID list.|
| int32_t *outSize | Length of the input device ID list. The value must be less than or equal to the value of **inSize**.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceIds** or **outSize** is a null pointer or **inSize** is less than **0**.|

### OH_Input_GetDevice()

```c
Input_Result OH_Input_GetDevice(int32_t deviceId, Input_DeviceInfo **deviceInfo)
```

**Description**

Obtains information about the input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) **deviceInfo | Pointer to the [Input_DeviceInfo](capi-input-input-deviceinfo.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** is a null pointer or **deviceId** is invalid.<br> You can use [OH_Input_GetDeviceIds](#oh_input_getdeviceids) to query the device IDs supported by the system.|

### OH_Input_CreateDeviceInfo()

```c
Input_DeviceInfo* OH_Input_CreateDeviceInfo(void)
```

**Description**

Creates a **deviceInfo** object. You can call [OH_Input_DestroyDeviceInfo](#oh_input_destroydeviceinfo) to destroy an input device information object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13

**Return value**

| Type| Description|
| -- | -- |
| Input_DeviceInfo* | Pointer to the [Input_DeviceInfo](capi-input-input-deviceinfo.md) object if the operation is successful; a null pointer otherwise (possibly because of a memory allocation failure).|

### OH_Input_DestroyDeviceInfo()

```c
void OH_Input_DestroyDeviceInfo(Input_DeviceInfo **deviceInfo)
```

**Description**

Destroys a **deviceInfo** object.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) **deviceInfo | **deviceInfo** object.|

### OH_Input_GetKeyboardType()

```c
Input_Result OH_Input_GetKeyboardType(int32_t deviceId, int32_t *keyboardType)
```

**Description**

Obtains the keyboard type of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|
| int32_t *keyboardType | Pointer to the keyboard type of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the device ID is invalid or **keyboardType** is a null pointer.|

### OH_Input_GetDeviceId()

```c
Input_Result OH_Input_GetDeviceId(Input_DeviceInfo *deviceInfo, int32_t *id)
```

**Description**

Obtains the ID of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| int32_t *id | Pointer to the input device ID.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **ID** is a null pointer.|

### OH_Input_GetDeviceName()

```c
Input_Result OH_Input_GetDeviceName(Input_DeviceInfo *deviceInfo, char **name)
```

**Description**

Obtains the name of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| char **name | Pointer to the input device name.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **name** is a null pointer.|

### OH_Input_GetCapabilities()

```c
Input_Result OH_Input_GetCapabilities(Input_DeviceInfo *deviceInfo, int32_t *capabilities)
```

**Description**

Obtains the capabilities of an input device, for example, a touchscreen, touchpad, or keyboard.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| int32_t *capabilities | Pointer to the capability information of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **capabilities** is a null pointer.|

### OH_Input_GetDeviceVersion()

```c
Input_Result OH_Input_GetDeviceVersion(Input_DeviceInfo *deviceInfo, int32_t *version)
```

**Description**

Obtains the version information of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| int32_t *version | Pointer to the version information of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **version** is a null pointer.|

### OH_Input_GetDeviceProduct()

```c
Input_Result OH_Input_GetDeviceProduct(Input_DeviceInfo *deviceInfo, int32_t *product)
```

**Description**

Obtains the product information of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| int32_t *product | Pointer to the product information of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **product** is a null pointer.|

### OH_Input_GetDeviceVendor()

```c
Input_Result OH_Input_GetDeviceVendor(Input_DeviceInfo *deviceInfo, int32_t *vendor)
```

**Description**

Obtains the vendor information of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| int32_t *vendor | Pointer to the vendor information of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **vendor** is a null pointer.|

### OH_Input_GetDeviceAddress()

```c
Input_Result OH_Input_GetDeviceAddress(Input_DeviceInfo *deviceInfo, char **address)
```

**Description**

Obtains the physical address of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_DeviceInfo](capi-input-input-deviceinfo.md) *deviceInfo | Input device information. For details, see [Input_DeviceInfo](capi-input-input-deviceinfo.md).|
| char **address | Pointer to the physical address of the input device.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **deviceInfo** or **address** is a null pointer.|

### OH_Input_GetFunctionKeyState()

```c
Input_Result OH_Input_GetFunctionKeyState(int32_t keyCode, int32_t *state)
```

**Description**

Obtains the function key status.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t keyCode | Function key. Currently, only the **CapsLock** key is supported. The key value is **1**.|
| int32_t *state | Function key status. The value **0** indicates that the function key is disabled, and the value **1** indicates that the function key is enabled.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | **OH_Input_GetFunctionKeyState** status code, specifically:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>  [INPUT_KEYBOARD_DEVICE_NOT_EXIST](#input_result) if the keyboard device does not exist.|

### OH_Input_InjectTouchEvent()

```c
int32_t OH_Input_InjectTouchEvent(const struct Input_TouchEvent* touchEvent)
```

**Description**

Injects a touch event by using coordinates in the relative coordinate system with the upper-left corner of the specified screen as the origin.

This API does not take effect if the event injection permission is not granted.

Since API version 20, you are advised to use [OH_Input_RequestInjection](#oh_input_requestinjection) to request the required permission before calling this API. If the status returned by [OH_Input_QueryAuthorizedStatus](#oh_input_queryauthorizedstatus) is [AUTHORIZED](capi-oh-input-manager-h.md#input_injectionstatus), then you can call this API.

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | **OH_Input_InjectTouchEvent** status code, specifically:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>         [INPUT_PERMISSION_DENIED](#input_result) if the permission is denied.|

### OH_Input_InjectMouseEvent()

```c
int32_t OH_Input_InjectMouseEvent(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Injects a mouse event by using coordinates in the relative coordinate system with the upper-left corner of the specified screen as the origin.

This API does not take effect if the event injection permission is not granted.

Since API version 20, you are advised to use [OH_Input_RequestInjection](#oh_input_requestinjection) to request the required permission before calling this API. If the status returned by [OH_Input_QueryAuthorizedStatus](#oh_input_queryauthorizedstatus) is [AUTHORIZED](capi-oh-input-manager-h.md#input_injectionstatus), then you can call this API.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent |  Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | **OH_Input_InjectTouchEvent** status code, specifically:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>         [INPUT_PERMISSION_DENIED](#input_result) if the permission is denied.|

### OH_Input_GetMouseEventDisplayId()

```c
int32_t OH_Input_GetMouseEventDisplayId(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the screen ID of a mouse event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Screen ID if the operation is successful; **-1** if **mouseEvent** is null.|

### OH_Input_QueryMaxTouchPoints()

```c
Input_Result OH_Input_QueryMaxTouchPoints(int32_t *count)
```

**Description**

Queries the maximum number of touch points supported by the device.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t *count | Maximum number of touch points supported by the device. The value range is [0, 10]. The value **-1** indicates that the number of touch points is unknown.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](capi-oh-input-manager-h.md#input_result) | Operation result:<br>[INPUT_SUCCESS](#input_result) if the operation is successful;<br> [INPUT_PARAMETER_ERROR](capi-oh-input-manager-h.md#input_result) if the parameter verification fails.|

### OH_Input_InjectMouseEventGlobal()
```c
int32_t OH_Input_InjectMouseEventGlobal(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Injects a mouse event by using coordinates in the global coordinate system with the upper-left corner of the primary screen as the origin.

This API does not take effect if the event injection permission is not granted.

You are advised to use [OH_Input_RequestInjection](#oh_input_requestinjection) to request the required permission before calling this API. If the status returned by [OH_Input_QueryAuthorizedStatus](#oh_input_queryauthorizedstatus) is [AUTHORIZED](capi-oh-input-manager-h.md#input_injectionstatus), then you can call this API.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Operation result:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>         [INPUT_PERMISSION_DENIED](#input_result) if the permission is denied.|

### OH_Input_SetMouseEventGlobalX()
```c
void OH_Input_SetMouseEventGlobalX(struct Input_MouseEvent* mouseEvent, int32_t globalX)
```

**Description**

Sets the X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t globalX | X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_GetMouseEventGlobalX()

```c
int32_t OH_Input_GetMouseEventGlobalX(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | X coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_SetMouseEventGlobalY()

```c
void OH_Input_SetMouseEventGlobalY(struct Input_MouseEvent* mouseEvent, int32_t globalY)
```

**Description**

Sets the Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).|
| int32_t globalY | Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_GetMouseEventGlobalY()

```c
int32_t OH_Input_GetMouseEventGlobalY(const struct Input_MouseEvent* mouseEvent)
```

**Description**

Obtains the Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can call [OH_Input_CreateMouseEvent](#oh_input_createmouseevent) to create a mouse event object.<br>If the mouse event object is no longer needed, destroy it by calling [OH_Input_DestroyMouseEvent](#oh_input_destroymouseevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Y coordinate of the mouse event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_InjectTouchEventGlobal()

```c
int32_t OH_Input_InjectTouchEventGlobal(const struct Input_TouchEvent* touchEvent)
```

**Description**

Injects a touch event by using coordinates in the global coordinate system with the upper-left corner of the primary screen as the origin.

This API does not take effect if the event injection permission is not granted.

You are advised to use [OH_Input_RequestInjection](#oh_input_requestinjection) to request the required permission before calling this API. If the status returned by [OH_Input_QueryAuthorizedStatus](#oh_input_queryauthorizedstatus) is [AUTHORIZED](capi-oh-input-manager-h.md#input_injectionstatus), then you can call this API.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Operation result:<br>         [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>         [INPUT_PERMISSION_DENIED](#input_result) if the permission is denied.|

### OH_Input_SetTouchEventGlobalX()

```c
void OH_Input_SetTouchEventGlobalX(struct Input_TouchEvent* touchEvent, int32_t globalX)
```

**Description**

Sets the X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 
| int32_t globalX | X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_GetTouchEventGlobalX()

```c
int32_t OH_Input_GetTouchEventGlobalX(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | X coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_SetTouchEventGlobalY()

```c
void OH_Input_SetTouchEventGlobalY(struct Input_TouchEvent* touchEvent, int32_t globalY)
```

**Description**

Sets the Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 
| int32_t globalY | Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_GetTouchEventGlobalY()

```c
int32_t OH_Input_GetTouchEventGlobalY(const struct Input_TouchEvent* touchEvent)
```

**Description**

Obtains the Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const struct [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **TouchEvent** object, which can be created through [OH_Input_CreateTouchEvent](#oh_input_createtouchevent).<br>If the **TouchEvent** object is no longer needed, destroy it by calling [OH_Input_DestroyTouchEvent](#oh_input_destroytouchevent).| 

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Y coordinate of the touch event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

### OH_Input_SetAxisEventGlobalX()

```c
Input_Result OH_Input_SetAxisEventGlobalX(struct Input_AxisEvent* axisEvent, int32_t globalX)
```

**Description**

Sets the X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t globalX | X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is a null pointer.|

### OH_Input_GetAxisEventGlobalX()

```c
Input_Result OH_Input_GetAxisEventGlobalX(const Input_AxisEvent* axisEvent, int32_t* globalX)
```

**Description**

Obtains the X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t* globalX | X coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **globalX** is a null pointer.|

### OH_Input_SetAxisEventGlobalY()

```c
Input_Result OH_Input_SetAxisEventGlobalY(struct Input_AxisEvent* axisEvent, int32_t globalY)
```

**Description**

Sets the Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t globalY | Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** is a null pointer.|

### OH_Input_GetAxisEventGlobalY()

```c
Input_Result OH_Input_GetAxisEventGlobalY(const Input_AxisEvent* axisEvent, int32_t* globalY)
```

**Description**

Obtains the Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object. You can call [OH_Input_CreateAxisEvent](#oh_input_createaxisevent) to create an axis event object.<br>If the axis event object is no longer needed, destroy it by calling [OH_Input_DestroyAxisEvent](#oh_input_destroyaxisevent).|
| int32_t* globalY | Y coordinate of the axis event in the global coordinate system with the upper-left corner of the primary screen as the origin.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | [INPUT_SUCCESS](#input_result) if the operation is successful;<br>         [INPUT_PARAMETER_ERROR](#input_result) if **axisEvent** or **globalY** is a null pointer.|

### OH_Input_GetPointerLocation()

```c
Input_Result OH_Input_GetPointerLocation(int32_t *displayId, double *displayX, double *displayY)
```

**Description**

Obtains the coordinates of the mouse pointer on the current screen.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t *displayId | Screen ID of the current screen.|
| double *displayX | X coordinate of the mouse pointer on the screen.|
| double *displayY | Y coordinate of the mouse pointer on the screen.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>      [INPUT_SUCCESS](#input_result) if the operation is successful;<br>      [INPUT_PARAMETER_ERROR](#input_result) if the parameter is incorrect;<br>      [INPUT_SERVICE_EXCEPTION](#input_result) if a service exception occurs;<br>      [INPUT_APP_NOT_FOCUSED](#input_result) if the current application is not in focus;<br>      [INPUT_DEVICE_NO_POINTER](#input_result) if no mouse device is available.|


### OH_Input_GetKeyEventId()

```c
Input_Result OH_Input_GetKeyEventId(const struct Input_KeyEvent* keyEvent, int32_t* eventId)
```

**Description**

Obtains the ID of a key event.

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | **KeyEvent** object, which can be created through [OH_Input_CreateKeyEvent](#oh_input_createkeyevent).<br>If the key event object is no longer needed, destroy it by calling [OH_Input_DestroyKeyEvent](#oh_input_destroykeyevent).|
| int32_t* eventId | ID of the key event.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br> [INPUT_SUCCESS](#input_result) if the operation is successful;<br> [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|


### OH_Input_AddKeyEventHook()

```c
Input_Result OH_Input_AddKeyEventHook(Input_KeyEventCallback callback)
```

**Description**

Adds a hook function for key event interception.

You can call [OH_Input_RemoveKeyEventHook](#oh_input_removekeyeventhook) to remove a hook function that has been added. Multiple hook functions can be set for an application, but only one hook function can be set for a process. The most recently added hook function has a higher priority.

<!--RP1--><!--RP1End-->

**Required permissions**: ohos.permission.HOOK_KEY_EVENT

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEventCallback](#input_keyeventcallback) callback | Hook function, which is used to intercept all key events to be distributed.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br> [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br>  [INPUT_DEVICE_NOT_SUPPORTED](#input_result) if the function is not supported.<br>  [INPUT_PERMISSION_DENIED](#input_result) if the permission verification fails;<br>  [INPUT_REPEAT_INTERCEPTOR](#input_result) if the hook function is set repeatedly (only one hook function can be set for a process);<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_RemoveKeyEventHook()

```c
Input_Result OH_Input_RemoveKeyEventHook(Input_KeyEventCallback callback)
```

**Description**

Removes the hook function for key event interception.

This API is usually used together with [OH_Input_AddKeyEventHook](#oh_input_addkeyeventhook).

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEventCallback](#input_keyeventcallback) callback | Hook function, which is used to intercept all key events to be distributed.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful; (if a hook is not added, a success message is also returned when the hook is removed);<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_DispatchToNextHandler()

```c
Input_Result OH_Input_DispatchToNextHandler(int32_t eventId)
```

**Description**

Redispatches key events.

Only key events intercepted by the hook function can be redispatched, and these events must maintain the original priority sequence.<br>
After this API is called, key events will be redispatched within 3 seconds. If the redispatch is not completed within 3 seconds, [INPUT_PARAMETER_ERROR](#input_result) is reported.<br>
Successful redispatch requires correct mapping of events. If one or more [KEY_ACTION_DOWN](#input_keyeventaction) events are redispatched, the [KEY_ACTION_UP](#input_keyeventaction) or [KEY_ACTION_CANCEL](#input_keyeventaction) event can be redispatched.<br>
If only the [KEY_ACTION_UP](#input_keyeventaction) or [KEY_ACTION_CANCEL](#input_keyeventaction) key events are redispatched, the API call is successful, but the dispatch is not actually performed.<br>
If the redispatched event is not intercepted by the hook function, the API call is successful, but the dispatch is not actually performed.

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t eventId | ID of the key event. which can be obtained through [OH_Input_GetKeyEventId](#oh_input_getkeyeventid).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails; (you can call [OH_Input_GetKeyEventId](#oh_input_getkeyeventid) to check whether the input eventId is correct);<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_SetPointerVisible()

```c
Input_Result OH_Input_SetPointerVisible(bool visible)
```

**Description**

Sets the visible status of the mouse pointer in the current window.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| bool visible | Whether the mouse pointer is visible. The value **true** indicates that the mouse pointer is visible, and the value **false** indicates the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_DEVICE_NOT_SUPPORTED](#input_result) if the device is not supported;<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_GetPointerStyle()

```c
Input_Result OH_Input_GetPointerStyle(int32_t windowId, int32_t *pointerStyle)
```

**Description**

Obtains the mouse pointer style of the specified window.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The value is an integer greater than or equal to **-1**. The value **-1** indicates the global window.<br> Only the ID of the current window or global window can be specified. If any other ID is specified, the default pointer style of the global window is returned. You can obtain the ID of the current window through [getWindowProperties](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9).|
| int32_t* pointerStyle | Mouse pointer style.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_SetPointerStyle()

```c
Input_Result OH_Input_SetPointerStyle(int32_t windowId, int32_t pointerStyle)
```

**Description**

Sets the mouse pointer style of the specified window.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The value is an integer greater than or equal to 0.<br> Only the ID of the current window can be specified. If any other ID is specified, the API call is successful, but the setting does not take effect. You can obtain the ID of the current window through [getWindowProperties](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9).|
| int32_t pointerStyle | Mouse pointer style. The value is an enumerated value of [Input_PointerStyle](capi-oh-pointer-style-h.md#input_pointerstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|


### OH_Input_CustomCursor_Create()

```c
Input_CustomCursor* OH_Input_CustomCursor_Create(OH_PixelmapNative* pixelMap, int32_t anchorX, int32_t anchorY)
```

**Description**

Creates a custom mouse pointer object. You can call [OH_Input_CustomCursor_Destroy](#oh_input_customcursor_destroy) to destroy a custom mouse pointer resource object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| OH_PixelmapNative* pixelMap | Pixel map of the custom mouse pointer object. For details, see [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md). The minimum value is the minimum size of the resource image. The maximum value is 256 x 256 px.|
| int32_t anchorX | Horizontal coordinate of the mouse pointer's focus. The coordinates are subject to the size of the custom mouse pointer. The minimum value is **0** and the maximum value is the maximum width of the resource image, in px.|
| int32_t anchorY | Vertical coordinate of the mouse pointer's focus. The coordinates are subject to the size of the custom mouse pointer. The minimum value is **0** and the maximum value is the maximum height of the resource image, in px.|

**Return value**
| Type| Description|
| -- | -- |
| Input_CustomCursor* | [Input_CustomCursor](./capi-input-input-customcursor.md) object. The pointer to the custom mouse pointer object is returned if the operation is successful, and a null pointer is returned if an exception occurs.|


### OH_Input_CustomCursor_Destroy()

```c
void OH_Input_CustomCursor_Destroy(Input_CustomCursor** customCursor)
```

**Description**

Destroys a custom mouse pointer object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| Input_CustomCursor** customCursor | Custom mouse pointer object. For details, see [Input_CustomCursor](./capi-input-input-customcursor.md).|


### OH_Input_CustomCursor_GetPixelMap()

```c
Input_Result OH_Input_CustomCursor_GetPixelMap(Input_CustomCursor* customCursor, OH_PixelmapNative** pixelMap)
```

**Description**

Obtains the pixel map of a custom mouse pointer object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| Input_CustomCursor* customCursor | Custom mouse pointer object. For details, see [Input_CustomCursor](./capi-input-input-customcursor.md).|
| OH_PixelmapNative** pixelMap | Pixel map of the custom mouse pointer object. For details, see [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|


### OH_Input_CustomCursor_GetAnchor()

```c
Input_Result OH_Input_CustomCursor_GetAnchor(Input_CustomCursor* customCursor, int32_t* anchorX, int32_t* anchorY)
```

**Description**

Obtains the focus coordinates of a custom mouse pointer object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| Input_CustomCursor* customCursor | Custom mouse pointer object. For details, see [Input_CustomCursor](./capi-input-input-customcursor.md).|
| int32_t* anchorX | Horizontal coordinate of the custom mouse pointer object's focus, in px.|
| int32_t* anchorY | Vertical coordinate of the custom mouse pointer object's focus, in px.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|


### OH_Input_CursorConfig_Create()

```c
Input_CursorConfig* OH_Input_CursorConfig_Create(bool followSystem)
```

**Description**

Creates a custom mouse pointer configuration object. You can call [OH_Input_CursorConfig_Destroy](#oh_input_cursorconfig_destroy) to destroy a custom mouse pointer configuration object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| bool followSystem | Whether to adjust the pointer size based on the system setting. The value **true** means to adjust the pointer size based on the system setting, and the value **false** means to use the size of the custom mouse pointer. The adjustable range is [size of the pointer image, 256 x 256].|

**Return value**

| Type| Description|
| -- | -- |
| Input_CursorConfig* | Custom mouse pointer configuration object. For details, see [Input_CursorConfig](./capi-input-input-cursorconfig.md).|


### OH_Input_CursorConfig_Destroy()

```c
void OH_Input_CursorConfig_Destroy(Input_CursorConfig** cursorConfig)
```

**Description**

Destroys a custom mouse pointer configuration object.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| Input_CursorConfig** cursorConfig | Custom mouse pointer configuration object. For details, see [Input_CursorConfig](./capi-input-input-cursorconfig.md).|


### OH_Input_CursorConfig_IsFollowSystem()

```c
Input_Result OH_Input_CursorConfig_IsFollowSystem(Input_CursorConfig *cursorConfig, bool *followSystem)
```

**Description**

Queries whether the custom mouse pointer configuration follows the system setting to adjust the pointer size.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| Input_CursorConfig* cursorConfig | Custom mouse pointer configuration object. For details, see [Input_CursorConfig](./capi-input-input-cursorconfig.md).|
| bool* followSystem | Whether to adjust the pointer size based on the system setting. The value **true** means to adjust the pointer size based on the system setting, and the value **false** means to use the size of custom mouse pointer.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|


### OH_Input_SetCustomCursor()

```c
Input_Result OH_Input_SetCustomCursor(int32_t windowId, Input_CustomCursor* customCursor, Input_CursorConfig* cursorConfig)
```

**Description**

Sets the custom mouse pointer style.

The cursor may be switched back to the system style in the following cases: application window layout change, hot zone switching, page redirection, moving of the cursor out of the window and then back to the window, or moving of the cursor in different areas of the window. In this case, you need to reset the cursor style.

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The value must be an integer greater than or equal to **0**. Only the pointer style of the current window can be specified.|
| Input_CustomCursor* customCursor | Custom mouse pointer object. For details, see [Input_CustomCursor](./capi-input-input-customcursor.md).|
| Input_CursorConfig* cursorConfig | Custom mouse pointer configuration object. For details, see [Input_CursorConfig](./capi-input-input-cursorconfig.md).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br> [INPUT_INVALID_WINDOWID](#input_result) if the window ID is invalid;<br>   [INPUT_DEVICE_NOT_SUPPORTED](#input_result) if the device is not supported;<br> [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|

### OH_Input_CursorInfo_Create()

```c
struct Input_CursorInfo* OH_Input_CursorInfo_Create()
```

**Description**

Creates a mouse pointer information object. You can call [OH_Input_CursorInfo_Destroy](#oh_input_cursorinfo_destroy) to destroy a mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Return value**

| Type| Description|
| -- | -- |
| struct Input_CursorInfo* | An [Input_CursorInfo](capi-input-input-cursorinfo.md) object if the operation is successful; a null pointer otherwise (possibly because of a memory allocation failure).|

### OH_Input_CursorInfo_Destroy()

```c
void OH_Input_CursorInfo_Destroy(Input_CursorInfo** cursorInfo)
```

**Description**

Destroys the mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)** cursorInfo | Mouse pointer information object.|

### OH_Input_CursorInfo_IsVisible()

```c
Input_Result OH_Input_CursorInfo_IsVisible(Input_CursorInfo* cursorInfo, bool* visible)
```

**Description**

Obtains the pointer visible status of the specified mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_GetMouseEventCursorInfo](#oh_input_getmouseeventcursorinfo) to query the mouse pointer information of a specified mouse event, or call [OH_Input_GetCursorInfo](#oh_input_getcursorinfo) to query the current mouse pointer information.|
| bool* visible | Visible status of the mouse pointer. The value **true** indicates that the mouse pointer is visible, and the value **false** indicates the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|

### OH_Input_CursorInfo_GetStyle()

```c
Input_Result OH_Input_CursorInfo_GetStyle(Input_CursorInfo* cursorInfo, Input_PointerStyle* style)
```

**Description**

Obtains the pointer style of the specified mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_GetMouseEventCursorInfo](#oh_input_getmouseeventcursorinfo) to query the mouse pointer information of a specified mouse event, or call [OH_Input_GetCursorInfo](#oh_input_getcursorinfo) to query the current mouse pointer information.|
| [Input_PointerStyle](capi-oh-pointer-style-h.md) | Pointer style. For details, see [Input_PointerStyle](./capi-oh-pointer-style-h.md#input_pointerstyle).|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails or the pointer is invisible.|

### OH_Input_CursorInfo_GetSizeLevel()

```c
Input_Result OH_Input_CursorInfo_GetSizeLevel(Input_CursorInfo* cursorInfo, int32_t* sizeLevel)
```

**Description**

Obtains the pointer size level of the specified mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_GetMouseEventCursorInfo](#oh_input_getmouseeventcursorinfo) to query the mouse pointer information of a specified mouse event, or call [OH_Input_GetCursorInfo](#oh_input_getcursorinfo) to query the current mouse pointer information.|
| int32_t* sizeLevel | Pointer size level of the mouse pointer information object. The value is an integer ranging from 1 to 7. A larger value indicates a higher pointer size level. The size of the custom pointer [DEVELOPER_DEFINED_ICON](./capi-oh-pointer-style-h.md#input_pointerstyle) is subject to the actual bitmap size.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails or the pointer is invisible.|

### OH_Input_CursorInfo_GetColor()

```c
Input_Result OH_Input_CursorInfo_GetColor(Input_CursorInfo* cursorInfo, uint32_t* color)
```

**Description**

Obtains the pointer color of the specified mouse pointer information object.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_GetMouseEventCursorInfo](#oh_input_getmouseeventcursorinfo) to query the mouse pointer information of a specified mouse event, or call [OH_Input_GetCursorInfo](#oh_input_getcursorinfo) to query the current mouse pointer information.|
| uint32_t* color | Pointer color of the mouse pointer information object, which is represented by a 32-bit ARGB integer. The size of the custom pointer [DEVELOPER_DEFINED_ICON](./capi-oh-pointer-style-h.md#input_pointerstyle) is subject to the actual bitmap color.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails or the pointer is invisible.|

### OH_Input_GetMouseEventCursorInfo()

```c
Input_Result OH_Input_GetMouseEventCursorInfo(const struct Input_MouseEvent* mouseEvent, Input_CursorInfo* cursorInfo)
```

**Description**

Obtains the mouse pointer information of the mouse event, including the pointer visible status, pointer style, pointer size level, and pointer color.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| const [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object. You can obtain the mouse event object from the callback of [OH_Input_AddMouseEventMonitor](#oh_input_addmouseeventmonitor) or [OH_Input_AddInputEventInterceptor](#oh_input_addinputeventinterceptor).|
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_CursorInfo_Create](#oh_input_cursorinfo_create) to create a mouse pointer information object.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails.|

### OH_Input_GetCursorInfo()

```c
Input_Result OH_Input_GetCursorInfo(Input_CursorInfo* cursorInfo, OH_PixelmapNative** pixelmap)
```

**Description**

Obtains the mouse pointer information, including the pointer visible status, pointer style, pointer size level, and pointer color. If the **pixelmap** parameter is not empty and the pointer style is [DEVELOPER_DEFINED_ICON](./capi-oh-pointer-style-h.md#input_pointerstyle), the **PixelMap** object of the pointer is returned.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_CursorInfo](capi-input-input-cursorinfo.md)* cursorInfo | Mouse pointer information object. You can call [OH_Input_CursorInfo_Create](#oh_input_cursorinfo_create) to create a mouse pointer information object.|
| [OH_PixelmapNative](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md)** pixelmap | **PixelMap** object. If this parameter is not empty and the pointer is a custom one, the **PixelMap** object of the pointer is returned. Otherwise, the **PixelMap** object is not returned. Firstly, create an **OH_PixelmapInitializationOptions** object through [OH_PixelmapInitializationOptions_Create](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapinitializationoptions_create). Then, set the width to a value greater than **0** through [OH_PixelmapInitializationOptions_SetWidth](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapinitializationoptions_setwidth), set the height to a value greater than **0** through [OH_PixelmapInitializationOptions_SetHeight](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapinitializationoptions_setheight). Finally, create a **PixelMap** object by calling [OH_PixelmapNative_CreateEmptyPixelmap](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_createemptypixelmap) with the **OH_PixelmapInitializationOptions** object passed in.<br>When the **PixelMap** object is no longer needed, you need to call [OH_PixelmapNative_Release](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release) to release the object and then call [OH_PixelmapNative_Destroy](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_destroy) to destroy it.|

**Return value**

| Type| Description|
| -- | -- |
| [Input_Result](#input_result) | Operation result:<br>  [INPUT_SUCCESS](#input_result) if the operation is successful;<br>  [INPUT_PARAMETER_ERROR](#input_result) if the parameter verification fails;<br>  [INPUT_SERVICE_EXCEPTION](#input_result) if the service is abnormal.|
