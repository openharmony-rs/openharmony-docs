# WindowManager

## 概述

Provides abilities of windowManager on the native side, such as picture in picture window.

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_window_pip.h](capi-oh-window-pip-h.md) | 定义画中画功能的相关接口，包含创建、删除画中画控制器，以及启动、停止画中画等。主要用于视频播放、直播、视频通话或视频会议场景下，以小窗（画中画）模式呈现内容。 |
| [oh_window.h](capi-oh-window-h.md) | The file declares the window management APIs. You can use the APIs to set and obtain the properties of awindow, and set its status bar style and navigation bar style. |
| [oh_window_event_filter.h](capi-oh-window-event-filter-h.md) | The file declares the APIs for a window to filter multimodal key events. When a multimodal input event passesthrough the window, the window can interrupt the event to prevent it from being further distributed. |
| [oh_window_comm.h](capi-oh-window-comm-h.md) | The file declares the common enums and definitions of the window manager. |
