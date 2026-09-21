# WindowManager_MainWindowInfo

```c
typedef struct WindowManager_MainWindowInfo {...} WindowManager_MainWindowInfo
```

## Overview

The struct describes the main window information.

**System capability**: SystemCapability.Window.SessionManager

**Since**: 21

**Related module**: [WindowManager](capi-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t displayId | ID of the display to which the main window belongs. |
| int32_t windowId | Window ID. The default value is **0**, and the value is an integer. |
| bool showing | Foreground/Background status of the main window. **true** if the main window is in the foreground, **false**<br>otherwise. |
| const char* label | Pointer to the task name of the main window. |


