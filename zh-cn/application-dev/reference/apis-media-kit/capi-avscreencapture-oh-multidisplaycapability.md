# OH_MultiDisplayCapability
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_MultiDisplayCapability {...} OH_MultiDisplayCapability
```

## 概述

多屏幕录制能力信息。多屏场景下，用户选择的多屏幕是否支持联合录制，以及联合录制的屏幕宽度和高度。

**起始版本：** 24

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool isMultiDisplaySupport | 是否支持多屏幕录制，true表示支持多屏幕录制，false表示不支持多屏幕录制。 |
| uint32_t width | 支持录制的屏幕区域宽度（单位：像素）。 |
| uint32_t height | 支持录制的屏幕区域高度（单位：像素）。 |