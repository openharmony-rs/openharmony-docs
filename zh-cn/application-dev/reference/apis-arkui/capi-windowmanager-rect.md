# WindowManager_Rect
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

定义窗口矩形结构体，包含窗口位置和宽高信息。

**起始版本：** 15

**相关模块：** [WindowManager](capi-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t posX | 窗口的x轴，单位为px，该参数为整数。 |
| int32_t posY | 窗口的y轴，单位为px，该参数为整数。 |
| uint32_t width | 窗口的宽度，单位为px，该参数为整数。 |
| uint32_t height | 窗口的高度，单位为px，该参数为整数。 |


