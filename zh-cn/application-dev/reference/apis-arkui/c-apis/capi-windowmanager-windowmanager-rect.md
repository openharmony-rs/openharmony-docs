# WindowManager_Rect

```c
typedef struct WindowManager_Rect {...} WindowManager_Rect
```

## 概述

定义窗口矩形结构体，包含窗口位置和宽高信息。

<!--Device-typedef struct WindowManager_Rect {...} WindowManager_Rect--><!--Device-typedef struct WindowManager_Rect {...} WindowManager_Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 15

**相关模块：** [WindowManager](capi-arkui-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t posX | 窗口的x坐标，单位为px，该参数为整数。<br><!--Device-int32_t posX--><!--Device-int32_t posX-End--> |
| int32_t posY | 窗口的y坐标，单位为px，该参数为整数。<br><!--Device-int32_t posY--><!--Device-int32_t posY-End--> |
| uint32_t width | 窗口的宽度，单位为px，该参数为整数。<br><!--Device-uint32_t width--><!--Device-uint32_t width-End--> |
| uint32_t height | 窗口的高度，单位为px，该参数为整数。<br><!--Device-uint32_t height--><!--Device-uint32_t height-End--> |


