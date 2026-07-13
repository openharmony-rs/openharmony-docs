# NativeDisplayManager_DisplaysInfo

```c
typedef struct NativeDisplayManager_DisplaysInfo {...} NativeDisplayManager_DisplaysInfo
```

## 概述

The struct describes the information about displays of a device with multiple screens.

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t displaysLength | Number of displays of a device with multiple screens. |
| [NativeDisplayManager_DisplayInfo](capi-oh-displaymanager-nativedisplaymanager-displayinfo.md) *displaysInfo | An array of NativeDisplayManager_DisplayInfo structs, each containing information about a display. |


