# WindowManager_MainWindowInfo

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

```
typedef struct {...} WindowManager_MainWindowInfo
```

## 概述

主窗口信息。

**起始版本：** 21

**相关模块：** [WindowManager](capi-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t displayId | 主窗口所在的屏幕ID。 |
| int32_t windowId | 主窗口ID。 |
| bool showing | 主窗口的前后台状态。true表示主窗口在前台，false表示主窗口不在前台。 |
| const char* label | 主窗口任务名称。 |