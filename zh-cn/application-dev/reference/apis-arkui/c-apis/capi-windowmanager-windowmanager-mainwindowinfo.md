# WindowManager_MainWindowInfo

```c
typedef struct WindowManager_MainWindowInfo {...} WindowManager_MainWindowInfo
```

## 概述

The struct describes the main window information.

**起始版本：** 21

**相关模块：** [WindowManager](capi-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t displayId | ID of the display to which the main window belongs. |
| int32_t windowId | Window ID. The default value is **0**, and the value is an integer. |
| bool showing | Foreground/Background status of the main window. **true** if the main window is in the foreground, **falseotherwise. |
| const char* label | Pointer to the task name of the main window. |


