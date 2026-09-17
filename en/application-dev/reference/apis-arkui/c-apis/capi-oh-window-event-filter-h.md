# oh_window_event_filter.h

## Overview

The file declares the APIs for a window to filter multimodal key events. When a multimodal input event passes through the window, the window can interrupt the event to prevent it from being further distributed.

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef bool (\*OH_NativeWindowManager_KeyEventFilter)(Input_KeyEvent* keyEvent)](#oh_nativewindowmanager_keyeventfilter) | OH_NativeWindowManager_KeyEventFilter | Defines a function for filtering multimodal key events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter keyEventFilter)](#oh_nativewindowmanager_registerkeyeventfilter) | - | Registers a function for filtering multimodal key events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterKeyEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregisterkeyeventfilter) | - | Unregisters a function for filtering multimodal key events. |
| [typedef bool (\*OH_NativeWindowManager_MouseEventFilter)(Input_MouseEvent* mouseEvent)](#oh_nativewindowmanager_mouseeventfilter) | OH_NativeWindowManager_MouseEventFilter | Defines a function for filtering multimodal mouse events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter mouseEventFilter)](#oh_nativewindowmanager_registermouseeventfilter) | - | Registers a function for filtering multimodal mouse events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterMouseEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregistermouseeventfilter) | - | Unregisters a function for filtering multimodal mouse events. |
| [typedef bool (\*OH_NativeWindowManager_TouchEventFilter)(Input_TouchEvent* touchEvent)](#oh_nativewindowmanager_toucheventfilter) | OH_NativeWindowManager_TouchEventFilter | Defines a function for filtering multimodal touch events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_RegisterTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter touchEventFilter)](#oh_nativewindowmanager_registertoucheventfilter) | - | Registers a function for filtering multimodal touch events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_UnregisterTouchEventFilter(int32_t windowId)](#oh_nativewindowmanager_unregistertoucheventfilter) | - | Unregisters a function for filtering multimodal touch events. |
| [WindowManager_ErrorCode OH_NativeWindowManager_GetKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter* outKeyEventFilter)](#oh_nativewindowmanager_getkeyeventfilter) | - | Gets the key event filter callback for the window. |
| [WindowManager_ErrorCode OH_NativeWindowManager_GetMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter* outMouseEventFilter)](#oh_nativewindowmanager_getmouseeventfilter) | - | Gets the mouse event filter callback for the window. |
| [WindowManager_ErrorCode OH_NativeWindowManager_GetTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter* outTouchEventFilter)](#oh_nativewindowmanager_gettoucheventfilter) | - | Gets the touch event filter callback for the window. |

### Variable

| Name | Description |
| -- | -- |
| bool (*OH_NativeWindowManager_KeyEventFilter)(Input_KeyEvent* keyEvent) | Defines a function for filtering multimodal key events.<br>**Since**: 12 |
| bool (*OH_NativeWindowManager_MouseEventFilter)(Input_MouseEvent* mouseEvent) | Defines a function for filtering multimodal mouse events.<br>**Since**: 15 |
| bool (*OH_NativeWindowManager_TouchEventFilter)(Input_TouchEvent* touchEvent) | Defines a function for filtering multimodal touch events.<br>**Since**: 15 |

## Function description

### OH_NativeWindowManager_KeyEventFilter()

```c
typedef bool (*OH_NativeWindowManager_KeyEventFilter)(Input_KeyEvent* keyEvent)
```

**Description**

Defines a function for filtering multimodal key events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Input_KeyEvent\* keyEvent | multimodal key event. For details, see {@link Input_KeyEvent}. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether to filter this event. Returning true prevents the window from dispatching it further;          Returns false indicates that the event is not intercepted. |

### OH_NativeWindowManager_RegisterKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter keyEventFilter)
```

**Description**

Registers a function for filtering multimodal key events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_KeyEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_keyeventfilter) keyEventFilter | Filter function for multimodal key event. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the keyEventFilter is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_UnregisterKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterKeyEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal key events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_MouseEventFilter()

```c
typedef bool (*OH_NativeWindowManager_MouseEventFilter)(Input_MouseEvent* mouseEvent)
```

**Description**

Defines a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| Input_MouseEvent\* mouseEvent | multimodal mouse event. For details, see {@link Input_MouseEvent}. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether to filter this event. Returning true prevents the window from dispatching it further;          returning false indicates that the event is not intercepted. |

### OH_NativeWindowManager_RegisterMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter mouseEventFilter)
```

**Description**

Registers a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_MouseEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_mouseeventfilter) mouseEventFilter | Filter function for multimodal mouse event. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the mouseEventFilter is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_UnregisterMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterMouseEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal mouse events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_TouchEventFilter()

```c
typedef bool (*OH_NativeWindowManager_TouchEventFilter)(Input_TouchEvent* touchEvent)
```

**Description**

Defines a function for filtering multimodal touch events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| Input_TouchEvent\* touchEvent | multimodal touchEvent. For details, see {@link Input_TouchEvent}. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether to filter this event. Returning true prevents the window from dispatching it further;          returning false indicates that the event is not intercepted. |

### OH_NativeWindowManager_RegisterTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_RegisterTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter touchEventFilter)
```

**Description**

Registers a function for filtering multimodal touch events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_TouchEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_toucheventfilter) touchEventFilter | Filter function for multimodal touch event. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the touchEventFilter is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_UnregisterTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_UnregisterTouchEventFilter(int32_t windowId)
```

**Description**

Unregisters a function for filtering multimodal touch events.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window for which the function is unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the status code of the execution.      <ul>      <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVAILD_WINDOW_ID} if the window id is invalid.</li><br>    <li>Returns {@link SERVICE_ERROR} if the window manager service error occurs.</li>      </ul> |

### OH_NativeWindowManager_GetKeyEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetKeyEventFilter(int32_t windowId, OH_NativeWindowManager_KeyEventFilter* outKeyEventFilter)
```

**Description**

Gets the key event filter callback for the window.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_KeyEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_keyeventfilter)* outKeyEventFilter | Output parameter for the registered key event filter callback. If no filter has been registered, *outKeyEventFilter will return NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the error code defined by {@link WindowManager_ErrorCode}.<br>    <ul><br>    <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the outKeyEventFilter is NULL.</li>      </ul> |

### OH_NativeWindowManager_GetMouseEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetMouseEventFilter(int32_t windowId, OH_NativeWindowManager_MouseEventFilter* outMouseEventFilter)
```

**Description**

Gets the mouse event filter callback for the window.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_MouseEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_mouseeventfilter)* outMouseEventFilter | Output parameter for the registered mouse event filter callback. If no filter has been registered, *outMouseEventFilter will return NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the error code defined by {@link WindowManager_ErrorCode}.<br>    <ul><br>    <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the outMouseEventFilter is NULL.</li>      </ul> |

### OH_NativeWindowManager_GetTouchEventFilter()

```c
WindowManager_ErrorCode OH_NativeWindowManager_GetTouchEventFilter(int32_t windowId, OH_NativeWindowManager_TouchEventFilter* outTouchEventFilter)
```

**Description**

Gets the touch event filter callback for the window.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | ID of the window. |
| [OH_NativeWindowManager_TouchEventFilter](capi-oh-window-event-filter-h.md#oh_nativewindowmanager_toucheventfilter)* outTouchEventFilter | Output parameter for the registered touch event filter callback. If no filter has been registered, *outTouchEventFilter will return NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| WindowManager_ErrorCode | Returns the error code defined by {@link WindowManager_ErrorCode}.<br>    <ul><br>    <li>Returns {@link OK} if the operation is successful.</li><br>    <li>Returns {@link INVALID_WINDOW_ID} if the windowId is invalid.</li><br>    <li>Returns {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} if the outTouchEventFilter is NULL.</li>      </ul> |


