# native_audio_suite_base.h

## Overview

Declare underlying data structure.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) | OH_AudioFormat | Define the audio format info structure, used to describe basic audio format. |
| [OH_AudioDataArray](capi-ohaudiosuite-oh-audiodataarray.md) | OH_AudioDataArray | Define the audio data array structure. This structure is used to get the processed audio data after acquisition processing during multi-channel rendering. |
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) | OH_EqualizerFrequencyBandGains | Specify equalizer frequency band gains. |
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md) | OH_AudioSuite_SpaceRenderPositionParams | Definition of the parameter structure for fixed position mode in 3D spatial rendering. Left-hand coordinate system: Extend your left hand, forming an "L" shape with your thumb and index finger. Point the thumb to the right, the index finger upward, and the remaining fingers forward. This establishes a left-hand coordinate system. In this system, the thumb, index finger, and other fingers represent the positive directions of the x, y, and z axes, respectively. |
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md) | OH_AudioSuite_SpaceRenderRotationParams | Space rendering dynamic mode parameters. |
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md) | - | Space rendering extension mode parameters. |
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md) | OH_AudioSuite_PureVoiceChangeOption | Define change voice option. |
| [OH_AudioSuiteEngineStruct](capi-ohaudiosuite-oh-audiosuiteenginestruct.md) | OH_AudioSuiteEngine | Declare the audio engine. The handle of audio suite engine is used for audio suite engine related functions. |
| [OH_AudioSuitePipelineStruct](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md) | OH_AudioSuitePipeline | Declare the audio pipeline. The handle of audio suite pipeline is used for audio pipeline related functions. |
| [OH_AudioNodeStruct](capi-ohaudiosuite-oh-audionodestruct.md) | OH_AudioNode | Declare the audio node. The handle of audio suite node is used for audio suite node related functions. |
| [OH_AudioNodeBuilderStruct](capi-ohaudiosuite-oh-audionodebuilderstruct.md) | OH_AudioNodeBuilder | Declare the audio node builder. The handle of audio node builder is used for audio node create. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioNode_Type](#oh_audionode_type) | OH_AudioNode_Type | Define audio node type. |
| [OH_AudioSuite_PipelineWorkMode](#oh_audiosuite_pipelineworkmode) | OH_AudioSuite_PipelineWorkMode | Define pipeline work mode |
| [OH_AudioSuite_PipelineState](#oh_audiosuite_pipelinestate) | OH_AudioSuite_PipelineState | Define pipeline state |
| [OH_AudioSuite_Result](#oh_audiosuite_result) | OH_AudioSuite_Result | Define the result of the function execution. |
| [OH_Audio_SampleFormat](#oh_audio_sampleformat) | OH_Audio_SampleFormat | Define the audio sample format. |
| [OH_Audio_EncodingType](#oh_audio_encodingtype) | OH_Audio_EncodingType | Define the audio encoding type. |
| [OH_Audio_SampleRate](#oh_audio_samplerate) | OH_Audio_SampleRate | Define the audio sample rate. |
| [OH_SoundFieldType](#oh_soundfieldtype) | OH_SoundFieldType | Define the sound field type. |
| [OH_EnvironmentType](#oh_environmenttype) | OH_EnvironmentType | Define the environment type. |
| [OH_VoiceBeautifierType](#oh_voicebeautifiertype) | OH_VoiceBeautifierType | Define voice beautifier type. |
| [OH_AudioSuite_SurroundDirection](#oh_audiosuite_surrounddirection) | OH_AudioSuite_SurroundDirection | Space rendering surround Direction |
| [OH_AudioSuite_PureVoiceChangeGenderOption](#oh_audiosuite_purevoicechangegenderoption) | OH_AudioSuite_PureVoiceChangeGenderOption | Define speaker gender in change voice option |
| [OH_AudioSuite_PureVoiceChangeType](#oh_audiosuite_purevoicechangetype) | OH_AudioSuite_PureVoiceChangeType | Define voice type in change voice option |
| [OH_AudioSuite_GeneralVoiceChangeType](#oh_audiosuite_generalvoicechangetype) | OH_AudioSuite_GeneralVoiceChangeType | Define voice type in general voice change. |

### Macro

| Name | Description |
| -- | -- |
| EQUALIZER_BAND_NUM (10) | Define the number of equalizer frequency bands<br>**Since**: 22 |
| OH_PURE_VOICE_DEFAULT_PITCH (0.0f) |  |

### Variable

| Name | Description |
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

## Enum type description

### OH_AudioNode_Type

```c
enum OH_AudioNode_Type
```

**Description**

Define audio node type.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
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

### OH_AudioSuite_PipelineWorkMode

```c
enum OH_AudioSuite_PipelineWorkMode
```

**Description**

Define pipeline work mode

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| AUDIOSUITE_PIPELINE_EDIT_MODE = 1 |  |
| AUDIOSUITE_PIPELINE_REALTIME_MODE = 2 |  |

### OH_AudioSuite_PipelineState

```c
enum OH_AudioSuite_PipelineState
```

**Description**

Define pipeline state

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| AUDIOSUITE_PIPELINE_STOPPED = 1 |  |
| AUDIOSUITE_PIPELINE_RUNNING = 2 |  |

### OH_AudioSuite_Result

```c
enum OH_AudioSuite_Result
```

**Description**

Define the result of the function execution.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| AUDIOSUITE_SUCCESS = 0 |  The call was successful.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_INVALID_PARAM = 1 |  This means that the function was executed with an invalid input parameter.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_INVALID_STATE = 2 |  Execution status exception.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_SYSTEM = 3 |  A system error has occurred.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT = 4 |  Unsupported audio format, such as unsupported encoding type, sample format etc.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_ENGINE_NOT_EXIST = 5 |  audio engine does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST = 6 |  audio pipeline does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_NODE_NOT_EXIST = 7 |  audio node does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT = 8 |  the connect or disconnect between the nodes is unsupported.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION = 9 |  Unsupported operation.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS = 10 |  The application attempted to create an object that exceeds the system's maximum limit.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING = 11 |  Required parameters are missing.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_TIMEOUT = 12 |  Operation timed out.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED = 13 |  Memory allocation failed.<br>**Since**: 22 |

### OH_Audio_SampleFormat

```c
enum OH_Audio_SampleFormat
```

**Description**

Define the audio sample format.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
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

**Description**

Define the audio encoding type.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| AUDIO_ENCODING_TYPE_RAW = 0 |  |

### OH_Audio_SampleRate

```c
enum OH_Audio_SampleRate
```

**Description**

Define the audio sample rate.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
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

**Description**

Define the sound field type.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| SOUND_FIELD_FRONT_FACING = 1 |  |
| SOUND_FIELD_GRAND = 2 |  |
| SOUND_FIELD_NEAR = 3 |  |
| SOUND_FIELD_WIDE = 4 |  |

### OH_EnvironmentType

```c
enum OH_EnvironmentType
```

**Description**

Define the environment type.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| ENVIRONMENT_TYPE_BROADCAST = 1 |  |
| ENVIRONMENT_TYPE_EARPIECE = 2 |  |
| ENVIRONMENT_TYPE_UNDERWATER = 3 |  |
| ENVIRONMENT_TYPE_GRAMOPHONE = 4 |  |

### OH_VoiceBeautifierType

```c
enum OH_VoiceBeautifierType
```

**Description**

Define voice beautifier type.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

| Enum item | Description |
| -- | -- |
| VOICE_BEAUTIFIER_TYPE_CLEAR = 1 |  |
| VOICE_BEAUTIFIER_TYPE_THEATRE = 2 |  |
| VOICE_BEAUTIFIER_TYPE_CD = 3 |  |
| VOICE_BEAUTIFIER_TYPE_RECORDING_STUDIO = 4 |  |

### OH_AudioSuite_SurroundDirection

```c
enum OH_AudioSuite_SurroundDirection
```

**Description**

Space rendering surround Direction

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

| Enum item | Description |
| -- | -- |
| SPACE_RENDER_CCW = 0 |  |
| SPACE_RENDER_CW = 1 |  |

### OH_AudioSuite_PureVoiceChangeGenderOption

```c
enum OH_AudioSuite_PureVoiceChangeGenderOption
```

**Description**

Define speaker gender in change voice option

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

| Enum item | Description |
| -- | -- |
| PURE_VOICE_CHANGE_FEMALE = 1 |  |
| PURE_VOICE_CHANGE_MALE = 2 |  |

### OH_AudioSuite_PureVoiceChangeType

```c
enum OH_AudioSuite_PureVoiceChangeType
```

**Description**

Define voice type in change voice option

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

| Enum item | Description |
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

**Description**

Define voice type in general voice change.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

| Enum item | Description |
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


