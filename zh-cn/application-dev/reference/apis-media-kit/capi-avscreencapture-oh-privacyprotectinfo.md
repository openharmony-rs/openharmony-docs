# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_PrivacyProtectInfo
```

## 概述

隐私保护信息结构体。

**起始版本：** 24

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool systemWindowProtection | 是否开启系统窗口隐私保护。true表示开启隐私保护，false表示关闭隐私保护。<br>**起始版本：** 24 |
| bool sensitiveAppProtection | 是否开启敏感应用的隐私保护。true表示开启隐私保护，false表示关闭隐私保护。<br>**起始版本：** 24 |
