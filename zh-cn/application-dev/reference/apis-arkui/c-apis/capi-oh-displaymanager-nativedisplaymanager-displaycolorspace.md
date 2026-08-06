# NativeDisplayManager_DisplayColorSpace

```c
typedef struct NativeDisplayManager_DisplayColorSpace {...} NativeDisplayManager_DisplayColorSpace
```

## 概述

The struct describes all the color spaces supported by a display.

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t colorSpaceLength | Number of color spaces supported by the display. |
| uint32_t *colorSpaces | Data of the color spaces supported by the display. |


