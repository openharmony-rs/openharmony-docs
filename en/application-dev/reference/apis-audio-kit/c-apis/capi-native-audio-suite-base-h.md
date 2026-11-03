# native_audio_suite_base.h

## Overview

Declare underlying data structure.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) | - | Define the audio format info structure, used to describe basic audio format. |
| [OH_AudioDataArray](capi-ohaudiosuite-oh-audiodataarray.md) | - | Define the audio data array structure. This structure is used to get the processed audio data after acquisition processing during multi-channel rendering. |
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) | - | Specify equalizer frequency band gains. |
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md) | - | Definition of the parameter structure for fixed position mode in 3D spatial rendering. Left-hand coordinate system: Extend your left hand, forming an "L" shape with your thumb and index finger. Point the thumb to the right, the index finger upward, and the remaining fingers forward. This establishes a left-hand coordinate system. In this system, the thumb, index finger, and other fingers represent the positive directions of the x, y, and z axes, respectively. |
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md) | - | Space rendering dynamic mode parameters. |
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md) | - | Space rendering extension mode parameters. |
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md) | - | Define change voice option. |
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
| OH_PURE_VOICE_DEFAULT_PITCH (0.0f) | Use system recommended pitch. Use in [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md).<br>**Since**: 23 |

### Variable

