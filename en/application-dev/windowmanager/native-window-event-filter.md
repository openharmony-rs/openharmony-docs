# Using WindowManager to Manage Multimodal Input Events (C/C++)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @@JUGaaab-->
<!--Designer: @CheryHome-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=afcc21d0782366dc4d4f328dd966d46677a0652f translatedAt=2026-11-12T04:50:20.453Z pushedAt=2026-11-12T07:43:56.861Z nl=1 -->

## When to Use

[WindowManager](../reference/apis-arkui/capi-windowmanager.md) provides application window management capabilities. It currently supports filtering various multimodal input events ([Input_KeyEvent (key input event)](../reference/apis-input-kit/capi-input-input-keyevent.md), [Input_MouseEvent (mouse input event)](../reference/apis-input-kit/capi-input-input-mouseevent.md), and [Input_TouchEvent (touch input event)](../reference/apis-input-kit/capi-input-input-touchevent.md)). This document uses key input event filtering as an example. In addition, it supports injecting multimodal [Input_TouchEvent (touch input event)](../reference/apis-input-kit/capi-input-input-touchevent.md) into a target window. For the specific development steps, see the following sections.

## Filtering Multimodal Key Input Events

You can use the capability provided by the WindowManager module to intercept key input events so that they are not distributed to internal components of your application.

### Linking the Dynamic Library in the CMake Script

```txt
target_link_libraries(entry PUBLIC libnative_window_manager.so libohinput.so)
```

### Available APIs

