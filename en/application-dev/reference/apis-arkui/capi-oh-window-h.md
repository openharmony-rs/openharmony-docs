# oh_window.h
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## Overview

The file declares the window management APIs. You can use the APIs to set and obtain the properties of a window, and set its status bar style and navigation bar style.

**File to include**: <window_manager/oh_window.h>

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 15

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [int32_t OH_WindowManager_SetWindowStatusBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)](#oh_windowmanager_setwindowstatusbarenabled) | - | Sets whether the main window displays the status bar.|
| [int32_t OH_WindowManager_SetWindowStatusBarColor(int32_t windowId, int32_t color)](#oh_windowmanager_setwindowstatusbarcolor) | - | Sets the color of the status bar in the main window.|
| [int32_t OH_WindowManager_SetWindowNavigationBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)](#oh_windowmanager_setwindownavigationbarenabled) | - | Sets whether the main window displays the navigation bar.|
| [int32_t OH_WindowManager_GetWindowAvoidArea(int32_t windowId, WindowManager_AvoidAreaType type, WindowManager_AvoidArea* avoidArea)](#oh_windowmanager_getwindowavoidarea) | - | Obtains the avoid area of a window.|
| [int32_t OH_WindowManager_IsWindowShown(int32_t windowId, bool* isShow)](#oh_windowmanager_iswindowshown) | - | Checks whether a window is displayed.|
| [int32_t OH_WindowManager_ShowWindow(int32_t windowId)](#oh_windowmanager_showwindow) | - | Shows a window.|
| [int32_t OH_WindowManager_SetWindowTouchable(int32_t windowId, bool isTouchable)](#oh_windowmanager_setwindowtouchable) | - | Sets whether a window is touchable.|
| [int32_t OH_WindowManager_SetWindowFocusable(int32_t windowId, bool isFocusable)](#oh_windowmanager_setwindowfocusable) | - | Sets whether a window is focusable.|
| [int32_t OH_WindowManager_SetWindowBackgroundColor(int32_t windowId, const char* color)](#oh_windowmanager_setwindowbackgroundcolor) | - | Sets the background color of a window.|
| [int32_t OH_WindowManager_SetWindowBrightness(int32_t windowId, float brightness)](#oh_windowmanager_setwindowbrightness) | - | Sets the screen brightness of a window.|
| [int32_t OH_WindowManager_SetWindowKeepScreenOn(int32_t windowId, bool isKeepScreenOn)](#oh_windowmanager_setwindowkeepscreenon) | - | Sets whether to always keep the screen on for a window.|
| [int32_t OH_WindowManager_SetWindowPrivacyMode(int32_t windowId, bool isPrivacy)](#oh_windowmanager_setwindowprivacymode) | - | Sets whether to enable privacy mode for a window.|
| [int32_t OH_WindowManager_GetWindowProperties(int32_t windowId, WindowManager_WindowProperties* windowProperties)](#oh_windowmanager_getwindowproperties) | - | Obtains the properties of a window.|
| [int32_t OH_WindowManager_Snapshot(int32_t windowId, OH_PixelmapNative* pixelMap)](#oh_windowmanager_snapshot) | - | Obtains the snapshot of a window.|
| [int32_t OH_WindowManager_GetAllWindowLayoutInfoList(int64_t displayId,WindowManager_Rect** windowLayoutInfoList, size_t* windowLayoutInfoSize)](#oh_windowmanager_getallwindowlayoutinfolist) | - | Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array.|
| [void OH_WindowManager_ReleaseAllWindowLayoutInfoList(WindowManager_Rect* windowLayoutInfoList)](#oh_windowmanager_releaseallwindowlayoutinfolist) | - | Releases the memory occupied by a window layout information array.|
| [int32_t OH_WindowManager_InjectTouchEvent(int32_t windowId, Input_TouchEvent* touchEvent, int32_t windowX, int32_t windowY)](#oh_windowmanager_injecttouchevent) | - | Injects a multimodal touch event into the target window. This function is limited to injecting events into windows that belong to the same process. The injection does not affect window focus or stacking order, nor does it start window dragging. The event is forwarded directly to ArkUI. This function must be called after the target window has completed its UI loading.|
| [int32_t OH_WindowManager_GetAllMainWindowInfo(WindowManager_MainWindowInfo** infoList, size_t* mainWindowInfoSize)](#oh_windowmanager_getallmainwindowinfo) | - | Obtains the information about all main windows.|
| [void OH_WindowManager_ReleaseAllMainWindowInfo(WindowManager_MainWindowInfo* infoList)](#oh_windowmanager_releaseallmainwindowinfo) | - | Releases the memory used by the main window information list.|
| [typedef void (\*OH_WindowManager_WindowSnapshotCallback)(const OH_PixelmapNative** snapshotPixelMapList, size_t snapshotListSize)](#oh_windowmanager_windowsnapshotcallback) | OH_WindowManager_WindowSnapshotCallback | Defines the callback used for receiving the main window screenshot list.|
| [int32_t OH_WindowManager_GetMainWindowSnapshot(int32_t* windowIdList, size_t windowIdListSize, WindowManager_WindowSnapshotConfig config, OH_WindowManager_WindowSnapshotCallback callback)](#oh_windowmanager_getmainwindowsnapshot) | - | Obtains the screenshots of one or more main windows specified by **windowId**.|
| [void OH_WindowManager_ReleaseMainWindowSnapshot(const OH_PixelmapNative* snapshotPixelMapList)](#oh_windowmanager_releasemainwindowsnapshot) | - | Releases the memory used by the main window screenshot list.|
| [int32_t OH_WindowManager_LockCursor(int32_t windowId, bool isCursorFollowMovement)](#oh_windowmanager_lockcursor) | - | Locks the mouse cursor within the specified window area and controls whether the cursor follows mouse movements. It is only supported by the window that currently has focus, and the lock is automatically released when the window loses focus.|
| [int32_t OH_WindowManager_UnlockCursor(int32_t windowId)](#oh_windowmanager_unlockcursor) | - | Clears the mouse cursor mode previously set for the window.|
| [int32_t OH_WindowManager_FrameMetrics_IsFirstDrawFrame(const OH_WindowManager_FrameMetrics* metrics, bool* isFirstDrawFrame)](#oh_windowmanager_framemetrics_isfirstdrawframe) | - | Checks whether this frame is the first frame.|
| [int32_t OH_WindowManager_FrameMetrics_GetInputHandlingDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)](#oh_windowmanager_framemetrics_getinputhandlingduration) | - | Obtains the time consumed for gesture handling in this frame.|
| [int32_t OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)](#oh_windowmanager_framemetrics_getlayoutmeasureduration) | - | Obtains the time consumed for layout measurement in this frame.|
| [int32_t OH_WindowManager_FrameMetrics_GetVsyncTimestamp(const OH_WindowManager_FrameMetrics* metrics, uint64_t* timestamp)](#oh_windowmanager_framemetrics_getvsynctimestamp) | - | Obtains the timestamp when this frame starts.|
| [int32_t OH_WindowManager_RegisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)](#oh_windowmanager_registerframemetricsmeasuredcallback) | - | Registers a callback for window frame metric change events.<br> This API depends on the loading of the window page content. That is, this API can be called only after the **loadContent()** or **setUIContent()** API in ArkTS takes effect.<br> The callback is triggered only when the client UI content is redrawn (for example, page switching, interaction with responsive components, or background color and opacity setting).<br> To cancel the registration, call the [OH_WindowManager_UnregisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_unregisterframemetricsmeasuredcallback) API.|
| [int32_t OH_WindowManager_UnregisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)](#oh_windowmanager_unregisterframemetricsmeasuredcallback) | - | Unregisters the callback for window frame metric change events.<br> This API depends on the loading of the window page content. That is, this API can be called only after the **loadContent()** or **setUIContent()** API in ArkTS takes effect.<br> To register such a callback, call the [OH_WindowManager_RegisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_registerframemetricsmeasuredcallback) API.|
| [int32_t OH_WindowManager_DensityInfo_GetDefaultDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getdefaultdensity) | - | Obtains the scale factor of the system default display size of the screen where the window is located.|
| [int32_t OH_WindowManager_DensityInfo_GetSystemDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getsystemdensity) | - | Obtains the scale factor of the system display size of the screen where the window is located.|
| [int32_t OH_WindowManager_DensityInfo_GetCustomDensity(const OH_WindowManager_DensityInfo* info, float* density)](#oh_windowmanager_densityinfo_getcustomdensity) | - | Obtains the scale factor of the custom display size of the window.|
| [int32_t OH_WindowManager_GetDensityInfoCopy(int32_t windowId, const OH_WindowManager_DensityInfo** info)](#oh_windowmanager_getdensityinfocopy) | - | Obtains window scale factor information, including the scale factors of the system display size, system default display size, and custom display size. The priorities in descending order are as follows:<br> Scale factor of the custom display size: window-level display scale factor, which affects only a single window.<br> Scale factor of the system display size: display size scale factor set in the current system.<br> Scale factor of the system default display size: default reference scale factor of the system.<br>|
| [int32_t OH_WindowManager_RegisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)](#oh_windowmanager_registerdensityinfochangecallback) | - | Registers a callback for listening to window scale factor changes.<br> This callback will be triggered when any of the following changes: the scale factor of the system display size of the screen where the window is located, the scale factor of the system default display size, or the scale factor of the custom display size.<br> To unregister this callback, use [OH_WindowManager_UnregisterDensityInfoChangeCallback](capi-oh-window-h.md#oh_windowmanager_unregisterdensityinfochangecallback).|
| [int32_t OH_WindowManager_UnregisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)](#oh_windowmanager_unregisterdensityinfochangecallback) | - | Unregisters the callback for listening to window scale factor changes.<br> This callback will not be triggered after being unregistered even if any of the following changes: the scale factor of the system display size of the screen where the window is located, the scale factor of the system default display size, or the scale factor of the custom display size.<br>|
| [int32_t OH_WindowManager_DensityInfo_Release(const OH_WindowManager_DensityInfo* info)](#oh_windowmanager_densityinfo_release) | - | Releases the memory occupied by the window scale factor object.|

## Function Description

### OH_WindowManager_SetWindowStatusBarEnabled()

```c
int32_t OH_WindowManager_SetWindowStatusBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)
```

**Description**

Sets whether the main window displays the status bar.

The return value obtained after the call takes effect does not indicate that the visibility changes of the status bar have been fully executed. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as the floating window or split-screen of Multi-Window). It takes effect once the main window enters full-screen or maximized mode.

**Since**: 15

**Device behavior differences**:

Calls to this API do not take effect or return an error on a device that supports [freeform windows](../../windowmanager/window-terminology.md#freeform-window) and is in the freeform window state. On a device that supports freeform windows but is not in the freeform window state, or on a device that does not support freeform windows, this API can be properly called.

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the main window. Calls to this API with a non-main window ID do not take effect or return an error. If the window ID does not exist, the error code **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL** is returned when this API is called.|
| bool enabled | Whether to display the status bar. **true** to display, **false** otherwise.|
| bool enableAnimation | Whether to enable the show/hide animation of the status bar. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowStatusBarColor()

```c
int32_t OH_WindowManager_SetWindowStatusBarColor(int32_t windowId, int32_t color)
```

**Description**

Sets the color of the status bar in the main window.

The return value obtained after the call takes effect does not indicate that the color updates of the status bar have been fully executed. The setting does not take effect when the main window is in non-full-screen or non-maximized mode (such as the floating window or split-screen of Multi-Window). It takes effect once the main window enters full-screen or maximized mode.

**Since**: 15

**Device behavior differences**:

Calls to this API do not take effect or return an error on a device that supports [freeform windows](../../windowmanager/window-terminology.md#freeform-window) and is in the freeform window state. On a device that supports freeform windows but is not in the freeform window state, or on a device that does not support freeform windows, this API can be properly called.

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the main window. Calls to this API with a non-main window ID do not take effect or return an error. If the window ID does not exist, the error code **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL** is returned when this API is called.|
| int32_t color | Color to set, in ARGB format.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowNavigationBarEnabled()

```c
int32_t OH_WindowManager_SetWindowNavigationBarEnabled(int32_t windowId, bool enabled, bool enableAnimation)
```

**Description**

Sets whether the main window displays the navigation bar.<!--RP2--><!--RP2End-->

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | ID of the main window. Calls to this API with a non-main window ID do not take effect or return an error. If the window ID does not exist, the error code **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL** is returned when this API is called.|
| bool enabled | Whether to display the navigation bar. **true** to display, **false** otherwise.|
| bool enableAnimation | Whether to enable the show/hide animation of the navigation bar. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_GetWindowAvoidArea()

```c
int32_t OH_WindowManager_GetWindowAvoidArea(int32_t windowId, WindowManager_AvoidAreaType type, WindowManager_AvoidArea* avoidArea)
```

**Description**

Obtains the avoid area of a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| [WindowManager_AvoidAreaType](capi-oh-window-comm-h.md#windowmanager_avoidareatype) type | Type of the avoid area.|
| [WindowManager_AvoidArea](capi-windowmanager-avoidarea.md)* avoidArea | Pointer to the avoid area.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called, and the pointer to the avoid area is returned.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_IsWindowShown()

```c
int32_t OH_WindowManager_IsWindowShown(int32_t windowId, bool* isShow)
```

**Description**

Checks whether a window is displayed.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| bool* isShow | Pointer to the check result for whether the window is displayed. **true** if displayed, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.|

### OH_WindowManager_ShowWindow()

```c
int32_t OH_WindowManager_ShowWindow(int32_t windowId)
```

**Description**

Shows a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowTouchable()

```c
int32_t OH_WindowManager_SetWindowTouchable(int32_t windowId, bool isTouchable)
```

**Description**

Sets whether a window is touchable.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| bool isTouchable | Whether the window is touchable. **true** if touchable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowFocusable()

```c
int32_t OH_WindowManager_SetWindowFocusable(int32_t windowId, bool isFocusable)
```

**Description**

Sets whether a window is focusable.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| bool isFocusable | Whether the window is focusable. **true** if focusable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowBackgroundColor()

```c
int32_t OH_WindowManager_SetWindowBackgroundColor(int32_t windowId, const char* color)
```

**Description**

Sets the background color of a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| const char* color | Pointer to the background color. The value is a string in hexadecimal RGB or ARGB color format.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.|

### OH_WindowManager_SetWindowBrightness()

```c
int32_t OH_WindowManager_SetWindowBrightness(int32_t windowId, float brightness)
```

**Description**

Sets the window brightness for the main window. The window brightness takes effect only when the window is in the foreground and has focus.

When the setting is valid, it affects only the physical screen where the window is displayed. It does not apply to virtual displays (for example, casting/mirroring screens).

If the input parameter is **-1**, the window brightness reverts to the system brightness (which can be adjusted through Control Panel or shortcut keys).

When the window moves to the background, the setting becomes invalid, and brightness can be adjusted through Control Panel or shortcut keys. You are not advised to call this API when the window is in the background, as it may cause timing issues.

**Device behavior differences**:
- For TVs: This API does not take effect or report an error.
- For non-2-in-1 devices (excluding TVs):
  - Before <!--RP1-->OpenHarmony 6.1<!--RP1End-->, when the window brightness of the current window is active, adjusting the system screen brightness from the Control Panel does not take effect.
  - Since <!--RP1-->OpenHarmony 6.1<!--RP1End-->, Control Panel can adjust system brightness even when the window brightness of the current window is active. Doing so will automatically reset that window's brightness to match the new system brightness.
- For 2-in-1 devices:
  - Before OpenHarmony 5.0.2, when the screen brightness set by a window is active, adjusting the system screen brightness from the Control Panel or a shortcut key does not take effect.
  - Since OpenHarmony 5.0.2, window brightness is always synchronized with system brightness. Brightness can be adjusted through this API, Control Panel, or shortcut keys.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| float brightness | Screen brightness. The value is a floating-point number in the range [0.0, 1.0] or is set to **-1.0**. The value **1.0** means the brightest, and **-1.0** means that the window brightness resets to the original brightness set through Control Panel.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowKeepScreenOn()

```c
int32_t OH_WindowManager_SetWindowKeepScreenOn(int32_t windowId, bool isKeepScreenOn)
```

**Description**

Sets whether to always keep the screen on for a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| bool isKeepScreenOn | Whether to always keep the screen on. **true** to always keep the screen on, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_SetWindowPrivacyMode()

```c
int32_t OH_WindowManager_SetWindowPrivacyMode(int32_t windowId, bool isPrivacy)
```

**Description**

Sets whether to enable privacy mode for a window.

**Required permissions**: ohos.permission.PRIVACY_WINDOW

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| bool isPrivacy | Whether to enable privacy mode. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_NO_PERMISSION**: The permission verification fails.|

### OH_WindowManager_GetWindowProperties()

```c
int32_t OH_WindowManager_GetWindowProperties(int32_t windowId, WindowManager_WindowProperties* windowProperties)
```

**Description**

Obtains the properties of a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| [WindowManager_WindowProperties](capi-windowmanager-windowproperties.md)* windowProperties | Pointer to the properties.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called, and the pointer to the window properties is returned.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.|

### OH_WindowManager_Snapshot()

```c
int32_t OH_WindowManager_Snapshot(int32_t windowId, OH_PixelmapNative* pixelMap)
```

**Description**

Obtains the snapshot of a window.

**Since**: 15


**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.<br>If the window ID is invalid or the window has been destroyed, you cannot obtain the window snapshot. To successfully obtain a snapshot, a valid window ID is required.<br>You can obtain a valid window ID by calling the ArkTS API [getWindowProperties()](arkts-apis-window-Window.md#getwindowproperties9) on the window object|
| [OH_PixelmapNative](capi-struct.md)* pixelMap | Pointer to the snapshot.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called, and the pointer to the pixelMap is returned.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_GetAllWindowLayoutInfoList()

```c
int32_t OH_WindowManager_GetAllWindowLayoutInfoList(int64_t displayId,WindowManager_Rect** windowLayoutInfoList, size_t* windowLayoutInfoSize)
```

**Description**

Obtains the layout information array of all windows visible on a display. The layout information is arranged based on the current window stacking order, and the topmost window in the hierarchy is at index 0 of the array.

**Since**: 17


**Parameters**

| Parameter| Description|
| -- | -- |
| int64_t displayId | ID of the display. You can obtain a valid display ID by calling the ArkTS API [getWindowProperties()](arkts-apis-window-Window.md#getwindowproperties9) on the window object|
| [WindowManager_Rect](capi-windowmanager-rect.md)** windowLayoutInfoList | Double pointer to the layout information array of all windows visible. This parameter is used as an output parameter.|
| size_t* windowLayoutInfoSize | Pointer to the length of the layout information array. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called, and the double pointer to the array and the pointer to the array length are returned.<br> **WINDOW_MANAGER_ERRORCODE_INVALID_PARAM**: A parameter is incorrect.<br> **WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br> **WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_ReleaseAllWindowLayoutInfoList()

```c
void OH_WindowManager_ReleaseAllWindowLayoutInfoList(WindowManager_Rect* windowLayoutInfoList)
```

**Description**

Releases the memory occupied by a window layout information array.

**Since**: 17


**Parameters**

| Parameter| Description|
| -- | -- |
| [WindowManager_Rect](capi-windowmanager-rect.md)* windowLayoutInfoList | Pointer to the layout information array of all windows visible on the display. You can obtain the array pointer by calling [OH_WindowManager_GetAllWindowLayoutInfoList](capi-oh-window-h.md#oh_windowmanager_getallwindowlayoutinfolist).|
### OH_WindowManager_InjectTouchEvent()

```c
int32_t OH_WindowManager_InjectTouchEvent(int32_t windowId, Input_TouchEvent* touchEvent, int32_t windowX, int32_t windowY)
```

**Description**

Injects a multimodal touch event into the target window. This function is limited to injecting events into windows that belong to the same process. The injection does not affect window focus or stacking order, nor does it start window dragging. The event is forwarded directly to ArkUI. This function must be called after the target window has completed its UI loading.

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The default value is **0**. The value is an integer.|
| [Input_TouchEvent](../apis-input-kit/capi-input-input-touchevent.md)* touchEvent | Pointer to the multimodal touch event. For details, see [Input_TouchEvent](../apis-input-kit/capi-input-input-touchevent.md). The event is defined in **oh_input_manager.h**. Certain fields in this parameter have specific constraints. Specifically, **action** should be an integer in the range [0, 3]; **id**, **displayX**, **displayY**, and **actionTime** should be an integer greater than or equal to 0. If these constraints are not met, the function returns **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**, indicating that the window manager service is abnormal.|
| int32_t windowX | X coordinate of the event relative to the target window. The value is an integer.|
| int32_t windowY | Y coordinate of the event relative to the target window. The value is an integer.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_GetAllMainWindowInfo()

```c
int32_t OH_WindowManager_GetAllMainWindowInfo(WindowManager_MainWindowInfo** infoList, size_t* mainWindowInfoSize)
```

**Description**

Obtains the information about all main windows.

**Device behavior differences**: This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Required permissions**: ohos.permission.CUSTOM_SCREEN_CAPTURE

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [WindowManager_MainWindowInfo](capi-windowmanager-windowmanager-mainwindowinfo.md)** infoList | Double pointer to the main window information list. This parameter is used as an output parameter.|
| size_t* mainWindowInfoSize | Pointer to the size of the main window information list. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_NO_PERMISSION**: The permission verification fails.<br>**WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br>**WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_ReleaseAllMainWindowInfo()

```c
void OH_WindowManager_ReleaseAllMainWindowInfo(WindowManager_MainWindowInfo* infoList)
```

**Description**

Releases the memory used by the main window information list.

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [WindowManager_MainWindowInfo](capi-windowmanager-windowmanager-mainwindowinfo.md)* infoList | Pointer to the main window information list.|

### OH_WindowManager_WindowSnapshotCallback()

```c
typedef void (*OH_WindowManager_WindowSnapshotCallback)(const OH_PixelmapNative** snapshotPixelMapList, size_t snapshotListSize)
```

**Description**

Defines the callback used for receiving the main window screenshot list.

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_PixelmapNative](capi-struct.md)** snapshotPixelMapList | Double pointer to the list of window screenshots.|
|  size_t snapshotListSize | Size of the window screenshot list.|

### OH_WindowManager_GetMainWindowSnapshot()

```c
int32_t OH_WindowManager_GetMainWindowSnapshot(int32_t* windowIdList, size_t windowIdListSize, WindowManager_WindowSnapshotConfig config, OH_WindowManager_WindowSnapshotCallback callback)
```

**Description**

Obtains the screenshots of one or more main windows specified by **windowId**.

**Device behavior differences**: This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Required permissions**: ohos.permission.CUSTOM_SCREEN_CAPTURE

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t* windowIdList | Pointer to the main window ID list.|
| size_t windowIdListSize | Size of the main window ID list.|
| [WindowManager_WindowSnapshotConfig](capi-windowmanager-windowmanager-windowsnapshotconfig.md) config | Configuration for obtaining the window screenshot.|
| [OH_WindowManager_WindowSnapshotCallback](capi-oh-window-h.md#oh_windowmanager_windowsnapshotcallback) callback | Callback used to return the lists of window screenshots, in the order of the provided window ID array.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_NO_PERMISSION**: The permission verification fails.<br>**WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The feature is not supported by the device.<br>**WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_ReleaseMainWindowSnapshot()

```c
void OH_WindowManager_ReleaseMainWindowSnapshot(const OH_PixelmapNative* snapshotPixelMapList)
```

**Description**

Releases the memory used by the main window screenshot list.

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_PixelmapNative](capi-struct.md)* snapshotPixelMapList | Pointer to the list of window screenshots.|

### OH_WindowManager_LockCursor()

```c
int32_t OH_WindowManager_LockCursor(int32_t windowId, bool isCursorFollowMovement)
```

**Description**

Locks the mouse cursor within the specified window area and controls whether the cursor follows mouse movements. It is only supported by the window that currently has focus, and the lock is automatically released when the window loses focus.

**Required permissions**: ohos.permission.LOCK_WINDOW_CURSOR

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The value is an integer.|
| bool isCursorFollowMovement | Behavior of the mouse cursor when locked. If it is set to **true**, the cursor moves along with the mouse. If it is set to **false**, the cursor remains stationary and does not follow mouse movements.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_NO_PERMISSION**: You do not have the permission to call the API.<br>**WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_UnlockCursor()

```c
int32_t OH_WindowManager_UnlockCursor(int32_t windowId)
```

**Description**

Clears the mouse cursor mode previously set for the window.

**Required permissions**: ohos.permission.LOCK_WINDOW_CURSOR

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID. The value is an integer.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_NO_PERMISSION**: You do not have the permission to call the API.<br>**WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED**: The device is not supported.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_SYSTEM_ABNORMAL**: The window manager service is abnormal.|

### OH_WindowManager_FrameMetrics_IsFirstDrawFrame()

```c
int32_t OH_WindowManager_FrameMetrics_IsFirstDrawFrame(const OH_WindowManager_FrameMetrics* metrics, bool* isFirstDrawFrame)
```

**Description**

Checks whether this frame is the first frame.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_FrameMetrics](capi-windowmanager-oh-windowmanager-framemetrics.md)* metrics | Pointer to the frame metric data object.|
| bool* isFirstDrawFrame | Pointer to **isFirstDrawFrame** indicating whether the current frame is the first frame. This parameter is used as an output parameter. **true** indicates that this frame is the first frame, and **false** indicates the opposite.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_FrameMetrics_GetInputHandlingDuration()

```c
int32_t OH_WindowManager_FrameMetrics_GetInputHandlingDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)
```

**Description**

Obtains the time consumed for gesture handling in this frame.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_FrameMetrics](capi-windowmanager-oh-windowmanager-framemetrics.md)* metrics | Pointer to the frame metric data object.|
| uint64_t* duration | Pointer to the time consumed for gesture handling in this frame, in nanoseconds. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration()

```c
int32_t OH_WindowManager_FrameMetrics_GetLayoutMeasureDuration(const OH_WindowManager_FrameMetrics* metrics, uint64_t* duration)
```

**Description**

Obtains the time consumed for layout measurement in this frame.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_FrameMetrics](capi-windowmanager-oh-windowmanager-framemetrics.md)* metrics | Pointer to the frame metric data object.|
| uint64_t* duration | Pointer to the time consumed for layout measurement in this frame, in nanoseconds. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_FrameMetrics_GetVsyncTimestamp()

```c
int32_t OH_WindowManager_FrameMetrics_GetVsyncTimestamp(const OH_WindowManager_FrameMetrics* metrics, uint64_t* timestamp)
```

**Description**

Obtains the timestamp when this frame starts.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_FrameMetrics](capi-windowmanager-oh-windowmanager-framemetrics.md)* metrics | Pointer to the frame metric data object.|
| uint64_t* timestamp | Pointer to the timestamp when this frame starts, in nanoseconds. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_RegisterFrameMetricsMeasuredCallback()

```c
int32_t OH_WindowManager_RegisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)
```

**Description**

Registers a callback for window frame metric change events.<br> This API depends on the loading of the window page content. That is, this API can be called only after the **loadContent()** or **setUIContent()** API in ArkTS takes effect.<br> The callback is triggered only when the client UI content is redrawn (for example, page switching, interaction with responsive components, or background color and opacity setting).<br> To cancel the registration, call the [OH_WindowManager_UnregisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_unregisterframemetricsmeasuredcallback) API.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID.|
| [OH_WindowManager_FrameMetricsMeasuredCallback](capi-oh-window-comm-h.md#oh_windowmanager_framemetricsmeasuredcallback) callback | Callback used to return the result.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal. Possible causes:<br> 1. The window has not been created or has been destroyed.<br> 2. The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_UnregisterFrameMetricsMeasuredCallback()

```c
int32_t OH_WindowManager_UnregisterFrameMetricsMeasuredCallback(int32_t windowId, OH_WindowManager_FrameMetricsMeasuredCallback callback)
```

**Description**

Unregisters the callback for window frame metric change events.<br> This API depends on the loading of the window page content. That is, this API can be called only after the **loadContent()** or **setUIContent()** API in ArkTS takes effect.<br> To register such a callback, call the [OH_WindowManager_RegisterFrameMetricsMeasuredCallback](capi-oh-window-h.md#oh_windowmanager_registerframemetricsmeasuredcallback) API.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID.|
| [OH_WindowManager_FrameMetricsMeasuredCallback](capi-oh-window-comm-h.md#oh_windowmanager_framemetricsmeasuredcallback) callback | Callback used to return the result.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br> **OK**: The function is successfully called.<br> **WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal. Possible causes:<br> 1. The window has not been created or has been destroyed.<br> 2. The window status is abnormal.<br> **WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: The parameter is incorrect. The value range of the parameter is improper.<br> For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_DensityInfo_GetDefaultDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetDefaultDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Obtains the scale factor of the system default display size of the screen where the window is located.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md)* info | Pointer to the window scale factor information, which can be obtained through [OH_WindowManager_GetDensityInfoCopy](capi-oh-window-h.md#oh_windowmanager_getdensityinfocopy).|
| float* density | Pointer to the scale factor of the system default display size. The value ranges from 0.5 to 4.0. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_DensityInfo_GetSystemDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetSystemDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Obtains the scale factor of the system display size of the screen where the window is located.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md)* info | Pointer to the window scale factor information, which can be obtained through [OH_WindowManager_GetDensityInfoCopy](capi-oh-window-h.md#oh_windowmanager_getdensityinfocopy).|
| float* density | Pointer to the scale factor of the system display size. The value ranges from 0.5 to 4.0. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_DensityInfo_GetCustomDensity()

```c
int32_t OH_WindowManager_DensityInfo_GetCustomDensity(const OH_WindowManager_DensityInfo* info, float* density)
```

**Description**

Obtains the scale factor of the custom display size of the window.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md)* info | Pointer to the window scale factor information, which can be obtained through [OH_WindowManager_GetDensityInfoCopy](capi-oh-window-h.md#oh_windowmanager_getdensityinfocopy).|
| float* density | Pointer to the scale factor of the custom display size of the window. The value ranges from 0.5 to 4.0. This parameter is used as an output parameter.<br>If this parameter is not set, the scale factor of the system display size is used. For a child window, global floating window, modal window, or system window, the scale factor of the custom display size is equal to the scale factor of the system display size (**systemDensity**).|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_GetDensityInfoCopy()

```c
int32_t OH_WindowManager_GetDensityInfoCopy(int32_t windowId, const OH_WindowManager_DensityInfo** info)
```

**Description**

Obtains window scale factor information, including the scale factors of the system display size, system default display size, and custom display size. The priorities in descending order are as follows:

- Scale factor of the custom display size: window-level display scale factor, which affects only a single window.

- Scale factor of the system display size: display size scale factor set in the current system.

- Scale factor of the system default display size: default reference scale factor of the system.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID when the window is created.|
| [const OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md)** info | Double pointer to the window scale factor information, which is used as an output parameter.<br>If the return value is **NULL**, the device does not support this API.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal. Possible causes: 1. The window has not been created or has been destroyed. 2. The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_RegisterDensityInfoChangeCallback()

```c
int32_t OH_WindowManager_RegisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)
```

**Description**

Registers a callback for listening to window scale factor changes.

This callback will be triggered when any of the following changes: the scale factor of the system display size of the screen where the window is located, the scale factor of the system default display size, or the scale factor of the custom display size.

To unregister this callback, use [OH_WindowManager_UnregisterDensityInfoChangeCallback](capi-oh-window-h.md#oh_windowmanager_unregisterdensityinfochangecallback).

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID when the window is created.|
| [OH_WindowManager_DensityInfoCallback](capi-oh-window-comm-h.md#oh_windowmanager_densityinfocallback) callback | Callback used to return the window scale factor.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal. Possible causes: 1. The window has not been created or has been destroyed. 2. The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_UnregisterDensityInfoChangeCallback()

```c
int32_t OH_WindowManager_UnregisterDensityInfoChangeCallback(int32_t windowId, OH_WindowManager_DensityInfoCallback callback)
```

**Description**

Unregisters the callback for listening to window scale factor changes.

This callback will not be triggered after being unregistered even if any of the following changes: the scale factor of the system display size of the screen where the window is located, the scale factor of the system default display size, or the scale factor of the custom display size.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t windowId | Window ID when the window is created.|
| [OH_WindowManager_DensityInfoCallback](capi-oh-window-comm-h.md#oh_windowmanager_densityinfocallback) callback | Callback used to return the window scale factor.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_STATE_ABNORMAL**: The window status is abnormal. Possible causes: 1. The window has not been created or has been destroyed. 2. The window status is abnormal.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|

### OH_WindowManager_DensityInfo_Release()

```c
int32_t OH_WindowManager_DensityInfo_Release(const OH_WindowManager_DensityInfo* info)
```

**Description**

Releases the memory occupied by the window scale factor object.

**Since:** 24

**Parameters**

| Parameter| Description|
| -- | -- |
| [const OH_WindowManager_DensityInfo](capi-windowmanager-oh-windowmanager-densityinfo.md)* info | Pointer to the window scale factor information. This parameter is used as an output parameter.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | One of the following result codes:<br>**OK**: The function is successfully called.<br>**WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM**: A parameter is incorrect. Possible cause: The parameter value is invalid.<br>For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode).|
