# oh_window_pip.h

## Overview

The file declares the APIs related to the Picture in Picture (PiP) feature, including creating and deleting a PiP controller, and starting and stopping PiP. PiP is mainly used in video playback, live streaming, video calls, or video meetings.

**Library**: libnative_window_manager.so

**System capability**: SystemCapability.Window.SessionManager

**Since**: 12

**Related module**: [WindowManager](capi-windowmanager.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PictureInPicture_PipConfig](capi-windowmanager-pictureinpicture-pipconfig.md) | PictureInPicture_PipConfig | Picture in picture config. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PictureInPicture_PipTemplateType](#pictureinpicture_piptemplatetype) | PictureInPicture_PipTemplateType | Enumerates the types of PiP templates. |
| [PictureInPicture_PipControlGroup](#pictureinpicture_pipcontrolgroup) | PictureInPicture_PipControlGroup | Enumerates the types of component groups displayed on the PiP controller. |
| [PictureInPicture_PipControlType](#pictureinpicture_pipcontroltype) | PictureInPicture_PipControlType | Enumerates the types of components displayed on the PiP controller. |
| [PictureInPicture_PipControlStatus](#pictureinpicture_pipcontrolstatus) | PictureInPicture_PipControlStatus | Enumerates the statuses of components displayed on the PiP controller. |
| [PictureInPicture_PipState](#pictureinpicture_pipstate) | PictureInPicture_PipState | Enumerates the PiP lifecycle states. |

### Macro

| Name | Description |
| -- | -- |
| OH_WINDOW_PIP_H | The file declares the APIs related to the Picture in Picture (PiP) feature, including creating and deleting a PiP controller, and starting and stopping PiP. PiP is mainly used in video playback, live streaming, video calls, or video meetings.<br>**Since**: 20<br>**System capability**: SystemCapability.Window.SessionManager |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*WebPipStartPipCallback)(uint32_t controllerId, uint8_t requestId, uint64_t surfaceId)](#webpipstartpipcallback) | WebPipStartPipCallback | Defines a callback function for PiP window creation. |
| [typedef void (\*WebPipLifecycleCallback)(uint32_t controllerId, PictureInPicture_PipState state, int32_t errcode)](#webpiplifecyclecallback) | WebPipLifecycleCallback | Defines a callback function for PiP window lifecycle changes. |
| [typedef void (\*WebPipControlEventCallback)(uint32_t controllerId, PictureInPicture_PipControlType controlType, PictureInPicture_PipControlStatus status)](#webpipcontroleventcallback) | WebPipControlEventCallback | Defines a callback function for the component click event of the PiP window. |
| [typedef void (\*WebPipResizeCallback)(uint32_t controllerId, uint32_t width, uint32_t height, double scale)](#webpipresizecallback) | WebPipResizeCallback | Defines a callback function for PiP window size changes. |
| [int32_t OH_PictureInPicture_CreatePipConfig(PictureInPicture_PipConfig* pipConfig)](#oh_pictureinpicture_createpipconfig) | - | Creates a PiP configuration. |
| [int32_t OH_PictureInPicture_DestroyPipConfig(PictureInPicture_PipConfig* pipConfig)](#oh_pictureinpicture_destroypipconfig) | - | Destroys a PiP configuration. |
| [int32_t OH_PictureInPicture_SetPipMainWindowId(PictureInPicture_PipConfig pipConfig, uint32_t mainWindowId)](#oh_pictureinpicture_setpipmainwindowid) | - | Sets the ID of the main window that launches PiP. |
| [int32_t OH_PictureInPicture_SetPipTemplateType(PictureInPicture_PipConfig pipConfig, PictureInPicture_PipTemplateType pipTemplateType)](#oh_pictureinpicture_setpiptemplatetype) | - | Sets the PiP template type. The default value is video playback. |
| [int32_t OH_PictureInPicture_SetPipRect(PictureInPicture_PipConfig pipConfig, uint32_t width, uint32_t height)](#oh_pictureinpicture_setpiprect) | - | Sets the size of the PiP window for calculating the aspect ratio. |
| [int32_t OH_PictureInPicture_SetPipControlGroup(PictureInPicture_PipConfig pipConfig, PictureInPicture_PipControlGroup* controlGroup, uint8_t controlGroupLength)](#oh_pictureinpicture_setpipcontrolgroup) | - | Sets a PiP component group, which must match the template type. |
| [int32_t OH_PictureInPicture_SetPipNapiEnv(PictureInPicture_PipConfig pipConfig, void* env)](#oh_pictureinpicture_setpipnapienv) | - | Sets the runtime environment for launching PiP. |
| [int32_t OH_PictureInPicture_CreatePip(PictureInPicture_PipConfig pipConfig, uint32_t* controllerId)](#oh_pictureinpicture_createpip) | - | Creates a PiP controller. |
| [int32_t OH_PictureInPicture_DeletePip(uint32_t controllerId)](#oh_pictureinpicture_deletepip) | - | Deletes a PiP controller. |
| [int32_t OH_PictureInPicture_StartPip(uint32_t controllerId)](#oh_pictureinpicture_startpip) | - | Starts PiP. |
| [int32_t OH_PictureInPicture_StopPip(uint32_t controllerId)](#oh_pictureinpicture_stoppip) | - | Stops PiP. |
| [int32_t OH_PictureInPicture_UpdatePipContentSize(uint32_t controllerId, uint32_t width, uint32_t height)](#oh_pictureinpicture_updatepipcontentsize) | - | Updates the media content size when the media content changes. |
| [int32_t OH_PictureInPicture_UpdatePipControlStatus(uint32_t controllerId, PictureInPicture_PipControlType controlType, PictureInPicture_PipControlStatus status)](#oh_pictureinpicture_updatepipcontrolstatus) | - | Updates the PiP component status. |
| [int32_t OH_PictureInPicture_SetPipControlEnabled(uint32_t controllerId, PictureInPicture_PipControlType controlType, bool enabled)](#oh_pictureinpicture_setpipcontrolenabled) | - | Sets the PiP component enabled status. |
| [int32_t OH_PictureInPicture_SetParentWindowId(uint32_t controllerId, uint32_t windowId)](#oh_pictureinpicture_setparentwindowid) | - | Sets the main window ID for PiP. |
| [int32_t OH_PictureInPicture_SetPipInitialSurfaceRect(uint32_t controllerId, int32_t positionX, int32_t positionY, uint32_t width, uint32_t height)](#oh_pictureinpicture_setpipinitialsurfacerect) | - | Sets the initial position and size of the PiP surface when the PiP launch animation starts. It can be used to achieve a seamless transition effect. |
| [int32_t OH_PictureInPicture_UnsetPipInitialSurfaceRect(uint32_t controllerId)](#oh_pictureinpicture_unsetpipinitialsurfacerect) | - | Cancels the previously set initial position and size for the PiP surface. |
| [int32_t OH_PictureInPicture_RegisterStartPipCallback(uint32_t controllerId, WebPipStartPipCallback callback)](#oh_pictureinpicture_registerstartpipcallback) | - | Registers a callback to listen for the completion of PiP surface creation. |
| [int32_t OH_PictureInPicture_UnregisterStartPipCallback(uint32_t controllerId, WebPipStartPipCallback callback)](#oh_pictureinpicture_unregisterstartpipcallback) | - | Unregisters the callback used to listen for the completion of PiP surface creation. |
| [int32_t OH_PictureInPicture_UnregisterAllStartPipCallbacks(uint32_t controllerId)](#oh_pictureinpicture_unregisterallstartpipcallbacks) | - | Unregisters all the callbacks used to listen for the completion of PiP surface creation. |
| [int32_t OH_PictureInPicture_RegisterLifecycleListener(uint32_t controllerId, WebPipLifecycleCallback callback)](#oh_pictureinpicture_registerlifecyclelistener) | - | Registers a callback to listen for PiP lifecycle state changes. |
| [int32_t OH_PictureInPicture_UnregisterLifecycleListener(uint32_t controllerId, WebPipLifecycleCallback callback)](#oh_pictureinpicture_unregisterlifecyclelistener) | - | Unregisters the callback used to listen for PiP lifecycle state changes. |
| [int32_t OH_PictureInPicture_UnregisterAllLifecycleListeners(uint32_t controllerId)](#oh_pictureinpicture_unregisteralllifecyclelisteners) | - | Unregisters all the callbacks used to listen for PiP lifecycle state changes. |
| [int32_t OH_PictureInPicture_RegisterControlEventListener(uint32_t controllerId, WebPipControlEventCallback callback)](#oh_pictureinpicture_registercontroleventlistener) | - | Registers a callback to listen for control panel action events in PiP mode. |
| [int32_t OH_PictureInPicture_UnregisterControlEventListener(uint32_t controllerId, WebPipControlEventCallback callback)](#oh_pictureinpicture_unregistercontroleventlistener) | - | Unregisters the callback used to listen for control panel action events in PiP mode. |
| [int32_t OH_PictureInPicture_UnregisterAllControlEventListeners(uint32_t controllerId)](#oh_pictureinpicture_unregisterallcontroleventlisteners) | - | Unregisters all the callbacks used to listen for control panel action events in PiP mode. |
| [int32_t OH_PictureInPicture_RegisterResizeListener(uint32_t controllerId, WebPipResizeCallback callback)](#oh_pictureinpicture_registerresizelistener) | - | Registers a callback to listen for PiP window size changes. |
| [int32_t OH_PictureInPicture_UnregisterResizeListener(uint32_t controllerId, WebPipResizeCallback callback)](#oh_pictureinpicture_unregisterresizelistener) | - | Unregisters the callback used to listen for PiP window size changes. |
| [int32_t OH_PictureInPicture_UnregisterAllResizeListeners(uint32_t controllerId)](#oh_pictureinpicture_unregisterallresizelisteners) | - | Unregisters all the callbacks used to listen for PiP window size changes. |
| [int32_t OH_PictureInPicture_SetAutoStartEnabled(uint32_t controllerId, bool enabled)](#oh_pictureinpicture_setautostartenabled) | - | Sets whether to automatically start a PiP window when the user returns to the home screen. By default, no PiP window is started. |

### Variable

| Name | Description |
| -- | -- |
| void* PictureInPicture_PipConfig | Picture in picture config.<br>**Since**: 20 |
| void (*WebPipStartPipCallback)(uint32_t controllerId, uint8_t requestId, uint64_t surfaceId) | Defines a callback function for PiP window creation.<br>**Since**: 20 |
| void (*WebPipLifecycleCallback)(uint32_t controllerId, PictureInPicture_PipState state, int32_t errcode) | Defines a callback function for PiP window lifecycle changes.<br>**Since**: 20 |
| void (*WebPipControlEventCallback)(uint32_t controllerId, PictureInPicture_PipControlType controlType, PictureInPicture_PipControlStatus status) | Defines a callback function for the component click event of the PiP window.<br>**Since**: 20 |
| void (*WebPipResizeCallback)(uint32_t controllerId, uint32_t width, uint32_t height, double scale) | Defines a callback function for PiP window size changes.<br>**Since**: 20 |

## Enum type description

### PictureInPicture_PipTemplateType

```c
enum PictureInPicture_PipTemplateType
```

**Description**

Enumerates the types of PiP templates.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| VIDEO_PLAY = 0 |  |
| VIDEO_CALL = 1 |  |
| VIDEO_MEETING = 2 |  |
| VIDEO_LIVE = 3 |  |

### PictureInPicture_PipControlGroup

```c
enum PictureInPicture_PipControlGroup
```

**Description**

Enumerates the types of component groups displayed on the PiP controller.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| VIDEO_PLAY_VIDEO_PREVIOUS_NEXT = 101 |  |
| VIDEO_PLAY_FAST_FORWARD_BACKWARD = 102 |  |
| VIDEO_CALL_MICROPHONE_SWITCH = 201 |  |
| VIDEO_CALL_HANG_UP_BUTTON = 202 |  |
| VIDEO_CALL_CAMERA_SWITCH = 203 |  |
| VIDEO_CALL_MUTE_SWITCH = 204 |  |
| VIDEO_MEETING_HANG_UP_BUTTON = 301 |  |
| VIDEO_MEETING_CAMERA_SWITCH = 302 |  |
| VIDEO_MEETING_MUTE_SWITCH = 303 |  |
| VIDEO_MEETING_MICROPHONE_SWITCH = 304 |  |
| VIDEO_LIVE_VIDEO_PLAY_PAUSE = 401 |  |
| VIDEO_LIVE_MUTE_SWITCH = 402 |  |

### PictureInPicture_PipControlType

```c
enum PictureInPicture_PipControlType
```

**Description**

Enumerates the types of components displayed on the PiP controller.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| VIDEO_PLAY_PAUSE = 0 |  |
| VIDEO_PREVIOUS = 1 |  |
| VIDEO_NEXT = 2 |  |
| FAST_FORWARD = 3 |  |
| FAST_BACKWARD = 4 |  |
| HANG_UP_BUTTON = 5 |  |
| MICROPHONE_SWITCH = 6 |  |
| CAMERA_SWITCH = 7 |  |
| MUTE_SWITCH = 8 |  |

### PictureInPicture_PipControlStatus

```c
enum PictureInPicture_PipControlStatus
```

**Description**

Enumerates the statuses of components displayed on the PiP controller.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| PLAY = 1 |  |
| PAUSE = 0 |  |
| OPEN = 1 |  |
| CLOSE = 0 |  |

### PictureInPicture_PipState

```c
enum PictureInPicture_PipState
```

**Description**

Enumerates the PiP lifecycle states.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

| Enum item | Description |
| -- | -- |
| ABOUT_TO_START = 1 |  |
| STARTED = 2 |  |
| ABOUT_TO_STOP = 3 |  |
| STOPPED = 4 |  |
| ABOUT_TO_RESTORE = 5 |  |
| ERROR = 6 |  |


## Function description

### WebPipStartPipCallback()

```c
typedef void (*WebPipStartPipCallback)(uint32_t controllerId, uint8_t requestId, uint64_t surfaceId)
```

**Description**

Defines a callback function for PiP window creation.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| uint8_t requestId | Request ID, which indicates the number of times the PiP window has been requested to be pulled up. |
| uint64_t surfaceId | Surface ID of the **XComponent** in PiP. It is used for application rendering. |

### WebPipLifecycleCallback()

```c
typedef void (*WebPipLifecycleCallback)(uint32_t controllerId, PictureInPicture_PipState state, int32_t errcode)
```

**Description**

Defines a callback function for PiP window lifecycle changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [PictureInPicture_PipState](capi-oh-window-pip-h.md#pictureinpicture_pipstate) state | PiP lifecycle state. |
| int32_t errcode | Common status codes of PiP APIs. For details, see [WindowManager_ErrorCode](capi-oh-window-comm-h.md#windowmanager_errorcode). |

### WebPipControlEventCallback()

```c
typedef void (*WebPipControlEventCallback)(uint32_t controllerId, PictureInPicture_PipControlType controlType, PictureInPicture_PipControlStatus status)
```

**Description**

Defines a callback function for the component click event of the PiP window.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [PictureInPicture_PipControlType](capi-oh-window-pip-h.md#pictureinpicture_pipcontroltype) controlType | Type of component displayed on the PiP controller. |
| [PictureInPicture_PipControlStatus](capi-oh-window-pip-h.md#pictureinpicture_pipcontrolstatus) status | Status of the component displayed on the PiP controller. |

### WebPipResizeCallback()

```c
typedef void (*WebPipResizeCallback)(uint32_t controllerId, uint32_t width, uint32_t height, double scale)
```

**Description**

Defines a callback function for PiP window size changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| uint32_t width | PiP window width, in px. The value is a positive integer and cannot be greater than the screen width. |
| uint32_t height | PiP window height, in px. The value is a positive integer and cannot be greater than the screen height. |
| double scale | Scale factor of the PiP window, representing the display size relative to the width and height. The value is a floating-point number in the range (0.0, 1.0]. The value **1** means that the PiP window matches specified width and height. |

### OH_PictureInPicture_CreatePipConfig()

```c
int32_t OH_PictureInPicture_CreatePipConfig(PictureInPicture_PipConfig* pipConfig)
```

**Description**

Creates a PiP configuration.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig* pipConfig | Pointer to the PiP parameter configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. |

### OH_PictureInPicture_DestroyPipConfig()

```c
int32_t OH_PictureInPicture_DestroyPipConfig(PictureInPicture_PipConfig* pipConfig)
```

**Description**

Destroys a PiP configuration.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig* pipConfig | Pointer to the PiP configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. |

### OH_PictureInPicture_SetPipMainWindowId()

```c
int32_t OH_PictureInPicture_SetPipMainWindowId(PictureInPicture_PipConfig pipConfig, uint32_t mainWindowId)
```

**Description**

Sets the ID of the main window that launches PiP.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| uint32_t mainWindowId | ID of the main window that launches PiP. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported. |

### OH_PictureInPicture_SetPipTemplateType()

```c
int32_t OH_PictureInPicture_SetPipTemplateType(PictureInPicture_PipConfig pipConfig, PictureInPicture_PipTemplateType pipTemplateType)
```

**Description**

Sets the PiP template type. The default value is video playback.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| [PictureInPicture_PipTemplateType](capi-oh-window-pip-h.md#pictureinpicture_piptemplatetype) pipTemplateType | Type of the PiP template. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported. |

### OH_PictureInPicture_SetPipRect()

```c
int32_t OH_PictureInPicture_SetPipRect(PictureInPicture_PipConfig pipConfig, uint32_t width, uint32_t height)
```

**Description**

Sets the size of the PiP window for calculating the aspect ratio.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| uint32_t width | Width of the original content, in px. The value must be a positive integer. It is used to determine the aspect ratio of the PiP window. |
| uint32_t height | Height of the original content, in px. The value must be a positive integer. It is used to determine the aspect ratio of the PiP window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported. |

### OH_PictureInPicture_SetPipControlGroup()

```c
int32_t OH_PictureInPicture_SetPipControlGroup(PictureInPicture_PipConfig pipConfig, PictureInPicture_PipControlGroup* controlGroup, uint8_t controlGroupLength)
```

**Description**

Sets a PiP component group, which must match the template type.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| [PictureInPicture_PipControlGroup](capi-oh-window-pip-h.md#pictureinpicture_pipcontrolgroup)* controlGroup | Pointer to an optional component group of the PiP controller. An application can configure whether to display these optional components. If this parameter is not set for an application, the basic components (for example, play/pause of the video playback component group) are displayed. A maximum of three components can be configured. |
| uint8_t controlGroupLength | Number of components in the PiP component group. The value ranges from 0 to 3. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported. |

### OH_PictureInPicture_SetPipNapiEnv()

```c
int32_t OH_PictureInPicture_SetPipNapiEnv(PictureInPicture_PipConfig pipConfig, void* env)
```

**Description**

Sets the runtime environment for launching PiP.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| void* env | Pointer to the NAPI environment. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported. |

### OH_PictureInPicture_CreatePip()

```c
int32_t OH_PictureInPicture_CreatePip(PictureInPicture_PipConfig pipConfig, uint32_t* controllerId)
```

**Description**

Creates a PiP controller.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| PictureInPicture_PipConfig pipConfig | PiP configuration. |
| uint32_t* controllerId | Pointer to the ID of the PiP controller created. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_DeletePip()

```c
int32_t OH_PictureInPicture_DeletePip(uint32_t controllerId)
```

**Description**

Deletes a PiP controller.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) The function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. |

### OH_PictureInPicture_StartPip()

```c
int32_t OH_PictureInPicture_StartPip(uint32_t controllerId)
```

**Description**

Starts PiP.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_PIP_STATE_ABNORMAL](capi-oh-window-comm-h.md#windowmanager_errorcode) the PiP window state is abnormal.          [WINDOW_MANAGER_ERRORCODE_PIP_CREATE_FAILED](capi-oh-window-comm-h.md#windowmanager_errorcode) failed to create the PiP window.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error.          [WINDOW_MANAGER_ERRORCODE_PIP_REPEATED_OPERATION](capi-oh-window-comm-h.md#windowmanager_errorcode) repeated PiP operation.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. |

### OH_PictureInPicture_StopPip()

```c
int32_t OH_PictureInPicture_StopPip(uint32_t controllerId)
```

**Description**

Stops PiP.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_PIP_DESTROY_FAILED](capi-oh-window-comm-h.md#windowmanager_errorcode) failed to destroy the PiP window.          [WINDOW_MANAGER_ERRORCODE_PIP_STATE_ABNORMAL](capi-oh-window-comm-h.md#windowmanager_errorcode) the PiP window state is abnormal.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error.          [WINDOW_MANAGER_ERRORCODE_PIP_REPEATED_OPERATION](capi-oh-window-comm-h.md#windowmanager_errorcode) repeated PiP operation.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. |

### OH_PictureInPicture_UpdatePipContentSize()

```c
int32_t OH_PictureInPicture_UpdatePipContentSize(uint32_t controllerId, uint32_t width, uint32_t height)
```

**Description**

Updates the media content size when the media content changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| uint32_t width | Width of the media content, in px. The value must be a positive integer. It is used to update the aspect ratio of the PiP window. |
| uint32_t height | Height of the media content, in px. The value must be a positive integer. It is used to update the aspect ratio of the PiP window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UpdatePipControlStatus()

```c
int32_t OH_PictureInPicture_UpdatePipControlStatus(uint32_t controllerId, PictureInPicture_PipControlType controlType, PictureInPicture_PipControlStatus status)
```

**Description**

Updates the PiP component status.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [PictureInPicture_PipControlType](capi-oh-window-pip-h.md#pictureinpicture_pipcontroltype) controlType | Type of the component displayed on the PiP controller. Currently, only **VIDEO_PLAY_PAUSE**, **<br>MICROPHONE_SWITCH**, **CAMERA_SWITCH**, and **MUTE_SWITCH** are supported. |
| [PictureInPicture_PipControlStatus](capi-oh-window-pip-h.md#pictureinpicture_pipcontrolstatus) status | Status of the component displayed on the PiP controller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_SetPipControlEnabled()

```c
int32_t OH_PictureInPicture_SetPipControlEnabled(uint32_t controllerId, PictureInPicture_PipControlType controlType, bool enabled)
```

**Description**

Sets the PiP component enabled status.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [PictureInPicture_PipControlType](capi-oh-window-pip-h.md#pictureinpicture_pipcontroltype) controlType | Type of the component displayed on the PiP controller. |
| bool enabled | Enabled status of the component displayed on the PiP controller. **true** if enabled, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_SetParentWindowId()

```c
int32_t OH_PictureInPicture_SetParentWindowId(uint32_t controllerId, uint32_t windowId)
```

**Description**

Sets the main window ID for PiP.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| uint32_t windowId | ID of the main window. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_SetPipInitialSurfaceRect()

```c
int32_t OH_PictureInPicture_SetPipInitialSurfaceRect(uint32_t controllerId, int32_t positionX, int32_t positionY, uint32_t width, uint32_t height)
```

**Description**

Sets the initial position and size of the PiP surface when the PiP launch animation starts. It can be used to achieve a seamless transition effect.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| int32_t positionX | X coordinate of the PiP window relative to the top-left corner of the screen when the PiP window is started, in px. |
| int32_t positionY | Y coordinate of the PiP window relative to the top-left corner of the screen when the PiP window is started, in px. |
| uint32_t width | Width of the PiP window when the PiP window is started. The value is greater than 0, measured in px. |
| uint32_t height | Height of the PiP window when the PiP window is started. The value is greater than 0, measured in px. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnsetPipInitialSurfaceRect()

```c
int32_t OH_PictureInPicture_UnsetPipInitialSurfaceRect(uint32_t controllerId)
```

**Description**

Cancels the previously set initial position and size for the PiP surface.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_RegisterStartPipCallback()

```c
int32_t OH_PictureInPicture_RegisterStartPipCallback(uint32_t controllerId, WebPipStartPipCallback callback)
```

**Description**

Registers a callback to listen for the completion of PiP surface creation.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipStartPipCallback](capi-oh-window-pip-h.md#webpipstartpipcallback) callback | Callback function for PiP window creation. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterStartPipCallback()

```c
int32_t OH_PictureInPicture_UnregisterStartPipCallback(uint32_t controllerId, WebPipStartPipCallback callback)
```

**Description**

Unregisters the callback used to listen for the completion of PiP surface creation.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipStartPipCallback](capi-oh-window-pip-h.md#webpipstartpipcallback) callback | Callback function for PiP window creation. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterAllStartPipCallbacks()

```c
int32_t OH_PictureInPicture_UnregisterAllStartPipCallbacks(uint32_t controllerId)
```

**Description**

Unregisters all the callbacks used to listen for the completion of PiP surface creation.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_RegisterLifecycleListener()

```c
int32_t OH_PictureInPicture_RegisterLifecycleListener(uint32_t controllerId, WebPipLifecycleCallback callback)
```

**Description**

Registers a callback to listen for PiP lifecycle state changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipLifecycleCallback](capi-oh-window-pip-h.md#webpiplifecyclecallback) callback | Callback function for PiP window lifecycle changes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterLifecycleListener()

```c
int32_t OH_PictureInPicture_UnregisterLifecycleListener(uint32_t controllerId, WebPipLifecycleCallback callback)
```

**Description**

Unregisters the callback used to listen for PiP lifecycle state changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipLifecycleCallback](capi-oh-window-pip-h.md#webpiplifecyclecallback) callback | Callback function for PiP window lifecycle changes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterAllLifecycleListeners()

```c
int32_t OH_PictureInPicture_UnregisterAllLifecycleListeners(uint32_t controllerId)
```

**Description**

Unregisters all the callbacks used to listen for PiP lifecycle state changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_RegisterControlEventListener()

```c
int32_t OH_PictureInPicture_RegisterControlEventListener(uint32_t controllerId, WebPipControlEventCallback callback)
```

**Description**

Registers a callback to listen for control panel action events in PiP mode.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipControlEventCallback](capi-oh-window-pip-h.md#webpipcontroleventcallback) callback | Callback function for the component click event of the PiP window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterControlEventListener()

```c
int32_t OH_PictureInPicture_UnregisterControlEventListener(uint32_t controllerId, WebPipControlEventCallback callback)
```

**Description**

Unregisters the callback used to listen for control panel action events in PiP mode.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipControlEventCallback](capi-oh-window-pip-h.md#webpipcontroleventcallback) callback | Callback function for the component click event of the PiP window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterAllControlEventListeners()

```c
int32_t OH_PictureInPicture_UnregisterAllControlEventListeners(uint32_t controllerId)
```

**Description**

Unregisters all the callbacks used to listen for control panel action events in PiP mode.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_RegisterResizeListener()

```c
int32_t OH_PictureInPicture_RegisterResizeListener(uint32_t controllerId, WebPipResizeCallback callback)
```

**Description**

Registers a callback to listen for PiP window size changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipResizeCallback](capi-oh-window-pip-h.md#webpipresizecallback) callback | Callback function for PiP window size changes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterResizeListener()

```c
int32_t OH_PictureInPicture_UnregisterResizeListener(uint32_t controllerId, WebPipResizeCallback callback)
```

**Description**

Unregisters the callback used to listen for PiP window size changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| [WebPipResizeCallback](capi-oh-window-pip-h.md#webpipresizecallback) callback | Callback function for PiP window size changes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_UnregisterAllResizeListeners()

```c
int32_t OH_PictureInPicture_UnregisterAllResizeListeners(uint32_t controllerId)
```

**Description**

Unregisters all the callbacks used to listen for PiP window size changes.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code.          [OK](capi-uchar-h.md#ublockcode) the function call is successful.          [WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error.          [WINDOW_MANAGER_ERRORCODE_DEVICE_NOT_SUPPORTED](capi-oh-window-comm-h.md#windowmanager_errorcode) capability not supported.          [WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. |

### OH_PictureInPicture_SetAutoStartEnabled()

```c
int32_t OH_PictureInPicture_SetAutoStartEnabled(uint32_t controllerId, bool enabled)
```

**Description**

Sets whether to automatically start a PiP window when the user returns to the home screen. By default, no PiP window is started.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t controllerId | ID of the PiP controller. The value is a non-negative integer. |
| bool enabled | Whether to automatically start a PiP window when the user returns to the home screen. **true** to start, **false** otherwise. If the PiP feature under **Settings** > **System** > **Multi-window**<br>is disabled, the PiP window will not be automatically started when the user returns to the home screen even if this parameter is set to **true**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Return the result code. <ul>          <li>[OK](capi-uchar-h.md#ublockcode) the function call is successful. </li>          <li>[WINDOW_MANAGER_ERRORCODE_INCORRECT_PARAM](capi-oh-window-comm-h.md#windowmanager_errorcode) parameter error. Possible cause:              Can not find the PiP controller corresponding to the controllerId ID.</li>          <li>[WINDOW_MANAGER_ERRORCODE_PIP_INTERNAL_ERROR](capi-oh-window-comm-h.md#windowmanager_errorcode) pip internal error. Possible cause:              The PiP controller has been destroyed.</li>          </ul> |


