# OH_CartesianPosition
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_CartesianPosition {...} OH_CartesianPosition
```

## 概述

表示对象声源在笛卡尔坐标系（Cartesian coordinate system）中的位置。笛卡尔坐标系使用x、y、z轴定义三维空间中的位置。

**起始版本：** 26.0.0

**相关模块：** [Core](capi-core.md)

**所在头文件：** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | 对象声源在笛卡尔坐标系中的归一化（Normalization，将数值按比例转换到指定范围内）X坐标，表示左/右维度。<br> 取值范围为[-1.0, 1.0]。 |
| float y | 对象声源在笛卡尔坐标系中的归一化Y坐标，表示前/后维度。<br> 取值范围为[-1.0, 1.0]。 |
| float z | 对象声源在笛卡尔坐标系中的归一化Z坐标，表示上/下维度。<br> 取值范围为[-1.0, 1.0]。 |
