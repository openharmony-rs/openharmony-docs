# DisplaySoloist_ExpectedRateRange
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @wh_qwe-->
<!--Designer: @wh_qwe-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} DisplaySoloist_ExpectedRateRange
```

## 概述

期望帧率范围结构体，用于设置DisplaySoloist（可变帧率独立线程绘制）的期望帧率范围。设置的期望帧率范围将作为系统调度的参考，系统会尽量在此范围内调整绘制帧率。

**起始版本：** 12

**相关模块：** [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

**所在头文件：** [native_display_soloist.h](capi-native-display-soloist-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t min | 期望的最小帧率，单位为帧/秒（fps），取值范围为[0, 设备支持的最大刷新率]。 |
| int32_t max | 期望的最大帧率，单位为帧/秒（fps），取值范围为[min, 设备支持的最大刷新率]。 |
| int32_t expected | 期望的目标帧率，单位为帧/秒（fps），取值范围为[min, max]。 |
