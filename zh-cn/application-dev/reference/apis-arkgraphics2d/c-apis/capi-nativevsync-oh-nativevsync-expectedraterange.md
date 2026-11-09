# OH_NativeVSync_ExpectedRateRange

```c
typedef struct OH_NativeVSync_ExpectedRateRange {...} OH_NativeVSync_ExpectedRateRange
```

## 概述

期望帧率范围结构体。

<!--Device-typedef struct OH_NativeVSync_ExpectedRateRange {...} OH_NativeVSync_ExpectedRateRange--><!--Device-typedef struct OH_NativeVSync_ExpectedRateRange {...} OH_NativeVSync_ExpectedRateRange-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 20

**相关模块：** [NativeVsync](capi-arkgraphics2d-nativevsync.md)

**所在头文件：** [native_vsync.h](capi-native-vsync-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t min | 帧率范围的最小帧率。 |
| int32_t max | 帧率范围的最大帧率。 |
| int32_t expected | 帧率范围的期望帧率。 |


