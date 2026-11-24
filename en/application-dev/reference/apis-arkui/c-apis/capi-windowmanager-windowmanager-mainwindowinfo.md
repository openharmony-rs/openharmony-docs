# WindowManager_MainWindowInfo

```c
typedef struct WindowManager_MainWindowInfo {...} WindowManager_MainWindowInfo
```

## Overview

The struct describes the main window information.

<!--Device-typedef struct WindowManager_MainWindowInfo {...} WindowManager_MainWindowInfo--><!--Device-typedef struct WindowManager_MainWindowInfo {...} WindowManager_MainWindowInfo-End-->

**System capability**: SystemCapability.Window.SessionManager

**Since**: 21

**Related module**: [WindowManager](capi-arkui-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t displayId | ID of the display to which the main window belongs.<br><!--Device-uint64_t displayId--><!--Device-uint64_t displayId-End--> |
| int32_t windowId | Window ID. The default value is **0**, and the value is an integer.<br><!--Device-int32_t windowId--><!--Device-int32_t windowId-End--> |
| bool showing | Foreground/Background status of the main window. **true** if the main window is in the foreground, **false** otherwise.<br><!--Device-bool showing--><!--Device-bool showing-End--> |
| const char* label | Pointer to the task name of the main window.<br><!--Device-const char* label--><!--Device-const char* label-End--> |


