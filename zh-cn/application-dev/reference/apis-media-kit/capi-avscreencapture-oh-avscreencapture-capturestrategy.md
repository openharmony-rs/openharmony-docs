# OH_AVScreenCapture_CaptureStrategy
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AVScreenCapture_CaptureStrategy OH_AVScreenCapture_CaptureStrategy
```

## 概述

通过OH_AVScreenCapture_CaptureStrategy设置录屏策略。

录屏策略需在录屏启动之前通过OH_AVScreenCapture_SetCaptureStrategy接口设置，录屏启动后设置将不生效。

支持开发者根据业务需求灵活配置录屏捕获行为，适用于需要定制录屏策略的场景，可提升录屏功能的适用性和可控性。

**起始版本：** 20

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

