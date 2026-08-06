# WindowManager_Rect

```c
typedef struct WindowManager_Rect {...} WindowManager_Rect
```

## 概述

The struct describes the window rectangle, including the window position, width, and height.

**起始版本：** 15

**相关模块：** [WindowManager](capi-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t posX | X coordinate of the window, in px. The value is an integer. |
| int32_t posY | Y coordinate of the window, in px. The value is an integer. |
| uint32_t width | Window width, in px. The value is an integer. |
| uint32_t height | Window height, in px. The value is an integer. |


