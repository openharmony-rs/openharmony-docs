# OH_AudioObjectPosition

```c
union OH_AudioObjectPosition {...}
```

## 概述

表示音频对象声源在三维空间中的位置。<br> 该位置可以用笛卡尔坐标或极坐标表示。

**系统能力：** SystemCapability.Multimedia.Media.Core

**起始版本：** 26.0.0

**相关模块：** [Core](capi-core.md)

**所在头文件：** [native_audio_vivid.h](capi-native-audio-vivid-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_CartesianPosition](capi-core-oh-cartesianposition.md) cartesian | 笛卡尔坐标表示的位置。<br>**起始版本：** 26.0.0 |
| OH_PolarPosition polar;
 } pos | 极坐标表示的位置。<br>**起始版本：** 26.0.0 |


