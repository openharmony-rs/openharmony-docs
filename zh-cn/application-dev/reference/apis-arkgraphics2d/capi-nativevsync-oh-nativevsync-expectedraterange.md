# OH_NativeVSync_ExpectedRateRange
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hudi33-->
<!--Designer: @hudi33-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} OH_NativeVSync_ExpectedRateRange
```

## 概述

期望帧率范围结构体。

**起始版本：** 20

**相关模块：** [NativeVsync](capi-nativevsync.md)

**所在头文件：** [native_vsync.h](capi-native-vsync-h.md)

## 汇总

### 成员变量

| 名称             | 描述                 |
| ---------------- | -------------------- |
| int32_t min      | 帧率范围的最小帧率。 |
| int32_t max      | 帧率范围的最大帧率。 |
| int32_t expected | 帧率范围的期望帧率。 |


### 成员函数

| 名称                                                         | typedef关键字                  | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------ |
| [typedef void (\*OH_NativeVSync_FrameCallback)(long long timestamp, void *data)](#oh_nativevsync_framecallback) | OH_NativeVSync_FrameCallback() | VSync回调函数类型。<br>**起始版本：** 9<br>**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync |


