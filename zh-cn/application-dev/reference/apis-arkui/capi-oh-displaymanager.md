# OH_DisplayManager
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

提供屏幕管理能力，包括获取显示设备的信息、获取屏幕截屏以及监听显示设备的旋转、折叠或展开等状态变化。开发者可通过该模块查询屏幕属性，响应屏幕状态变化事件，实现屏幕适配和多屏幕场景支持。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [oh_display_capture.h](capi-oh-display-capture-h.md) | 提供屏幕截屏的能力。 |
| [oh_display_info.h](capi-oh-display-info-h.md) | 提供屏幕的公共枚举、公共定义等。 |
| [oh_display_manager.h](capi-oh-display-manager-h.md) | 提供屏幕管理的基础能力，包括获取默认显示设备的信息（如屏幕宽度、高度、旋转角度、刷新率或像素密度等），以及监听显示设备的旋转、折叠或展开等状态变化的能力。适用于需要适配不同屏幕形态、响应屏幕状态变化和获取屏幕详细属性信息的场景。 |