| API                                                      | Description                                        |
| ------------------------------------------------------------ | -------------------------------------------- |
| [OH_NativeWindowManager_KeyEventFilter](../reference/apis-arkui/capi-oh-window-event-filter-h.md#oh_nativewindowmanager_keyeventfilter) | Defines the filter function for multimodal key events. |
| [OH_NativeWindowManager_RegisterKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter keyEventFilter)](../reference/apis-arkui/capi-oh-window-event-filter-h.md#oh_nativewindowmanager_registerkeyeventfilter) | Registers a key event filter for the specified window. |
| [OH_NativeWindowManager_UnregisterKeyEventFilter(int32_t windowId)](../reference/apis-arkui/capi-oh-window-event-filter-h.md#oh_nativewindowmanager_unregisterkeyeventfilter) | Unregisters the key event filter of the specified window. |

- After an application window is created, bind a key event filter using the window ID.
- The key event filter is triggered only when the application window receives a key event.
- If the key event filter returns **true**, the event is intercepted; if it returns **false**, the event is not intercepted.
- Only one key event filter can be registered for the same window ID. The last registered filter overwrites the previously registered one. To filter a multi-key combination, you are advised to process it in a single filter.

### Example

The following sample code describes how to register and unregister a key event filter. The following uses the Esc key and number keys as an example.

<!-- @[keyEventFilter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkEventDistribution/KeyEventFilter/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "napi/native_api.h"
#include "window_manager/oh_window_event_filter.h"
#include "multimodalinput/oh_input_manager.h"
#include "multimodalinput/oh_key_code.h"

// Set a filter.
static bool filterFunc(Input_KeyEvent *event)
{
    auto keyCode = OH_Input_GetKeyEventKeyCode(event);
    auto action = OH_Input_GetKeyEventAction(event);
    
    // Filter the press of the Escape key and number keys.
    return (keyCode >= Input_KeyCode::KEYCODE_0 && keyCode <= Input_KeyCode::KEYCODE_9
         && action == Input_KeyEventAction::KEY_ACTION_DOWN) || (keyCode == Input_KeyCode::KEYCODE_ESCAPE);
}

static napi_value registerFilter(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
    
    int32_t windowId;
    napi_get_value_int32(env, args[0], &windowId);
    
    // Register the filter function filterFunc for the window corresponding to windowId.
    auto res = OH_NativeWindowManager_RegisterKeyEventFilter(windowId, filterFunc);
    
    napi_value errCode;
    napi_create_int32(env, res, &errCode);
    return errCode;
}

static napi_value clearFilter(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int32_t windowId;
    napi_get_value_int32(env, args[0], &windowId);

    auto res = OH_NativeWindowManager_UnregisterKeyEventFilter(windowId);
    napi_value errCode;
    napi_create_int32(env, res, &errCode);
    return errCode;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        {"registerFilter", nullptr, registerFilter, nullptr, nullptr, nullptr, napi_default, nullptr},
        {"clearFilter", nullptr, clearFilter, nullptr, nullptr, nullptr, napi_default, nullptr}};
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```

## Injecting Multimodal Touch Events into the Target Window

Use the capabilities provided by the WindowManager module to inject touch input events into a specified window. Only windows in the same process are supported. This operation does not trigger window focus, z-order changes, or drag operations; the events are sent directly to ArkUI.


### Linking the Dynamic Library in the CMake Script

```txt
target_link_libraries(entry PUBLIC libnative_window_manager.so libohinput.so)
```

### Available APIs

| API                                                      | Description                      |
| ------------------------------------------------------------ | -------------------------- |
| [OH_WindowManager_InjectTouchEvent(int32_t windowId, Input_TouchEvent* touchEvent, int32_t windowX, int32_t windowY)](../reference/apis-arkui/capi-oh-window-h.md#oh_windowmanager_injecttouchevent) | Injects a touch event into the specified window. |

- Construct event parameters and inject the event to the window with the specified window ID.

- Only windows within the same process are supported. Injection does not trigger changes in window focus, z-order, or dragging. Events are directly sent to ArkUI.

- The API must be called after the specified window has completed its UI loading.

- Complete validation of the window and the multimodal touch input event to ensure that the event parameters are correct, and then send the event to ArkUI. The specific parameters are described below:

  | Name    | Description                                                        |
  | ---------- | ------------------------------------------------------------ |
  | windowId   | ID of the target window. Only windows within the same process are supported. Otherwise, error code 1300002 is returned. The window must have completed UI loading. Otherwise, error code 1300003 is returned.|
  | touchEvent | Pointer to the multimodal touch event. For details, see [Input_TouchEvent](../reference/apis-input-kit/capi-input-input-touchevent.md). The event is defined in **oh_input_manager.h**. Call [OH_Input_CreateTouchEvent](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_createtouchevent) to create a touchEvent object, and call [OH_Input_DestroyTouchEvent](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_destroytouchevent) to destroy the object after use. For specific parameter details, see the table below. |
  | windowX    | X coordinate of the event relative to the target window. The parameter must be a non-negative integer; otherwise, error code 1300003 is returned.|
  | windowY    | Y coordinate of the event relative to the target window. The parameter must be a non-negative integer; otherwise, error code 1300003 is returned.|

  The specific parameters of the touchEvent multimodal touch input event are described as follows:

  | Name    | API                                                        | Description                                                        |
  | ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | action     | [OH_Input_SetTouchEventAction](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventaction) | Event action. The default value is **0**.<br>Only the following actions are supported:<br>- **0**: cancel, indicating a cancel event.<br>- **1**: down, indicating a press-down event.<br>- **2**: move, indicating a move event.<br>- **3**: up, indicating a lift event.<br>- For other actions, error code 1300003 is returned.|
  | id         | [OH_Input_SetTouchEventFingerId](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventfingerid) | Finger ID. The default value is **0**.<br>The parameter must be a non-negative integer; otherwise, error code 1300003 is returned.|
  | displayX   | [OH_Input_SetTouchEventDisplayX](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventdisplayx) | X coordinate of the event relative to the screen. The default value is **0**.<br>The parameter must be a non-negative integer; otherwise, error code 1300003 is returned. It is recommended that the value of this parameter be the same as that of **windowX**, although inconsistency will not return an error code. Only the input parameter's range is verified. You are advised to use [getWindowProperties()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9) to obtain the **windowRect** property and calculate the corresponding **windowX** by subtracting the horizontal coordinate of the window's top-left corner in **windowRect** from **displayX**.|
  | displayY   | [OH_Input_SetTouchEventDisplayY](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventdisplayy) | Y coordinate of the event relative to the screen. The default value is **0**.<br>The parameter must be a non-negative integer; otherwise, error code 1300003 is returned. It is recommended that the value of this parameter be the same as that of **windowY**, although inconsistency will not return an error code. Only the input parameter's range is verified. You are advised to use [getWindowProperties()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9) to obtain the **windowRect** property and calculate the corresponding **windowY** by subtracting the vertical coordinate of the window's top-left corner in **windowRect** from **displayY**.|
  | actionTime | [OH_Input_SetTouchEventActionTime](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventactiontime) | Indicates the timestamp. The default value is -1. |
  | windowId   | [OH_Input_SetTouchEventWindowId](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventwindowid) | Window ID for event injection. The default value is **-1**. If the parameter is not the default value and does not match **windowId** in [OH_WindowManager_InjectTouchEvent](../reference/apis-arkui/capi-oh-window-h.md#oh_windowmanager_injecttouchevent), the input parameter is considered invalid.|
  | displayId  | [OH_Input_SetTouchEventDisplayId](../reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventdisplayid) | Display ID for event injection. The default value is **-1**. There are no restrictions, but you are advised to ensure that the display ID matches the window ID in [OH_WindowManager_InjectTouchEvent](../reference/apis-arkui/capi-oh-window-h.md#oh_windowmanager_injecttouchevent). You are advised to call [getWindowProperties()](../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9) to obtain the **displayId** property.|

### Example

The following sample code describes how to inject multimodal touch input events into a target window, using a single event injection as an example.

<!-- @[injectTouchEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkEventDistribution/InjectTouchEvent/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "napi/native_api.h"
#include "window_manager/oh_window.h"
#include "multimodalinput/oh_input_manager.h"

const int32_t ARGS_TWO = 2;
const int32_t ARGS_THREE = 3;
const int32_t ARGS_FOUR = 4;
const int32_t ARGS_FIVE = 5;
const int32_t ARGS_SIX = 6;
const int32_t ARGS_SEVEN = 7;
const int32_t ARGS_EIGHT = 8;
const int32_t ARGS_NINE = 9;
const int32_t ARGS_TEN = 10;

static napi_value injectEvent(napi_env env, napi_callback_info info)
{
    size_t argc = ARGS_TEN;
    napi_value args[ARGS_TEN] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int32_t windowId;
    napi_get_value_int32(env, args[0], &windowId);

    int32_t displayId;
    napi_get_value_int32(env, args[1], &displayId);

    int32_t windowX;
    napi_get_value_int32(env, args[ARGS_TWO], &windowX);

    int32_t windowY;
    napi_get_value_int32(env, args[ARGS_THREE], &windowY);

    int32_t action;
    napi_get_value_int32(env, args[ARGS_FOUR], &action);

    int32_t fingerId;
    napi_get_value_int32(env, args[ARGS_FIVE], &fingerId);

    int32_t displayX;
    napi_get_value_int32(env, args[ARGS_SIX], &displayX);

    int32_t displayY;
    napi_get_value_int32(env, args[ARGS_SEVEN], &displayY);

    int32_t actionTime;
    napi_get_value_int32(env, args[ARGS_EIGHT], &actionTime);

    int32_t TE_WindowId;
    napi_get_value_int32(env, args[ARGS_NINE], &TE_WindowId);
    
    // Construct a multimodal event touchEvent.
    Input_TouchEvent* touchEvent = OH_Input_CreateTouchEvent();
    OH_Input_SetTouchEventAction(touchEvent, action);
    OH_Input_SetTouchEventFingerId(touchEvent, fingerId);
    OH_Input_SetTouchEventDisplayX(touchEvent, displayX);
    OH_Input_SetTouchEventDisplayY(touchEvent, displayY);
    OH_Input_SetTouchEventActionTime(touchEvent, actionTime);
    OH_Input_SetTouchEventWindowId(touchEvent, TE_WindowId);
    OH_Input_SetTouchEventDisplayId(touchEvent, displayId);

    // Inject a multimodal touch event into the window corresponding to windowId.
    auto res = OH_WindowManager_InjectTouchEvent(windowId, touchEvent, windowX, windowY);

    // Destroy the object after using touchEvent.
    OH_Input_DestroyTouchEvent(&touchEvent);
    
    napi_value errCode;
    napi_create_int32(env, res, &errCode);
    return errCode;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        {"injectEvent", nullptr, injectEvent, nullptr, nullptr, nullptr, napi_default, nullptr}};
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
```