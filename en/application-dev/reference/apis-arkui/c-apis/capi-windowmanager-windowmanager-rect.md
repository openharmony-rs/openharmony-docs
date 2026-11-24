# WindowManager_Rect

```c
typedef struct WindowManager_Rect {...} WindowManager_Rect
```

## Overview

The struct describes the window rectangle, including the window position, width, and height.

<!--Device-typedef struct WindowManager_Rect {...} WindowManager_Rect--><!--Device-typedef struct WindowManager_Rect {...} WindowManager_Rect-End-->

**System capability**: SystemCapability.Window.SessionManager

**Since**: 15

**Related module**: [WindowManager](capi-arkui-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t posX | X coordinate of the window, in px. The value is an integer.<br><!--Device-int32_t posX--><!--Device-int32_t posX-End--> |
| int32_t posY | Y coordinate of the window, in px. The value is an integer.<br><!--Device-int32_t posY--><!--Device-int32_t posY-End--> |
| uint32_t width | Window width, in px. The value is an integer.<br><!--Device-uint32_t width--><!--Device-uint32_t width-End--> |
| uint32_t height | Window height, in px. The value is an integer.<br><!--Device-uint32_t height--><!--Device-uint32_t height-End--> |