| Name | Description |
| -- | -- |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DEFAULT | Default equalization effect band gains. Gains is {0, 0, 0, 0, 0, 0, 0, 0, 0, 0}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_BALLADS | Ballad equalization effect band gains. Gains is {3, 5, 2, -4, 1, 2, -3, 1, 4, 5}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CHINESE_STYLE | Chinese style equalization effect band gains. Gains is {0, 0, 2, 0, 0, 4, 4, 2, 2, 5}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CLASSICAL | Classic equalization effect band gains. Gains is {2, 3, 2, 1, 0, 0, -5, -5, -5, -6}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DANCE_MUSIC | Dance music equalization effect band gains. Gains is {4, 3, 2, -3, 0, 0, 5, 4, 2, 0}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_JAZZ | Jazz equalization effect band gains. Gains is {2, 0, 2, 3, 6, 5, -1, 3, 4, 4}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_POP | Pop equalization effect band gains. Gains is {5, 2, 1, -1, -5, -5, -2, 1, 2, 4}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_RB | R&B equalization effect band gains. Gains is {1, 4, 5, 3, -2, -2, 2, 3, 5, 5}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_ROCK | Rock equalization effect band gains. Gains is {6, 4, 4, 2, 0, 1, 3, 3, 5, 4}.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |

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
| INPUT_NODE_TYPE_DEFAULT = 1 | default input node type, this input node type supports getting audio data from application.<br>**Since**: 22 |
| OUTPUT_NODE_TYPE_DEFAULT = 101 | default output node type, this output node type supports providing audio data to the application.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_EQUALIZER = 201 | Equalization node type. The audio format output by the equalizer node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_NOISE_REDUCTION = 202 | Noise reduction node type. The audio format output by the noise reduction node is as follows: Sample rate: 16000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 1.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_SOUND_FIELD = 203 | Sound field node type. Support sound field type [OH_SoundFieldType](capi-native-audio-suite-base-h.md#oh_soundfieldtype). The audio format output by the sound field node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 22 |
| EFFECT_MULTII_OUTPUT_NODE_TYPE_AUDIO_SEPARATION = 204 | Audio separation node type, it can only connect to output node. The audio format output by the audio separation node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_F32LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 4 (First 2 channels for vocals; last 2 channels for accompaniment).<br>**Since**: 22 |
| EFFECT_NODE_TYPE_VOICE_BEAUTIFIER = 205 | Voice beautifier node type. Supports beautifier type [OH_VoiceBeautifierType](capi-native-audio-suite-base-h.md#oh_voicebeautifiertype). The audio format output by the voice beautifier node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_ENVIRONMENT_EFFECT = 206 | Scene effect node type. The audio format output by the environment node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_AUDIO_MIXER = 207 | Audio mixer node type. The audio format output by the mixer node is as follows: Sample rate: [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate). Sample format: [AUDIO_SAMPLE_F32LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 22 |
| EFFECT_NODE_TYPE_SPACE_RENDER = 208 | Space render node type. The audio format output by the space render node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 23 |
| EFFECT_NODE_TYPE_PURE_VOICE_CHANGE = 209 | Pure voice change node type. The audio format output by the pure voice change node is as follows: Sample rate: 16000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 1.<br>**Since**: 23 |
| EFFECT_NODE_TYPE_GENERAL_VOICE_CHANGE = 210 | General voice change node type. The audio format output by the general voice change node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2.<br>**Since**: 23 |
| EFFECT_NODE_TYPE_TEMPO_PITCH = 211 | Tempo and pitch node type. The audio format output by the tempo and pitch node is as follows: Sample rate: 48000 Hz. Sample format: [AUDIO_SAMPLE_S16LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 1.<br>**Since**: 23 |
| EFFECT_NODE_TYPE_HOA_SPACE_RENDER = 212 | HOA input space render node type. The audio format input by the HOA space render node is as follows: Sample rate: [SAMPLE_RATE_16000](capi-native-audio-suite-base-h.md#oh_audio_samplerate), [SAMPLE_RATE_48000](capi-native-audio-suite-base-h.md#oh_audio_samplerate). Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). layout: 1st to 3rd order HOA, as one of the follows: [CH_LAYOUT_AMB_ORDER1_ACN_N3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER1_ACN_SN3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER1_FUMA](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER2_ACN_N3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER2_ACN_SN3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER2_FUMA](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER3_ACN_N3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER3_ACN_SN3D](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout), [CH_LAYOUT_AMB_ORDER3_FUMA](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout). The audio format output by the HOA space render node is as follows: Sample rate: [SAMPLE_RATE_48000](capi-native-audio-suite-base-h.md#oh_audio_samplerate). Sample format: [AUDIO_SAMPLE_S32LE](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Channels: 2. This node must be connected to an input node with the audio format set to HOA. If it is not connected, an error will be reported in the [OH_AudioSuiteEngine_StartPipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_startpipeline) interface.<br>**Since**: 26.0.0 |

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
| AUDIOSUITE_PIPELINE_EDIT_MODE = 1 | The pipeline supports creating various effect nodes in suite mode.<br>**Since**: 22 |
| AUDIOSUITE_PIPELINE_REALTIME_MODE = 2 | If you need to play audio after effect processing, you should select this mode. Before API version 23, in real-time rendering mode, the pipeline only supports EQ effect processing. In API version 23 and later, in real-time rendering mode, the pipeline supports all effect processing.<br>**Since**: 22 |

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
| AUDIOSUITE_PIPELINE_STOPPED = 1 | The pipeline is in a stopped state.<br>**Since**: 22 |
| AUDIOSUITE_PIPELINE_RUNNING = 2 | The pipeline is in a running state.<br>**Since**: 22 |

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
| AUDIOSUITE_SUCCESS = 0 | &nbsp;The call was successful.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_INVALID_PARAM = 1 | &nbsp;This means that the function was executed with an invalid input parameter.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_INVALID_STATE = 2 | &nbsp;Execution status exception.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_SYSTEM = 3 | &nbsp;A system error has occurred.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT = 4 | &nbsp;Unsupported audio format, such as unsupported encoding type, sample format etc.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_ENGINE_NOT_EXIST = 5 | &nbsp;audio engine does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST = 6 | &nbsp;audio pipeline does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_NODE_NOT_EXIST = 7 | &nbsp;audio node does not exist.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT = 8 | &nbsp;the connect or disconnect between the nodes is unsupported.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION = 9 | &nbsp;Unsupported operation.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS = 10 | &nbsp;The application attempted to create an object that exceeds the system's maximum limit.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING = 11 | &nbsp;Required parameters are missing.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_TIMEOUT = 12 | &nbsp;Operation timed out.<br>**Since**: 22 |
| AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED = 13 | &nbsp;Memory allocation failed.<br>**Since**: 22 |

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
| AUDIO_SAMPLE_U8 = 0 | Unsigned 8 format.<br>**Since**: 22 |
| AUDIO_SAMPLE_S16LE = 1 | Signed 16 bit integer, little endian.<br>**Since**: 22 |
| AUDIO_SAMPLE_S24LE = 2 | Signed 24 bit integer, little endian.<br>**Since**: 22 |
| AUDIO_SAMPLE_S32LE = 3 | Signed 32 bit integer, little endian.<br>**Since**: 22 |
| AUDIO_SAMPLE_F32LE = 4 | 32 bit IEEE floating point, little endian.<br>**Since**: 22 |

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
| AUDIO_ENCODING_TYPE_RAW = 0 | PCM encoding type.<br>**Since**: 22 |

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
| SAMPLE_RATE_8000 = 8000 | 8kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_11025 = 11025 | 11.025kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_12000 = 12000 | 12kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_16000 = 16000 | 16kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_22050 = 22050 | 22.05kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_24000 = 24000 | 24kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_32000 = 32000 | 32kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_44100 = 44100 | 44.1kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_48000 = 48000 | 48kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_64000 = 64000 | 64kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_88200 = 88200 | 88.2kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_96000 = 96000 | 96kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_176400 = 176400 | 176.4kHz sample rate.<br>**Since**: 22 |
| SAMPLE_RATE_192000 = 192000 | 192kHz sample rate.<br>**Since**: 22 |

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
| SOUND_FIELD_FRONT_FACING = 1 | Front facing sound field type.<br>**Since**: 22 |
| SOUND_FIELD_GRAND = 2 | Grand sound field type.<br>**Since**: 22 |
| SOUND_FIELD_NEAR = 3 | Near sound field type.<br>**Since**: 22 |
| SOUND_FIELD_WIDE = 4 | Wide sound field type.<br>**Since**: 22 |

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
| ENVIRONMENT_TYPE_BROADCAST = 1 | Broadcast environment effect type.<br>**Since**: 22 |
| ENVIRONMENT_TYPE_EARPIECE = 2 | Earpiece environment effect type.<br>**Since**: 22 |
| ENVIRONMENT_TYPE_UNDERWATER = 3 | UnderWater environment effect type.<br>**Since**: 22 |
| ENVIRONMENT_TYPE_GRAMOPHONE = 4 | Gramophone environment effect type.<br>**Since**: 22 |

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
| VOICE_BEAUTIFIER_TYPE_CLEAR = 1 | Clear voice beautifier type.<br>**Since**: 22 |
| VOICE_BEAUTIFIER_TYPE_THEATRE = 2 | Theatre voice beautifier type.<br>**Since**: 22 |
| VOICE_BEAUTIFIER_TYPE_CD = 3 | CD voice beautifier type.<br>**Since**: 22 |
| VOICE_BEAUTIFIER_TYPE_RECORDING_STUDIO = 4 | Recording studio voice beautifier type.<br>**Since**: 22 |

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
| SPACE_RENDER_CCW = 0 | Rotate counterclockwise<br>**Since**: 23 |
| SPACE_RENDER_CW = 1 | Rotate clockwise<br>**Since**: 23 |

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
| PURE_VOICE_CHANGE_FEMALE = 1 | set female voice.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_MALE = 2 | set male voice.<br>**Since**: 23 |

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
| PURE_VOICE_CHANGE_TYPE_CARTOON = 1 | Cartoon voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_CUTE = 2 | Cute voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_FEMALE = 3 | Female voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_MALE = 4 | Male voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_MONSTER = 5 | Monster voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_ROBOTS = 6 | Robots voice type.<br>**Since**: 23 |
| PURE_VOICE_CHANGE_TYPE_SEASONED = 7 | Seasoned voice type.<br>**Since**: 23 |

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
| GENERAL_VOICE_CHANGE_TYPE_CUTE = 1 | Cute voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_CYBERPUNK = 2 | Cyberpunk voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_FEMALE = 3 | Female voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_MALE = 4 | Male voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_MIX = 5 | Mix voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_MONSTER = 6 | Monster voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_SEASONED = 7 | Seasoned voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_SYNTH = 8 | Synth voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_TRILL = 9 | Trill voice type.<br>**Since**: 23 |
| GENERAL_VOICE_CHANGE_TYPE_WAR = 10 | War voice type.<br>**Since**: 23 |


