# WindowManager
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

提供应用窗口的管理能力。

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_window.h](capi-oh-window-h.md) | 定义窗口管理的相关接口，主要用于设置和获取指定窗口的属性，以及设置指定窗口的状态栏样式、导航栏样式。 |
| [oh_window_comm.h](capi-oh-window-comm-h.md) | 提供窗口的公共枚举、公共定义等。 |
| [oh_window_event_filter.h](capi-oh-window-event-filter-h.md) | 定义窗口管理按键事件过滤的接口，当多模输入的事件经过窗口时，可以通过过滤接口拦截事件不让事件往下分发。 |
| [oh_window_pip.h](capi-oh-window-pip-h.md) | 定义画中画功能的相关接口，包含创建、删除画中画控制器，以及启动、停止画中画等。主要用于视频播放、直播、视频通话或视频会议场景下，以小窗（画中画）模式呈现内容。 |
