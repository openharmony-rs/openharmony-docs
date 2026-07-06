# OH_AudioCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioCaptureInfo {...} OH_AudioCaptureInfo
```

## 概述

音频采样信息。

用于配置屏幕录制中的音频采集参数，包括采样率、声道数和音频源类型，适用于需要指定音频采集参数的场景。

当audioSampleRate和audioChannels同时为0时，忽略该类型音频相关参数，不录制该类型音频数据。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t audioSampleRate | 音频采样率，支持列表请查阅Audio Kit的[AudioSamplingRate](../apis-audio-kit/arkts-apis-audio-e.md#audiosamplingrate8)。单位为赫兹（Hz）。 |
| int32_t audioChannels | 音频声道数。取值范围为1或2，1表示单声道，2表示双声道。 |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) audioSource | 音频源，用于指定录制的音频来源，可选值请参考[OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype)。 |


