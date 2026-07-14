# NativeDisplayManager_DisplayHdrFormat

```c
typedef struct NativeDisplayManager_DisplayHdrFormat {...} NativeDisplayManager_DisplayHdrFormat
```

## 概述

The struct describes all the HDR formats supported by a display.

**起始版本：** 14

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t hdrFormatLength | Number of HDR formats supported by the display. |
| uint32_t *hdrFormats | Data of the HDR formats supported by the display. |


