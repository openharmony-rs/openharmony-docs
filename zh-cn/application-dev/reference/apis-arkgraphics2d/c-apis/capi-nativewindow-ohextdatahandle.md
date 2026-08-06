# OHExtDataHandle

```c
typedef struct OHExtDataHandle {...} OHExtDataHandle
```

## 概述

Defines the ExtData Handle

**起始版本：** 9

**废弃版本：** 10

**相关模块：** [NativeWindow](capi-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t fd | < Handle fd, -1 if not supported |
| uint32_t reserveInts | < the number of reserved integer value |
| int32_t reserve[0] | < the reserved data |


