# OH_AudioSuite_SpaceRenderExtensionParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_AudioSuite_SpaceRenderExtensionParams {...} OH_AudioSuite_SpaceRenderExtensionParams
```

## 概述

定义空间渲染效果节点扩展模式配置参数。

**起始版本：** 23

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float extRadius | 扩展半径，表示声音源的空间扩散范围。取值越大，声音的空间扩散范围越宽广。取值范围为[1.0, 5.0]，单位为米（m）。 |
| int32_t extAngle | 扩展角度，表示声音源在水平面上的扩散角度范围。取值越大，声音的扩散角度越宽。取值范围为(0, 360)，单位为度（°）。 |


