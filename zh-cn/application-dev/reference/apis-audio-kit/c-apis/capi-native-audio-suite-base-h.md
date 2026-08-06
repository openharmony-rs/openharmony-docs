# native_audio_suite_base.h

## 概述

声明音频编创相关底层数据结构。

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 22

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) | OH_AudioFormat | 定义音频编创的音频流信息，用于描述基本音频格式。 |
| [OH_AudioSuite_SystemNodeFormat](capi-ohaudiosuite-oh-audiosuite-systemnodeformat.md) | OH_AudioSuite_SystemNodeFormat | 定义音频格式信息结构，用于描述系统节点的基本音频格式。 |
| [OH_AudioDataArray](capi-ohaudiosuite-oh-audiodataarray.md) | OH_AudioDataArray | 定义多路输出渲染接口的输出数据描述。当管线中存在多输出效果节点时，通过多输出渲染接口获取处理过后的音频数据。 |
| [OH_AudioSuite_MetaFrame](capi-ohaudiosuite-oh-audiosuite-metaframe.md) | OH_AudioSuite_MetaFrame | 定义音频元数据帧结构。该结构用于将音频数据和元数据一起传递。 |
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) | OH_EqualizerFrequencyBandGains | 定义音频编创均衡器效果节点配置参数。 |
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md) | OH_AudioSuite_SpaceRenderPositionParams | 定义3D空间渲染效果节点固定摆位模式的配置参数。<br>左手坐标系：伸出左手，用拇指和食指形成一个“L”形。拇指指向右侧，食指向上，其余手指指向前。此时形成了一个3D的左手坐标系。在这个坐标系中，拇指、食指和其他手指分别代表x轴、y轴和z轴的正方向。 |
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md) | OH_AudioSuite_SpaceRenderRotationParams | 定义空间渲染效果节点旋转模式配置参数。 |
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md) | OH_AudioSuite_SpaceRenderExtensionParams | 定义空间渲染效果节点扩展模式配置参数。 |
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md) | OH_AudioSuite_PureVoiceChangeOption | 定义音频编创传统变声选项。 |
| [OH_AudioSuiteEngineStruct](capi-ohaudiosuite-oh-audiosuiteenginestruct.md) | OH_AudioSuiteEngine | 声明音频编创引擎，用来管理音频编创管线。 |
| [OH_AudioSuitePipelineStruct](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md) | OH_AudioSuitePipeline | 声明音频编创管线，用来管理音频编创节点。 |
| [OH_AudioNodeStruct](capi-ohaudiosuite-oh-audionodestruct.md) | OH_AudioNode | 声明音频编创节点，用于描述音频编创节点实例。 |
| [OH_AudioNodeBuilderStruct](capi-ohaudiosuite-oh-audionodebuilderstruct.md) | OH_AudioNodeBuilder | 声明音频编创节点的构造器。用于构建{@link OH_AudioNode}，配置输入/输出节点数据格式，配置输入节点回调接口。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioNode_Type](#oh_audionode_type) | OH_AudioNode_Type | 定义音频编创节点类型。 |
| [OH_AudioSuite_SystemNodeType](#oh_audiosuite_systemnodetype) | OH_AudioSuite_SystemNodeType | 定义音频节点系统类型。 |
| [OH_AudioSuite_PipelineWorkMode](#oh_audiosuite_pipelineworkmode) | OH_AudioSuite_PipelineWorkMode | 定义音频编创管线工作模式。 |
| [OH_AudioSuite_PipelineState](#oh_audiosuite_pipelinestate) | OH_AudioSuite_PipelineState | 定义音频编创管线运行状态。 |
| [OH_AudioSuite_Result](#oh_audiosuite_result) | OH_AudioSuite_Result | 音频编创错误码。 |
| [OH_Audio_SampleFormat](#oh_audio_sampleformat) | OH_Audio_SampleFormat | 定义音频编创节点音频流的位深度。 |
| [OH_Audio_EncodingType](#oh_audio_encodingtype) | OH_Audio_EncodingType | 定义音频流编码类型。 |
| [OH_Audio_SampleRate](#oh_audio_samplerate) | OH_Audio_SampleRate | 定义音频采样率。 |
| [OH_SoundFieldType](#oh_soundfieldtype) | OH_SoundFieldType | 定义音频编创声场效果节点的效果模式。 |
| [OH_EnvironmentType](#oh_environmenttype) | OH_EnvironmentType | 定义音频编创环境效果节点的模式。 |
| [OH_VoiceBeautifierType](#oh_voicebeautifiertype) | OH_VoiceBeautifierType | 定义音频编创美化效果节点模式。 |
| [OH_AudioSuite_SurroundDirection](#oh_audiosuite_surrounddirection) | OH_AudioSuite_SurroundDirection | 定义空间渲染效果节点旋转模式环绕方向。 |
| [OH_AudioSuite_PureVoiceChangeGenderOption](#oh_audiosuite_purevoicechangegenderoption) | OH_AudioSuite_PureVoiceChangeGenderOption | 定义音频编创传统变声效果节点的性别。 |
| [OH_AudioSuite_PureVoiceChangeType](#oh_audiosuite_purevoicechangetype) | OH_AudioSuite_PureVoiceChangeType | 定义音频编创传统变声效果节点的变声类型。 |
| [OH_AudioSuite_GeneralVoiceChangeType](#oh_audiosuite_generalvoicechangetype) | OH_AudioSuite_GeneralVoiceChangeType | 定义音频编创通用变声的节点类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| EQUALIZER_BAND_NUM (10) | 定义均衡器频带数量为10个。<br>**起始版本：** 22 |
| OH_PURE_VOICE_DEFAULT_PITCH (0.0f) |  |

### 变量

| 名称 | 描述 |
| -- | -- |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DEFAULT |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_BALLADS |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CHINESE_STYLE |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CLASSICAL |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DANCE_MUSIC |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_JAZZ |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_POP |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_RB |  |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_ROCK |  |

## 枚举类型说明

### OH_AudioNode_Type

```c
enum OH_AudioNode_Type
```

**描述**

定义音频编创节点类型。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| INPUT_NODE_TYPE_DEFAULT = 1 |  |
| OUTPUT_NODE_TYPE_DEFAULT = 101 |  |
| EFFECT_NODE_TYPE_EQUALIZER = 201 |  |
| EFFECT_NODE_TYPE_NOISE_REDUCTION = 202 |  |
| EFFECT_NODE_TYPE_SOUND_FIELD = 203 |  |
| EFFECT_MULTII_OUTPUT_NODE_TYPE_AUDIO_SEPARATION = 204 |  |
| EFFECT_NODE_TYPE_VOICE_BEAUTIFIER = 205 |  |
| EFFECT_NODE_TYPE_ENVIRONMENT_EFFECT = 206 |  |
| EFFECT_NODE_TYPE_AUDIO_MIXER = 207 |  |
| EFFECT_NODE_TYPE_SPACE_RENDER = 208 |  |
| EFFECT_NODE_TYPE_PURE_VOICE_CHANGE = 209 |  |
| EFFECT_NODE_TYPE_GENERAL_VOICE_CHANGE = 210 |  |
| EFFECT_NODE_TYPE_TEMPO_PITCH = 211 |  |
| EFFECT_NODE_TYPE_HOA_SPACE_RENDER = 212 |  |

### OH_AudioSuite_SystemNodeType

```c
enum OH_AudioSuite_SystemNodeType
```

**描述**

定义音频节点系统类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_DIALOGUE_ENHANCE = 301 |  |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_VOICE_BEAUTIFIER = 302 |  |

### OH_AudioSuite_PipelineWorkMode

```c
enum OH_AudioSuite_PipelineWorkMode
```

**描述**

定义音频编创管线工作模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSUITE_PIPELINE_EDIT_MODE = 1 |  |
| AUDIOSUITE_PIPELINE_REALTIME_MODE = 2 |  |

### OH_AudioSuite_PipelineState

```c
enum OH_AudioSuite_PipelineState
```

**描述**

定义音频编创管线运行状态。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSUITE_PIPELINE_STOPPED = 1 |  |
| AUDIOSUITE_PIPELINE_RUNNING = 2 |  |

### OH_AudioSuite_Result

```c
enum OH_AudioSuite_Result
```

**描述**

音频编创错误码。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSUITE_SUCCESS = 0 | 调用成功。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_INVALID_PARAM = 1 | 输入参数无效。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_INVALID_STATE = 2 | 非法状态。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_SYSTEM = 3 | 系统通用错误。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT = 4 | 不支持的音频格式，如不支持的编码类型、采样格式等。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_ENGINE_NOT_EXIST = 5 | 引擎不存在。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST = 6 | 管线不存在。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_NODE_NOT_EXIST = 7 | 节点不存在。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT = 8 | 节点之间不支持连接。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION = 9 | 不支持的操作。例如，效果节点不支持设置音频格式。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS = 10 | 创建管线或者节点超过系统最大数量限制。具体情况如下：<br> 引擎最多支持创建10条管线（其中，实时预览管线最多创建1条）。<br> 每一个管线中，输出节点的数量不超过1个，混音节点的数量不超过3个，音源分离节点的数量不超过1个。<br> 在API version 24之前，每一个管线中，输入节点的数量不超过5个，其余效果节点的数量不超过5个；在API version 24及以后，每一个管线中，输入节点的数量不超过15个，其余效果节点的数量不超过15个。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING = 11 | 参数缺少必要参数。例如，输入节点未设置回调函数、输出节点未设置音频格式。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_TIMEOUT = 12 | 操作超时。<br>**起始版本：** 22 |
| AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED = 13 | 内存申请失败。<br>**起始版本：** 22 |

### OH_Audio_SampleFormat

```c
enum OH_Audio_SampleFormat
```

**描述**

定义音频编创节点音频流的位深度。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SAMPLE_U8 = 0 |  |
| AUDIO_SAMPLE_S16LE = 1 |  |
| AUDIO_SAMPLE_S24LE = 2 |  |
| AUDIO_SAMPLE_S32LE = 3 |  |
| AUDIO_SAMPLE_F32LE = 4 |  |

### OH_Audio_EncodingType

```c
enum OH_Audio_EncodingType
```

**描述**

定义音频流编码类型。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_ENCODING_TYPE_RAW = 0 |  |

### OH_Audio_SampleRate

```c
enum OH_Audio_SampleRate
```

**描述**

定义音频采样率。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| SAMPLE_RATE_8000 = 8000 |  |
| SAMPLE_RATE_11025 = 11025 |  |
| SAMPLE_RATE_12000 = 12000 |  |
| SAMPLE_RATE_16000 = 16000 |  |
| SAMPLE_RATE_22050 = 22050 |  |
| SAMPLE_RATE_24000 = 24000 |  |
| SAMPLE_RATE_32000 = 32000 |  |
| SAMPLE_RATE_44100 = 44100 |  |
| SAMPLE_RATE_48000 = 48000 |  |
| SAMPLE_RATE_64000 = 64000 |  |
| SAMPLE_RATE_88200 = 88200 |  |
| SAMPLE_RATE_96000 = 96000 |  |
| SAMPLE_RATE_176400 = 176400 |  |
| SAMPLE_RATE_192000 = 192000 |  |

### OH_SoundFieldType

```c
enum OH_SoundFieldType
```

**描述**

定义音频编创声场效果节点的效果模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| SOUND_FIELD_FRONT_FACING = 1 |  |
| SOUND_FIELD_GRAND = 2 |  |
| SOUND_FIELD_NEAR = 3 |  |
| SOUND_FIELD_WIDE = 4 |  |

### OH_EnvironmentType

```c
enum OH_EnvironmentType
```

**描述**

定义音频编创环境效果节点的模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ENVIRONMENT_TYPE_BROADCAST = 1 |  |
| ENVIRONMENT_TYPE_EARPIECE = 2 |  |
| ENVIRONMENT_TYPE_UNDERWATER = 3 |  |
| ENVIRONMENT_TYPE_GRAMOPHONE = 4 |  |

### OH_VoiceBeautifierType

```c
enum OH_VoiceBeautifierType
```

**描述**

定义音频编创美化效果节点模式。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| VOICE_BEAUTIFIER_TYPE_CLEAR = 1 |  |
| VOICE_BEAUTIFIER_TYPE_THEATRE = 2 |  |
| VOICE_BEAUTIFIER_TYPE_CD = 3 |  |
| VOICE_BEAUTIFIER_TYPE_RECORDING_STUDIO = 4 |  |

### OH_AudioSuite_SurroundDirection

```c
enum OH_AudioSuite_SurroundDirection
```

**描述**

定义空间渲染效果节点旋转模式环绕方向。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| SPACE_RENDER_CCW = 0 |  |
| SPACE_RENDER_CW = 1 |  |

### OH_AudioSuite_PureVoiceChangeGenderOption

```c
enum OH_AudioSuite_PureVoiceChangeGenderOption
```

**描述**

定义音频编创传统变声效果节点的性别。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| PURE_VOICE_CHANGE_FEMALE = 1 |  |
| PURE_VOICE_CHANGE_MALE = 2 |  |

### OH_AudioSuite_PureVoiceChangeType

```c
enum OH_AudioSuite_PureVoiceChangeType
```

**描述**

定义音频编创传统变声效果节点的变声类型。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| PURE_VOICE_CHANGE_TYPE_CARTOON = 1 |  |
| PURE_VOICE_CHANGE_TYPE_CUTE = 2 |  |
| PURE_VOICE_CHANGE_TYPE_FEMALE = 3 |  |
| PURE_VOICE_CHANGE_TYPE_MALE = 4 |  |
| PURE_VOICE_CHANGE_TYPE_MONSTER = 5 |  |
| PURE_VOICE_CHANGE_TYPE_ROBOTS = 6 |  |
| PURE_VOICE_CHANGE_TYPE_SEASONED = 7 |  |

### OH_AudioSuite_GeneralVoiceChangeType

```c
enum OH_AudioSuite_GeneralVoiceChangeType
```

**描述**

定义音频编创通用变声的节点类型。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| GENERAL_VOICE_CHANGE_TYPE_CUTE = 1 |  |
| GENERAL_VOICE_CHANGE_TYPE_CYBERPUNK = 2 |  |
| GENERAL_VOICE_CHANGE_TYPE_FEMALE = 3 |  |
| GENERAL_VOICE_CHANGE_TYPE_MALE = 4 |  |
| GENERAL_VOICE_CHANGE_TYPE_MIX = 5 |  |
| GENERAL_VOICE_CHANGE_TYPE_MONSTER = 6 |  |
| GENERAL_VOICE_CHANGE_TYPE_SEASONED = 7 |  |
| GENERAL_VOICE_CHANGE_TYPE_SYNTH = 8 |  |
| GENERAL_VOICE_CHANGE_TYPE_TRILL = 9 |  |
| GENERAL_VOICE_CHANGE_TYPE_WAR = 10 |  |


