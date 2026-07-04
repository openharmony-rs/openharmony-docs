# OH_AudioEncInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioEncInfo {...} OH_AudioEncInfo
```

## 概述

音频编码信息。

用于配置屏幕录制场景下的音频编码参数，包括音频编码比特率和音频编码格式，支持的编码格式详见[OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat)枚举定义。

OH_AudioEncInfo用于配置屏幕录制时的音频编码参数，支持设置音频编码比特率和编码格式，适用于需要在屏幕录制场景中指定音频编码质量和编码方式的场景。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t audioBitrate | 音频编码比特率，用于设置音频编码的输出比特率。取值范围需参考具体编码格式支持的比特率范围，常见取值有48000、96000和128000。单位为比特每秒（bit/s）。超出编码格式支持范围时可能导致编码失败。 |
| [OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat) audioCodecFormat | 音频编码格式，用于指定屏幕录制时音频数据所采用的编码格式。支持的编码格式详见[OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat)枚举定义。 |


