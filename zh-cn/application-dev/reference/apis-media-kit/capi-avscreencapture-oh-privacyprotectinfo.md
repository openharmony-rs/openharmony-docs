# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_PrivacyProtectInfo {...} OH_PrivacyProtectInfo
```

## 概述

隐私保护信息结构体。

用于在屏幕录制场景中对系统窗口和敏感应用进行隐私保护。systemWindowProtection控制系统窗口级别的隐私保护，sensitiveAppProtection控制敏感应用级别的隐私保护，两者都适用于需要在屏幕录制时保护用户隐私数据的场景。

**起始版本：** 24

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool systemWindowProtection | 是否开启系统窗口隐私保护。true表示开启隐私保护，false表示关闭隐私保护，默认值为true。系统窗口是指系统级应用（如输入法、通知等）的窗口。<br>**起始版本：** 24 |
| bool sensitiveAppProtection | 是否开启敏感应用的隐私保护。true表示开启隐私保护，false表示关闭隐私保护，默认值为true。敏感应用（如金融类应用）是指包含用户隐私数据的应用。<br>**起始版本：** 24 |
