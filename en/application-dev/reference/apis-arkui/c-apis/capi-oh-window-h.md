# oh_window.h

## Overview

The file declares the window management APIs. You can use the APIs to set and obtain the properties of a window, and set its status bar style and navigation bar style.

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [int32_t OH_WindowManager_SetWindowStatusBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)](#oh_windowmanager_setwindowstatusbarenabled) | - | Sets whether to display the status bar in a window. |
| [int32_t OH_WindowManager_SetWindowStatusBarColor(int32_t windowId, int32_t color)](#oh_windowmanager_setwindowstatusbarcolor) | - | Sets the color of the status bar in a window. |
| [int32_t OH_WindowManager_SetWindowNavigationBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)](#oh_windowmanager_setwindownavigationbarenabled) | - | Sets whether to display the navigation bar in a window. |
| [int32_t OH_WindowManager_GetWindowAvoidArea(int32_t windowId, WindowManager_AvoidAreaType type, WindowManager_AvoidArea* avoidArea)](#oh_windowmanager_getwindowavoidarea) | - | Obtains the avoid area of a window. |
| [int32_t OH_WindowManager_IsWindowShown(int32_t windowId, bool* isShow)](#oh_windowmanager_iswindowshown) | - | Checks whether a window is displayed. |
| [int32_t OH_WindowManager_ShowWindow(int32_t windowId)](#oh_windowmanager_showwindow) | - | Shows a window. |
| [int32_t OH_WindowManager_SetWindowTouchable(int32_t windowId, bool isTouchable)](#oh_windowmanager_setwindowtouchable) | - | Sets whether a window is touchable. |
| [int32_t OH_WindowManager_SetWindowFocusable(int32_t windowId, bool isFocusable)](#oh_windowmanager_setwindowfocusable) | - | Sets whether a window is focusable. |
| [int32_t OH_WindowManager_SetWindowBackgroundColor(int32_t windowId, const char* color)](#oh_windowmanager_setwindowbackgroundcolor) | - | Sets the background color of a window. |
| [int32_t OH_WindowManager_SetWindowBrightness(int32_t windowId, float brightness)](#oh_windowmanager_setwindowbrightness) | - | Sets the window brightness for the main window. The window brightness takes effect only when the window is in the foreground and has focus. |
| [int32_t OH_WindowManager_SetWindowKeepScreenOn(int32_t windowId, bool isKeepScreenOn)](#oh_windowmanager_setwindowkeepscreenon) | - | Sets whether to always keep the screen on for a window. |
| [int32_t OH_WindowManager_SetWindowPrivacyMode(int32_t windowId, bool isPrivacy)](#oh_windowmanager_setwindowprivacymode) | - | Sets whether to enable privacy mode for a window. |
| [int32_t OH_WindowManager_GetWindowProperties(int32_t windowId, WindowManager_WindowProperties* windowProperties)](#oh_windowmanager_getwindowproperties) | - | Obtains the properties of a window. |
| [int32_t OH_WindowManager_Snapshot(int32_t windowId, OH_PixelmapNative* pixelMap)](#oh_windowmanager_snapshot) | - | Obtains the snapshot of a window. |
| [int32_t OH_WindowManager_GetAllWindowLayoutInfoList(int64_t displayId, WindowManager_Rect** windowLayoutInfoList, size_t* windowLayoutInfoSize)](#oh_windowmanager_getallwindowlayoutinfolist) | - | Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array. |
| [void OH_WindowManager_ReleaseAllWindowLayoutInfoList(WindowManager_Rect* windowLayoutInfoList)](#oh_windowmanager_releaseallwindowlayoutinfolist) | - | Releases the memory occupied by a window layout information array. |
| [int32_t OH_WindowManager_InjectTouchEvent(int32_t windowId, Input_TouchEvent* touchEvent, int32_t windowX, int32_t windowY)](#oh_windowmanager_injecttouchevent) | - | Injects a multimodal touch event into the target window. This function is limited to injecting events into windows that belong to the same process. The injection does not affect window focus or stacking order, nor does it start window dragging. The event is forwarded directly to ArkUI. This function must be called after the target window has completed its UI loading. |
| [int32_t OH_WindowManager_GetAllMainWindowInfo(WindowManager_MainWindowInfo** infoList, size_t* mainWindowInfoSize)](#oh_windowmanager_getallmainwindowinfo) | - | Obtains the information about all main windows. |
| [void OH_WindowManager_ReleaseAllMainWindowInfo(WindowManager_MainWindowInfo* infoList)](#oh_windowmanager_releaseallmainwindowinfo) | - | Releases the memory used by the main window information list. |
| [typedef void (\*OH_WindowManager_WindowSnapshotCallback)(const OH_PixelmapNative** snapshotPixelMapList, size_t snapshotListSize)](#oh_windowmanager_windowsnapshotcallback) | OH_WindowManager_WindowSnapshotCallback | Defines the callback used for receiving the main window screenshot list. |
| [int32_t OH_WindowManager_GetMainWindowSnapshot(int32_t* windowIdList, size_t windowIdListSize, WindowManager_WindowSnapshotConfig config, OH_WindowManager_WindowSnapshotCallback callback)](#oh_windowmanager_getmainwindowsnapshot) | - | Obtains the screenshots of one or more main windows specified by **windowId**. |
| [void OH_WindowManager_ReleaseMainWindowSnapshot(const OH_PixelmapNative* snapshotPixelMapList)](#oh_windowmanager_releasemainwindowsnapshot) | - | Releases the memory used by the main window screenshot list. |
| [int32_t OH_WindowManager_LockCursor(int32_t windowId, bool isCursorFollowMovement)](#oh_windowmanager_lockcursor) | - | Locks the mouse cursor within the specified window area and controls whether the cursor follows mouse movements. It is only supported by the window that currently has focus, and the lock is automatically released when the window loses focus. |
| [int32_t OH_WindowManager_UnlockCursor(int32_t windowId)](#oh_windowmanager_unlockcursor) | - | Clears the mouse cursor mode previously set for the window. |
| [int32_t OH_WindowManager_FrameMetrics_IsFirstDrawFrame(const OH_WindowManager_FrameMetrics* metrics, bool* isFirstDrawFrame)](#oh_windowmanager_framemetrics_isfirstdrawframe) | - | Check whether the current frame is the first frame. |
| [int32_t OH_WindowManager_FrameMetrics_GetInputHandlingDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)](#oh_windowmanager_framemetrics_getinputhandlingduration) | - | Get the time taken to process external input events in one frame. |
| [int32_t OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)](#oh_windowmanager_framemetrics_getlayoutmeasureduration) | - | Get the time taken for layout measurement in one frame. |
| [int32_t OH_WindowManager_FrameMetrics_GetVsyncTimestamp(const OH_WindowManager_FrameMetrics* metrics, uint64_t* timestamp)](#oh_windowmanager_framemetrics_getvsynctimestamp) | - | Get the start timestamp of the current frame. |
| [int32_t OH_WindowManager_RegisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)](#oh_windowmanager_registerframemetricsmeasuredcallback) | - | Registers a callback for window frame metric change events. This API depends on the loading of the window page content. That is, this API can be called only after the **<br>loadContent()** or **setUIContent()** API in ArkTS takes effect. The callback is triggered only when the client UI content is redrawn (for example, page switching, interaction with responsive components, or background color and opacity setting). To cancel the registration, call the [OH_WindowManager_UnregisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_unregisterframemetricsmeasuredcallback) API. |
| [int32_t OH_WindowManager_UnregisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)](#oh_windowmanager_unregisterframemetricsmeasuredcallback) | - | Unregisters the callback for window frame metric change events. This API depends on the loading of the window page content. That is, this API can be called only after the **<br>loadContent()** or **setUIContent()** API in ArkTS takes effect. To register such a callback, call the [OH_WindowManager_RegisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_registerframemetricsmeasuredcallback) API. |
| [int32_t OH_WindowManager_DensityInfo_GetDefaultDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getdefaultdensity) | - | Gets the system default display size scaling factor of the screen where the window is located. |
| [int32_t OH_WindowManager_DensityInfo_GetSystemDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getsystemdensity) | - | Gets the system display size scaling factor of the screen where the window is located. |
| [int32_t OH_WindowManager_DensityInfo_GetCustomDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getcustomdensity) | - | Gets the custom display size scaling factor of the window. |
| [int32_t OH_WindowManager_GetDensityInfoCopy(int32_t windowId, const OH_WindowManager_DensityInfo** info)](#oh_windowmanager_getdensityinfocopy) | - | Get the system display size scaling factor, the system default display size scaling factor, and the custom display size scaling factor information of the screen where the current window is located. |
| [int32_t OH_WindowManager_RegisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)](#oh_windowmanager_registerdensityinfochangecallback) | - | Listen for changes in the display size scaling factor information of the window. The callback function is triggered when any of the system display size scaling factor, system default display size scaling factor, or custom display size scaling factor of the screen where the window resides changes. To unlisten for changes in the display size scaling factor information of the window, call OH_WindowManager_UnregisterDensityInfoChangeCallback. |
| [int32_t OH_WindowManager_UnregisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)](#oh_windowmanager_unregisterdensityinfochangecallback) | - | Unlisten for changes in the display size scaling factor information of the window. The callback function is triggered when any of the system display size scaling factor, system default display size scaling factor, or custom display size scaling factor of the screen where the window resides changes. To listen for changes in the display size scaling factor information of the window, call OH_WindowManager_RegisterDensityInfoChangeCallback. |
| [int32_t OH_WindowManager_DensityInfo_Release(const OH_WindowManager_DensityInfo* info)](#oh_windowmanager_densityinfo_release) | - | Releases the memory occupied by DensityInfo. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_WindowManager_WindowSnapshotCallback)(const OH_PixelmapNative** snapshotPixelMapList, size_t snapshotListSize) | Defines the callback used for receiving the main window screenshot list.<br>**Since**: 21 |

## Function description

### OH_WindowManager_SetWindowStatusBarEnabled()

```c
int32_t OH_WindowManager_SetWindowStatusBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)
```

**Description**

Sets whether to display the status bar in a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool enabled | Whether to display the status bar. **true** to display, **false** otherwise. |
| bool enableAnimation | Whether to enable the show/hide animation of the status bar. **true** to enable, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowStatusBarColor()

```c
int32_t OH_WindowManager_SetWindowStatusBarColor(int32_t windowId, int32_t color)
```

**Description**

Sets the color of the status bar in a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| int32_t color | Color to set, in ARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowNavigationBarEnabled()

```c
int32_t OH_WindowManager_SetWindowNavigationBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)
```

**Description**

Sets whether to display the navigation bar in a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool enabled | Whether to display the navigation bar. **true** to display, **false** otherwise. |
| bool enableAnimation | Whether to enable the show/hide animation of the navigation bar. **true** to enable, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_GetWindowAvoidArea()

```c
int32_t OH_WindowManager_GetWindowAvoidArea(int32_t windowId, WindowManager_AvoidAreaType type, WindowManager_AvoidArea* avoidArea)
```

**Description**

Obtains the avoid area of a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| WindowManager_AvoidAreaType type | Type of the avoid area. |
| WindowManager_AvoidArea* avoidArea | Pointer to the avoid area. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful, return avoid area ptr in avoidArea.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_IsWindowShown()

```c
int32_t OH_WindowManager_IsWindowShown(int32_t windowId, bool* isShow)
```

**Description**

Checks whether a window is displayed.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool* isShow | Pointer to the check result for whether the window is displayed. **true** if displayed, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. |

### OH_WindowManager_ShowWindow()

```c
int32_t OH_WindowManager_ShowWindow(int32_t windowId)
```

**Description**

Shows a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowTouchable()

```c
int32_t OH_WindowManager_SetWindowTouchable(int32_t windowId, bool isTouchable)
```

**Description**

Sets whether a window is touchable.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool isTouchable | Whether the window is touchable. **true** if touchable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowFocusable()

```c
int32_t OH_WindowManager_SetWindowFocusable(int32_t windowId, bool isFocusable)
```

**Description**

Sets whether a window is focusable.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool isFocusable | Whether the window is focusable. **true** if focusable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowBackgroundColor()

```c
int32_t OH_WindowManager_SetWindowBackgroundColor(int32_t windowId, const char* color)
```

**Description**

Sets the background color of a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| const char* color | Pointer to the background color. The value is a string in hexadecimal RGB or ARGB color format. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. |

### OH_WindowManager_SetWindowBrightness()

```c
int32_t OH_WindowManager_SetWindowBrightness(int32_t windowId, float brightness)
```

**Description**

Sets the window brightness for the main window. The window brightness takes effect only when the window is in the foreground and has focus.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| float brightness | Screen brightness. The value is a floating-point number in the range [0.0, 1.0] or is set to **-1. 0**. The value **1.0** means the brightest, and **-1.0** means that the window brightness resets to the original brightness set through Control Panel. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowKeepScreenOn()

```c
int32_t OH_WindowManager_SetWindowKeepScreenOn(int32_t windowId, bool isKeepScreenOn)
```

**Description**

Sets whether to always keep the screen on for a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool isKeepScreenOn | Whether to always keep the screen on. **true** to always keep the screen on, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_SetWindowPrivacyMode()

```c
int32_t OH_WindowManager_SetWindowPrivacyMode(int32_t windowId, bool isPrivacy)
```

**Description**

Sets whether to enable privacy mode for a window.

**Required permission**: ohos.permission.PRIVACY_WINDOW

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| bool isPrivacy | Whether to enable privacy mode. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally.<br>    {@link WINDOW_MANAGER_ERRORCODE_NO_PERMISSION} permission verification failed. |

### OH_WindowManager_GetWindowProperties()

```c
int32_t OH_WindowManager_GetWindowProperties(int32_t windowId, WindowManager_WindowProperties* windowProperties)
```

**Description**

Obtains the properties of a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| WindowManager_WindowProperties* windowProperties | Pointer to the properties. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful, return window properties ptr in windowProperties.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. |

### OH_WindowManager_Snapshot()

```c
int32_t OH_WindowManager_Snapshot(int32_t windowId, OH_PixelmapNative* pixelMap)
```

**Description**

Obtains the snapshot of a window.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. If the window ID is invalid or the window has been destroyed, you cannot obtain the window snapshot. To successfully obtain a snapshot, a valid window ID is required. You can obtain a valid window ID by calling the ArkTS API {@link getWindowProperties()} on the window object |
| OH_PixelmapNative* pixelMap | Pointer to the snapshot. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful, return pixel map ptr in pixelMap.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_GetAllWindowLayoutInfoList()

```c
int32_t OH_WindowManager_GetAllWindowLayoutInfoList(int64_t displayId, WindowManager_Rect** windowLayoutInfoList, size_t* windowLayoutInfoSize)
```

**Description**

Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t displayId | ID of the display. You can obtain a valid display ID by calling the ArkTS API {@link getWindowProperties()} on the window object |
| WindowManager_Rect** windowLayoutInfoList | Double pointer to the layout information array of all windows visible. This parameter is used as an output parameter. |
| size_t* windowLayoutInfoSize | Pointer to the length of the layout information array. This parameter is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful, return Window layout info list.<br>    {@link WINDOW_MANAGER_ERRORCODE_INVALID_PARAM} parameter error.<br>    {@link WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED} capability not supported.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_ReleaseAllWindowLayoutInfoList()

```c
void OH_WindowManager_ReleaseAllWindowLayoutInfoList(WindowManager_Rect* windowLayoutInfoList)
```

**Description**

Releases the memory occupied by a window layout information array.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| WindowManager_Rect* windowLayoutInfoList | Pointer to the layout information array of all windows visible on the display. You can obtain the array pointer by calling [OH_WindowManager_GetAllWindowLayoutInfoList](capi-oh-window-h.md#oh_windowmanager_getallwindowlayoutinfolist). |

### OH_WindowManager_InjectTouchEvent()

```c
int32_t OH_WindowManager_InjectTouchEvent(int32_t windowId, Input_TouchEvent* touchEvent, int32_t windowX, int32_t windowY)
```

**Description**

Injects a multimodal touch event into the target window. This function is limited to injecting events into windows that belong to the same process. The injection does not affect window focus or stacking order, nor does it start window dragging. The event is forwarded directly to ArkUI. This function must be called after the target window has completed its UI loading.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer. |
| Input_TouchEvent* touchEvent | Pointer to the multimodal touch event. For details, see {@link Input_TouchEvent}. The event is defined in **oh_input_manager.h**. Certain fields in this parameter have specific constraints. Specifically, **<br>action** should be an integer in the range [0, 3]; **id**, **displayX**, **displayY** should be an integer greater than or equal to 0. If these constraints are not met, the function returns **<br>WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**, indicating that the window manager service is abnormal. |
| int32_t windowX | X coordinate of the event relative to the target window. The value is an integer. |
| int32_t windowY | Y coordinate of the event relative to the target window. The value is an integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.      {@link OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_GetAllMainWindowInfo()

```c
int32_t OH_WindowManager_GetAllMainWindowInfo(WindowManager_MainWindowInfo** infoList, size_t* mainWindowInfoSize)
```

**Description**

Obtains the information about all main windows.

**Required permission**: ohos.permission.CUSTOM_SCREEN_CAPTURE

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| WindowManager_MainWindowInfo** infoList | Double pointer to the main window information list. This parameter is used as an output parameter. |
| size_t* mainWindowInfoSize | Pointer to the size of the main window information list. This parameter is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_NO_PERMISSION} permission verification failed.<br>    {@link WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED} capability not supported.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_ReleaseAllMainWindowInfo()

```c
void OH_WindowManager_ReleaseAllMainWindowInfo(WindowManager_MainWindowInfo* infoList)
```

**Description**

Releases the memory used by the main window information list.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| WindowManager_MainWindowInfo* infoList | Pointer to the main window information list. |

### OH_WindowManager_WindowSnapshotCallback()

```c
typedef void (*OH_WindowManager_WindowSnapshotCallback)(const OH_PixelmapNative** snapshotPixelMapList, size_t snapshotListSize)
```

**Description**

Defines the callback used for receiving the main window screenshot list.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_PixelmapNative\*\* snapshotPixelMapList | Double pointer to the list of window screenshots. |
| size_t snapshotListSize | Size of the window screenshot list. |

### OH_WindowManager_GetMainWindowSnapshot()

```c
int32_t OH_WindowManager_GetMainWindowSnapshot(int32_t* windowIdList, size_t windowIdListSize, WindowManager_WindowSnapshotConfig config, OH_WindowManager_WindowSnapshotCallback callback)
```

**Description**

Obtains the screenshots of one or more main windows specified by **windowId**.

**Required permission**: ohos.permission.CUSTOM_SCREEN_CAPTURE

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t* windowIdList | Pointer to the main window ID list. |
| size_t windowIdListSize | Size of the main window ID list. |
| WindowManager_WindowSnapshotConfig config | Configuration for obtaining the window screenshot. |
| [OH_WindowManager_WindowSnapshotCallback](capi-oh-window-h.md#oh_windowmanager_windowsnapshotcallback) callback | Callback used to return the lists of window screenshots, in the order of the provided window ID array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_NO_PERMISSION} permission verification failed.<br>    {@link WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED} capability not supported.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_ReleaseMainWindowSnapshot()

```c
void OH_WindowManager_ReleaseMainWindowSnapshot(const OH_PixelmapNative* snapshotPixelMapList)
```

**Description**

Releases the memory used by the main window screenshot list.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_PixelmapNative* snapshotPixelMapList | Pointer to the list of window screenshots. |

### OH_WindowManager_LockCursor()

```c
int32_t OH_WindowManager_LockCursor(int32_t windowId, bool isCursorFollowMovement)
```

**Description**

Locks the mouse cursor within the specified window area and controls whether the cursor follows mouse movements. It is only supported by the window that currently has focus, and the lock is automatically released when the window loses focus.

**Required permission**: ohos.permission.LOCK_WINDOW_CURSOR

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The value is an integer. |
| bool isCursorFollowMovement | Behavior of the mouse cursor when locked. If it is set to **true**, the cursor moves along with the mouse. If it is set to **false**, the cursor remains stationary and does not follow mouse movements. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_NO_PERMISSION} permission verification failed.<br>    {@link WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED} capability not supported.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_UnlockCursor()

```c
int32_t OH_WindowManager_UnlockCursor(int32_t windowId)
```

**Description**

Clears the mouse cursor mode previously set for the window.

**Required permission**: ohos.permission.LOCK_WINDOW_CURSOR

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. The value is an integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_NO_PERMISSION} permission verification failed.<br>    {@link WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED} capability not supported.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL} the window manager service works abnormally. |

### OH_WindowManager_FrameMetrics_IsFirstDrawFrame()

```c
int32_t OH_WindowManager_FrameMetrics_IsFirstDrawFrame(const OH_WindowManager_FrameMetrics* metrics, bool* isFirstDrawFrame)
```

**Description**

Check whether the current frame is the first frame.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_FrameMetrics* metrics | Frame metrics data object. |
| bool* isFirstDrawFrame | This parameter is the return value of the function, indicating whether the current frame is the first frame. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_FrameMetrics_GetInputHandlingDuration()

```c
int32_t OH_WindowManager_FrameMetrics_GetInputHandlingDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)
```

**Description**

Get the time taken to process external input events in one frame.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_FrameMetrics* metrics | Frame metrics data object. |
| uint64_t* duration | This parameter is the return value of the function, indicating the time taken to process external input events in one frame, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration()

```c
int32_t OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)
```

**Description**

Get the time taken for layout measurement in one frame.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_FrameMetrics* metrics | Frame metrics data object. |
| uint64_t* duration | This parameter is the return value of the function, indicating the time taken for layout measurement in one frame, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_FrameMetrics_GetVsyncTimestamp()

```c
int32_t OH_WindowManager_FrameMetrics_GetVsyncTimestamp(const OH_WindowManager_FrameMetrics* metrics, uint64_t* timestamp)
```

**Description**

Get the start timestamp of the current frame.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_FrameMetrics* metrics | Frame metrics data object. |
| uint64_t* timestamp | This parameter is the return value of the function, indicating the start timestamp of the current frame, in nanoseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_RegisterFrameMetricsMeasuredCallback()

```c
int32_t OH_WindowManager_RegisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)
```

**Description**

Registers a callback for window frame metric change events. This API depends on the loading of the window page content. That is, this API can be called only after the **<br>loadContent()** or **setUIContent()** API in ArkTS takes effect. The callback is triggered only when the client UI content is redrawn (for example, page switching, interaction with responsive components, or background color and opacity setting). To cancel the registration, call the [OH_WindowManager_UnregisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_unregisterframemetricsmeasuredcallback) API.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. |
| OH_WindowManager_FrameMetricsMeasuredCallback callback | Callback used to return the result. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. Possible cause:<br>    1. The window is not created or destroyed;<br>    2. This window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:      1. Invalid parameter range. |

### OH_WindowManager_UnregisterFrameMetricsMeasuredCallback()

```c
int32_t OH_WindowManager_UnregisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)
```

**Description**

Unregisters the callback for window frame metric change events. This API depends on the loading of the window page content. That is, this API can be called only after the **<br>loadContent()** or **setUIContent()** API in ArkTS takes effect. To register such a callback, call the [OH_WindowManager_RegisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_registerframemetricsmeasuredcallback) API.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | Window ID. |
| OH_WindowManager_FrameMetricsMeasuredCallback callback | Callback used to return the result. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.      {@link WS_OK} the function call is successful.<br>    {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. Possible cause:<br>    1. The window is not created or destroyed;<br>    2. This window state is abnormal.<br>    {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:      1. Invalid parameter range. |

### OH_WindowManager_DensityInfo_GetDefaultDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetDefaultDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Gets the system default display size scaling factor of the screen where the window is located.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_DensityInfo* info | Display size scaling factor information for the current window. |
| float* density | System default display size scaling factor |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_DensityInfo_GetSystemDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetSystemDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Gets the system display size scaling factor of the screen where the window is located.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_DensityInfo* info | Display size scaling factor information for the current window. |
| float* density | System display size scaling factor |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_DensityInfo_GetCustomDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetCustomDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Gets the custom display size scaling factor of the window.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_DensityInfo* info | Display size scaling factor information for the current window. |
| float* density | Custom display size scaling factor of the window. A return value of -1 indicates that no custom display size scaling factor has been set, or it has been reset. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_GetDensityInfoCopy()

```c
int32_t OH_WindowManager_GetDensityInfoCopy(int32_t windowId, const OH_WindowManager_DensityInfo** info)
```

**Description**

Get the system display size scaling factor, the system default display size scaling factor, and the custom display size scaling factor information of the screen where the current window is located.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | WindowId when window is created. |
| const OH_WindowManager_DensityInfo** info | Display size scaling factor information for the current window. A return value of NULL means this interface is not supported on the current device. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. Possible cause:<br>            1. The window is not created or destroyed;<br>            2. This window state is abnormal.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_RegisterDensityInfoChangeCallback()

```c
int32_t OH_WindowManager_RegisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)
```

**Description**

Listen for changes in the display size scaling factor information of the window. The callback function is triggered when any of the system display size scaling factor, system default display size scaling factor, or custom display size scaling factor of the screen where the window resides changes. To unlisten for changes in the display size scaling factor information of the window, call OH_WindowManager_UnregisterDensityInfoChangeCallback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | WindowId when window is created. |
| OH_WindowManager_DensityInfoCallback callback | Callback used to return the result of density information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. Possible cause:<br>            1. The window is not created or destroyed;<br>            2. This window state is abnormal.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_UnregisterDensityInfoChangeCallback()

```c
int32_t OH_WindowManager_UnregisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)
```

**Description**

Unlisten for changes in the display size scaling factor information of the window. The callback function is triggered when any of the system display size scaling factor, system default display size scaling factor, or custom display size scaling factor of the screen where the window resides changes. To listen for changes in the display size scaling factor information of the window, call OH_WindowManager_RegisterDensityInfoChangeCallback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t windowId | WindowId when window is created. |
| OH_WindowManager_DensityInfoCallback callback | Callback used to return the result of density information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL} this window state is abnormal. Possible cause:<br>            1. The window is not created or destroyed;<br>            2. This window state is abnormal.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |

### OH_WindowManager_DensityInfo_Release()

```c
int32_t OH_WindowManager_DensityInfo_Release(const OH_WindowManager_DensityInfo* info)
```

**Description**

Releases the memory occupied by DensityInfo.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_WindowManager_DensityInfo* info | Display size scaling factor information for the current window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the status code of the execution.          {@link WS_OK} the function call is successful.<br>        {@link WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM} Parameter error. Possible cause:              1. Invalid parameter range. |


