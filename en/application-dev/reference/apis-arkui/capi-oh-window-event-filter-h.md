# oh_window_event_filter.h

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=43433a4dbf9ba0069b5e7d96c07741ab924162cf translatedAt=2026-08-25T02:17:01.682Z pushedAt=2026-08-25T02:32:48.016Z -->

## Overview

Defines the APIs for event filtering in window management. When a multimodal input event passes through a window, the event can be intercepted through the filtering APIs to prevent it from being further distributed.

**File to include**: <window_manager/oh_window_event_filter.h>

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef bool (\*OH_NativeWindowManager_KeyEventFilter)(Input_KeyEvent* keyEvent)](#oh_nativewindowmanager_keyeventfilter) | OH_NativeWindowManager_KeyEventFilter | Defines a function for filtering multimodal key events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter keyEventFilter)](#oh_nativewindowmanager_registerkeyeventfilter) | - | Registers a function for filtering multimodal key events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterKeyEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregisterkeyeventfilter) | - | Unregisters a function for filtering multimodal key events.|
| [typedef bool (\*OH_NativeWindowManager_MouseEventFilter)(Input_MouseEvent* mouseEvent)](#oh_nativewindowmanager_mouseeventfilter) | OH_NativeWindowManager_MouseEventFilter | Defines a function for filtering multimodal mouse events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter mouseEventFilter)](#oh_nativewindowmanager_registermouseeventfilter) | - | Registers a function for filtering multimodal mouse events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterMouseEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregistermouseeventfilter) | - | Unregisters a function for filtering multimodal mouse events.|
| [typedef bool (\*OH_NativeWindowManager_TouchEventFilter)(Input_TouchEvent* touchEvent)](#oh_nativewindowmanager_toucheventfilter) | OH_NativeWindowManager_TouchEventFilter | Defines a function for filtering multimodal touch events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter touchEventFilter)](#oh_nativewindowmanager_registertoucheventfilter) | - | Registers a function for filtering multimodal touch events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterTouchEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregistertoucheventfilter) | - | Unregisters a function for filtering multimodal touch events.|
| [WindowManager_ErrorCode OH_NativeWindowManager_GetKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter* outKeyEventFilter)](#oh_nativewindowmanager_getkeyeventfilter) | - | Obtains the multimodal key event filtering function registered for the specified window. |
| [WindowManager_ErrorCode OH_NativeWindowManager_GetMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter* outMouseEventFilter)](#oh_nativewindowmanager_getmouseeventfilter) | - | Obtains the multimodal mouse event filtering function registered for the specified window. |
| [WindowManager_ErrorCode OH_NativeWindowManager_GetTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter* outTouchEventFilter)](#oh_nativewindowmanager_gettoucheventfilter) | - | Obtains the multimodal touch event filtering function registered for the specified window. |

## Function Description

### OH_NativeWindowManager_KeyEventFilter()

```c
typedef bool (*OH_NativeWindowManager_KeyEventFilter)(Input_KeyEvent* keyEvent)
```

**Description**

Defines a function for filtering multimodal key events.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_KeyEvent](../apis-input-kit/capi-input-input-keyevent.md)* keyEvent | Pointer to the multimodal key event. For details, see [Input_KeyEvent](../apis-input-kit/capi-input-input-keyevent.md). The event is defined in **oh_input_manager**.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Event filtering result. The value **true** indicates that the event is intercepted and will not be distributed to the next node. The value **false** indicates that the event is not intercepted and will be distributed to the next node.|

### OH_NativeWindowManager_RegisterKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter keyEventFilter)
```

**Description**

Registers a function for filtering multimodal key events.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is registered.|
| [OH_NativeWindowManager_KeyEventFilter](#oh_nativewindowmanager_keyeventfilter) keyEventFilter | Function to register.|

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Execution result of the function.<br> **OK**: The API is successfully called.<br> **INVAILD_WINDOW_ID**: The **windowId** parameter is invalid.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: The **keyEventFilter** parameter is invalid.<br> **SERVICE_ERROR**: The window management service is abnormal.|

### OH_NativeWindowManager_UnregisterKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterKeyEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal key events.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is unregistered.|

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Execution result of the function.<br> **OK**: The API is successfully called.<br> **INVAILD_WINDOW_ID**: The **windowId** parameter is invalid.<br> **SERVICE_ERROR**: The window management service is abnormal.|

### OH_NativeWindowManager_MouseEventFilter()

```c
typedef bool (*OH_NativeWindowManager_MouseEventFilter)(Input_MouseEvent* mouseEvent)
```

**Description**

Defines a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_MouseEvent](../apis-input-kit/capi-input-input-mouseevent.md)* mouseEvent | Pointer to the multimodal mouse event. For details, see [Input_MouseEvent](../apis-input-kit/capi-input-input-mouseevent.md). The event is defined in **oh_input_manager**.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Event filtering result. The value **true** indicates that the event is intercepted and will not be distributed to the next node. The value **false** indicates that the event is not intercepted and will be distributed to the next node.|

### OH_NativeWindowManager_RegisterMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter mouseEventFilter)
```

**Description**

Registers a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is registered.|
| [OH_NativeWindowManager_MouseEventFilter](#oh_nativewindowmanager_mouseeventfilter) mouseEventFilter | Function to register.|

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Execution result of the function.<br> **OK**: The API is successfully called.<br> **INVAILD_WINDOW_ID**: The **windowId** parameter is invalid.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: The **mouseEventFilter** parameter is invalid.<br> **SERVICE_ERROR**: The window management service is abnormal.|

### OH_NativeWindowManager_UnregisterMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterMouseEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is unregistered.|

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Execution result of the function.<br> **OK**: The API is successfully called.<br> **INVAILD_WINDOW_ID**: The **windowId** parameter is invalid.<br> **SERVICE_ERROR**: The window management service is abnormal.|

### OH_NativeWindowManager_TouchEventFilter()

```c
typedef bool (*OH_NativeWindowManager_TouchEventFilter)(Input_TouchEvent* touchEvent)
```

**Description**

Defines a function for filtering multimodal touch events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| [Input_TouchEvent](../apis-input-kit/capi-input-input-touchevent.md)* touchEvent | Pointer to the multimodal touch event. For details, see [Input_TouchEvent](../apis-input-kit/capi-input-input-touchevent.md). The event is defined in **oh_input_manager**.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Event filtering result. The value **true** indicates that the event is intercepted and will not be distributed to the next node. The value **false** indicates that the event is not intercepted and will be distributed to the next node.|

### OH_NativeWindowManager_RegisterTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter touchEventFilter)
```

**Description**

Registers a function for filtering multimodal touch events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is registered.|
| [OH_NativeWindowManager_TouchEventFilter](#oh_nativewindowmanager_toucheventfilter) touchEventFilter | Function for filtering multimodal touch events. |

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Result code.<br> Returns **OK** if the API is called successfully.<br> Returns **INVAILD_WINDOW_ID** if the **windowId** parameter is invalid.<br> Returns **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM** if the **touchEventFilter** parameter is invalid.<br> Returns **SERVICE_ERROR** if the window management service is abnormal. |

### OH_NativeWindowManager_UnregisterTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterTouchEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal touch events.

**Since**: 15

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the window for which the function is unregistered.|

**Return value**

| Type| Description|
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Execution result of the function.<br> **OK**: The API is successfully called.<br> **INVAILD_WINDOW_ID**: The **windowId** parameter is invalid.<br> **SERVICE_ERROR**: The window management service is abnormal.|

### OH_NativeWindowManager_GetKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter* outKeyEventFilter)
```

**Description**

Obtains the multimodal key event filtering function registered for the specified window.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| int32_t windowId | Window ID. |
| [OH_NativeWindowManager_KeyEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_keyeventfilter)* outKeyEventFilter | Pointer to the registered multimodal key event filtering function. If no filter is registered for the window, **\*outKeyEventFilter** returns **NULL**. |

**Returns**

| Type | Description |
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Result code.<br>Returns **OK** if the API is successfully called.<br>Returns **INVALID_WINDOW_ID** if the input parameter **windowId** is invalid.<br>Returns **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM** if the input parameter **outKeyEventFilter** is **NULL**. |

### OH_NativeWindowManager_GetMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter* outMouseEventFilter)
```

**Description**

Obtains the multimodal mouse event filtering function registered for the specified window.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| int32_t windowId | Window ID. |
| [OH_NativeWindowManager_MouseEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_mouseeventfilter)* outMouseEventFilter | Pointer to the registered multimodal mouse event filtering function. If no filter is registered for the window, **\*outMouseEventFilter** returns **NULL**. |

**Returns**

| Type | Description |
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Result code.<br>Returns **OK** if the API is successfully called.<br>Returns **INVALID_WINDOW_ID** if the input parameter **windowId** is invalid.<br>Returns **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM** if the input parameter **outMouseEventFilter** is **NULL**. |

### OH_NativeWindowManager_GetTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter* outTouchEventFilter)
```

**Description**

Obtains the multimodal touch event filtering function registered for the specified window.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| int32_t windowId | Window ID. |
| [OH_NativeWindowManager_TouchEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_toucheventfilter)* outTouchEventFilter | Pointer to the registered multimodal touch event filtering function. If no filter is registered for the window, **\*outTouchEventFilter** returns **NULL**. |

**Returns**

| Type | Description |
| -- | -- |
| [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode) | Result code.<br>Returns **OK** if the API is successfully called.<br>Returns **INVALID_WINDOW_ID** if the input parameter **windowId** is invalid.<br>Returns **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM** if the input parameter **outTouchEventFilter** is **NULL**. |