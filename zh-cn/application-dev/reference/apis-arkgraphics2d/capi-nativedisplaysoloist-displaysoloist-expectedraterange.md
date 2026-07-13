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

提供期望帧率范围结构体。

**起始版本：** 12

**相关模块：** [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

**所在头文件：** [native_display_soloist.h](capi-native-display-soloist-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t min | 期望帧率范围最小值，取值范围为[0,120]。 |
| int32_t max | 期望帧率范围最大值，取值范围为[0,120]。 |
| int32_t expected | 期望帧率，取值范围为[0,120]。 |


