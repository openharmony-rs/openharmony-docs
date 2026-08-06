# WindowManager_WindowSnapshotConfig

```c
typedef struct WindowManager_WindowSnapshotConfig {...} WindowManager_WindowSnapshotConfig
```

## 概述

Describes the configuration of the main window screenshot.

**起始版本：** 21

**相关模块：** [WindowManager](capi-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool useCache | Whether the existing screenshot of the main window should be used. The default value is **true**. When it is setto **true**, the system uses the existing screenshot of the main window, or captures the latest screenshot if noexisting screenshot is saved. When it is set to **false**, the system captures the latest screenshot of the mainwindow. |


