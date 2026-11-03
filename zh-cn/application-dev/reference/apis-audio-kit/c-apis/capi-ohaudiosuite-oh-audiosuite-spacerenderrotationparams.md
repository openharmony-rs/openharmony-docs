# OH_AudioSuite_SpaceRenderRotationParams

```c
struct OH_AudioSuite_SpaceRenderRotationParams {...}
```

## 概述

定义空间渲染效果节点旋转模式配置参数。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 23

**相关模块：** [OHAudioSuite](capi-others-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | 空间中的X坐标。取值范围为[-5.0, 5.0]，单位为米。<br>**起始版本：** 23 |
| float y | 空间中的Y坐标。取值范围为[-5.0, 5.0]，单位为米。<br>**起始版本：** 23 |
| float z | 空间中的Z坐标。取值范围为[-5.0, 5.0]，单位为米。<br>**起始版本：** 23 |
| int32_t surroundTime | 单周环绕时间。取值范围为[2, 40]，单位为秒。<br>**起始版本：** 23 |
| [OH_AudioSuite_SurroundDirection](capi-native-audio-suite-base-h.md#oh_audiosuite_surrounddirection) surroundDirection | 环绕方向。0表示逆时针旋转，1表示顺时针旋转。<br>**起始版本：** 23 |


