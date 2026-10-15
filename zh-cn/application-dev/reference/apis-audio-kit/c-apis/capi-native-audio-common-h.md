# native_audio_common.h

## 概述

声明音频公共基础枚举定义， 包括音频错误码、音频场景、铃声模式、录音降噪模式等，在音频播放、音频录制、音频管理相关接口中使用。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioCommon_Result](#oh_audiocommon_result) | OH_AudioCommon_Result | 音频公共错误码枚举定义，用作音频管理接口的返回值。 <br>开发者可通过错误码确定报错类型，采取相应的处理步骤，解决报错场景的功能问题。 |
| [OH_AudioScene](#oh_audioscene) | OH_AudioScene | 音频场景枚举定义。 |
| [OH_AudioRingerMode](#oh_audioringermode) | OH_AudioRingerMode | 铃声模式枚举定义。 |
| [OH_AudioNoiseReductionMode](#oh_audionoisereductionmode) | OH_AudioNoiseReductionMode | 录音降噪模式枚举定义。 |

## 枚举类型说明

### OH_AudioCommon_Result

```c
enum OH_AudioCommon_Result
```

**描述：**

音频公共错误码枚举定义，用作音频管理接口的返回值。 <br>开发者可通过错误码确定报错类型，采取相应的处理步骤，解决报错场景的功能问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIOCOMMON_RESULT_SUCCESS = 0 | 操作成功。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED = 201 | 权限缺失。<br>**起始版本：** 26.0.0 |
| AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101 | 入参错误。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_NO_MEMORY = 6800102 | 内存不足。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE = 6800103 | 非法状态。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED = 6800104 | 操作不支持。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_TIMEOUT = 6800105 | 操作超时。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH = 6800106 | 输入音频数据与所需帧长度不匹配。<br>**起始版本：** 26.0.0 |
| AUDIOCOMMON_RESULT_ERROR_STREAM_LIMIT = 6800201 | 达到系统可支持的最大数量。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301 | 系统通用错误。<br>**起始版本：** 12 |
| AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED = 6800302 | 系统服务进程死亡。<br>**起始版本：** 26.0.1 |
| AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET = 6800501 | 网络条件不满足接口要求。<br>**起始版本：** 26.0.1 |
| AUDIOCOMMON_RESULT_ERROR_STORAGE_NOT_ENOUGH = 6800502 | 设备存储空间不足。<br>**起始版本：** 26.0.1 |

### OH_AudioScene

```c
enum OH_AudioScene
```

**描述：**

音频场景枚举定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SCENE_DEFAULT = 0 |  |
| AUDIO_SCENE_RINGING = 1 |  |
| AUDIO_SCENE_PHONE_CALL = 2 |  |
| AUDIO_SCENE_VOICE_CHAT = 3 |  |

### OH_AudioRingerMode

```c
enum OH_AudioRingerMode
```

**描述：**

铃声模式枚举定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_RINGER_MODE_SILENT = 0 |  |
| AUDIO_RINGER_MODE_VIBRATE = 1 |  |
| AUDIO_RINGER_MODE_NORMAL = 2 |  |

### OH_AudioNoiseReductionMode

```c
enum OH_AudioNoiseReductionMode
```

**描述：**

录音降噪模式枚举定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_NOISE_REDUCTION_MODE_FIDELITY = 0 | 保真模式，不进行降噪。<br>**起始版本：** 26.0.0 |
| AUDIO_NOISE_REDUCTION_MODE_PURE_VOCALS = 1 | 纯人声模式，强降噪，显著抑制周边环境声音。<br>**起始版本：** 26.0.0 |
| AUDIO_NOISE_REDUCTION_MODE_STANDARD = 2 | 标准模式，弱降噪，适当抑制周边环境声音。<br>**起始版本：** 26.0.0 |


