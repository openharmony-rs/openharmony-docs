# OH_AudioObjectPosition
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioObjectPosition {...} OH_AudioObjectPosition
```

## 概述

表示音频对象声源在三维空间中的位置。该位置可以用笛卡尔坐标或极坐标表示。

**起始版本：** 26.0.0

**相关模块：** [Core](capi-core.md)

**所在头文件：** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool isCartesian | 对象声源是否使用笛卡尔坐标表示。<br>true表示使用笛卡尔坐标，false表示不使用笛卡尔坐标系，使用极坐标系。 |
| union {<br>[OH_CartesianPosition](capi-core-oh-cartesianposition.md) cartesian;<br>[OH_PolarPosition](capi-core-oh-polarposition.md) polar; <br>} pos | 包含笛卡尔坐标或极坐标位置数据的联合体。<br>cartesian：笛卡尔坐标表示的位置。<br>polar：极坐标表示的位置。 |


