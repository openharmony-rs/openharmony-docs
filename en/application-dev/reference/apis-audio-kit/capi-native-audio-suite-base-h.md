# native_audio_suite_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the basic data structs used in audio creation.

**File to include**: <ohaudiosuite/native_audio_suite_base.h>

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) | OH_AudioFormat | Describes the audio stream information, which is used to describe the basic audio format, required for audio creation.|
| [OH_AudioDataArray](capi-ohaudiosuite-oh-audiodataarray.md) | OH_AudioDataArray | Describes the input data for the multi-output rendering interface. It is used to obtain processed audio data when multiple output effect nodes are present in the pipeline.|
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) | OH_EqualizerFrequencyBandGains | Describes the configuration parameters for the equalizer effect node used in audio creation.|
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md) | OH_AudioSuite_SpaceRenderPositionParams | Defines the configuration parameters of the 3D spatial rendering effect node in fixed placement mode. Left-handed coordinate system: Extend your left hand and form an "L" shape with your thumb and index finger.<br> The thumb points to the right, the index finger points upward, and the other fingers point forward.<br> This creates a 3D left-handed coordinate system. In this coordinate system, the thumb, index finger,<br> and other fingers represent the positive directions of the x-axis, y-axis, and z-axis, respectively.|
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md) | OH_AudioSuite_SpaceRenderRotationParams | Defines the configuration parameters of the spatial rendering effect node in rotation mode.|
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md) | OH_AudioSuite_SpaceRenderExtensionParams | Defines the configuration parameters of the spatial rendering effect node in extension mode.|
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md) | OH_AudioSuite_PureVoiceChangeOption | Defines the pure voice change options of audio creation.|
| [OH_AudioSuiteEngineStruct](capi-ohaudiosuite-oh-audiosuiteenginestruct.md) | OH_AudioSuiteEngine | Describes the audio creation engine, which is used to manage audio creation pipelines.|
| [OH_AudioSuitePipelineStruct](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md) | OH_AudioSuitePipeline | Describes the audio creation pipeline, which is used to manage audio creation nodes.|
| [OH_AudioNodeStruct](capi-ohaudiosuite-oh-audionodestruct.md) | OH_AudioNode | Describes a node for audio creation, which is used to represent instances of audio creation nodes.|
| [OH_AudioNodeBuilderStruct](capi-ohaudiosuite-oh-audionodebuilderstruct.md) | OH_AudioNodeBuilder | Describes a builder for nodes used in audio creation. It allows you to create an [OH_AudioNode](../apis-audio-kit/capi-ohaudiosuite-oh-audionodestruct.md) object, define the data formats for input and output nodes, and configures the callback interface for input nodes.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioNode_Type](#oh_audionode_type) | OH_AudioNode_Type | Enumerates the types of audio creation nodes.|
| [OH_AudioSuite_PipelineWorkMode](#oh_audiosuite_pipelineworkmode) | OH_AudioSuite_PipelineWorkMode | Enumerates the working modes of the audio creation pipeline.|
| [OH_AudioSuite_PipelineState](#oh_audiosuite_pipelinestate) | OH_AudioSuite_PipelineState | Enumerates the operational states of the audio creation pipeline.|
| [OH_AudioSuite_Result](#oh_audiosuite_result) | OH_AudioSuite_Result | Enumerates the error codes for audio creation.|
| [OH_Audio_SampleFormat](#oh_audio_sampleformat) | OH_Audio_SampleFormat | Enumerates the bit depth of audio streams in an audio creation node.|
| [OH_Audio_EncodingType](#oh_audio_encodingtype) | OH_Audio_EncodingType | Enumerates the encoding types of audio streams.|
| [OH_Audio_SampleRate](#oh_audio_samplerate) | OH_Audio_SampleRate | Enumerates the sample rates of audio streams.|
| [OH_SoundFieldType](#oh_soundfieldtype) | OH_SoundFieldType | Enumerates the effect modes of sound field effect nodes used for audio creation.|
| [OH_EnvironmentType](#oh_environmenttype) | OH_EnvironmentType | Enumerates the types of environment effect nodes used for audio creation.|
| [OH_VoiceBeautifierType](#oh_voicebeautifiertype) | OH_VoiceBeautifierType | Enumerates the types of voice beautifier effect nodes used for audio creation.|
| [OH_AudioSuite_SurroundDirection](#oh_audiosuite_surrounddirection) | OH_AudioSuite_SurroundDirection | Defines the surround direction of the spatial rendering effect node in rotation mode.|
| [OH_AudioSuite_PureVoiceChangeGenderOption](#oh_audiosuite_purevoicechangegenderoption) | OH_AudioSuite_PureVoiceChangeGenderOption | Defines the gender of the pure voice change effect node used for audio creation.|
| [OH_AudioSuite_PureVoiceChangeType](#oh_audiosuite_purevoicechangetype) | OH_AudioSuite_PureVoiceChangeType | Defines the voice change type of the pure voice change effect node used for audio creation.|
| [OH_AudioSuite_GeneralVoiceChangeType](#oh_audiosuite_generalvoicechangetype) | OH_AudioSuite_GeneralVoiceChangeType | Defines the type of audio creation node for general voice change.|

### Macros

| Name| Description|
| -- | -- |
| EQUALIZER_BAND_NUM (10) | Number of equalizer bands, defined as 10.<br>**Since**: 22|
| OH_PURE_VOICE_DEFAULT_PITCH (0.0f) | Uses the pitch recommended by the system. Used for [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md).<br>**Since**: 23|

### Variables

| Name| Description|
| -- | -- |
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DEFAULT | Default equalizer band gain settings.<br> Band gains: {0, 0, 0, 0, 0, 0, 0, 0, 0, 0}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_BALLADS | Built-in ballad effect for the equalizer node.<br> Band gains: {3, 5, 2, -4, 1, 2, -3, 1, 4, 5}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CHINESE_STYLE | Built-in Chinese style effect for the equalizer node.<br> Band gains: {0, 0, 2, 0, 0, 4, 4, 2, 2, 5}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_CLASSICAL | Built-in classical effect for the equalizer node.<br> Band gains: {2, 3, 2, 1, 0, 0, -5, -5, -5, -6}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_DANCE_MUSIC | Built-in dance music effect for the equalizer node.<br> Band gains: {4, 3, 2, -3, 0, 0, 5, 4, 2, 0}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_JAZZ | Built-in jazz effect for the equalizer node.<br> Band gains: {2, 0, 2, 3, 6, 5, -1, 3, 4, 4}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_POP | Built-in pop effect for the equalizer node.<br> Band gains: {5, 2, 1, -1, -5, -5, -2, 1, 2, 4}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_RB | Built-in R&B effect for the equalizer node.<br> Band gains: {1, 4, 5, 3, -2, -2, 2, 3, 5, 5}.<br>**Since**: 22|
| const [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) OH_EQUALIZER_PARAM_ROCK | Built-in rock effect for the equalizer node.<br> Band gains: {6, 4, 4, 2, 0, 1, 3, 3, 5, 4}.<br>**Since**: 22|

## Enum Description

### OH_AudioNode_Type

```c
enum OH_AudioNode_Type
```

**Description**

Enumerates the types of audio creation nodes.

**Since**: 22

| Value| Description|
| -- | -- |
| INPUT_NODE_TYPE_DEFAULT = 1 | Input node that supports obtaining audio data from applications.<br>**Since**: 22|
| OUTPUT_NODE_TYPE_DEFAULT = 101 | Output node that supports providing audio data to applications.<br>**Since**: 22|
| EFFECT_NODE_TYPE_EQUALIZER = 201 | Equalizer effect node. The output audio format of the equalizer effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 22|
| EFFECT_NODE_TYPE_NOISE_REDUCTION = 202 | Noise reduction effect node. The output audio format of the noise reduction effect node is as follows:<br> Sample rate: 16000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 1<br>**Since**: 22|
| EFFECT_NODE_TYPE_SOUND_FIELD = 203 | Sound field effect node. The sound field effect node supports the sound field types enumerated in [OH_SoundFieldType](capi-native-audio-suite-base-h.md#oh_soundfieldtype).<br> The output audio format of the sound field effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 22|
| EFFECT_MULTII_OUTPUT_NODE_TYPE_AUDIO_SEPARATION = 204 | Source separation effect node. The source separation effect node can only be connected to an output node.<br> The output audio format of the source separation effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_F32LE<br> Channel count: 4 (first 2 channels for vocals, last 2 for accompaniment)<br>**Since**: 22|
| EFFECT_NODE_TYPE_VOICE_BEAUTIFIER = 205 | Voice beautification effect node. The voice beautification effect node supports the voice beautification types enumerated in [OH_VoiceBeautifierType](capi-native-audio-suite-base-h.md#oh_voicebeautifiertype).<br> The output audio format of the voice beautification effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 22|
| EFFECT_NODE_TYPE_ENVIRONMENT_EFFECT = 206 | Environment effect node. The output audio format of the environment effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 22|
| EFFECT_NODE_TYPE_AUDIO_MIXER = 207 | Audio mixer effect node. The output audio format of the audio mixer effect node is as follows:<br> Sample rate: [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate)<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_F32LE<br> Channel count: 2<br>**Since**: 22|
| EFFECT_NODE_TYPE_SPACE_RENDER = 208 | Spatial rendering effect node. The output audio format of the spatial rendering effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 23|
| EFFECT_NODE_TYPE_PURE_VOICE_CHANGE = 209 | Pure voice change effect node. The output audio format of the pure voice change effect node is as follows:<br> Sample rate: 16000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 1<br>**Since**: 23|
| EFFECT_NODE_TYPE_GENERAL_VOICE_CHANGE = 210 | General voice change effect node. The output audio format of the general voice change effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 2<br>**Since**: 23|
| EFFECT_NODE_TYPE_TEMPO_PITCH = 211 | Tempo and pitch effect node. The output audio format of the tempo and pitch effect node is as follows:<br> Sample rate: 48000 Hz<br> Sample format: [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat).AUDIO_SAMPLE_S16LE<br> Channel count: 1<br>**Since**: 23|

### OH_AudioSuite_PipelineWorkMode

```c
enum OH_AudioSuite_PipelineWorkMode
```

**Description**

Enumerates the working modes of the audio creation pipeline.

**Since**: 22

| Value| Description|
| -- | -- |
| AUDIOSUITE_PIPELINE_EDIT_MODE = 1 | Edit mode. In this mode, the pipeline can create various effect nodes for audio processing.|
| AUDIOSUITE_PIPELINE_REALTIME_MODE = 2 | Real-time rendering mode. In this mode, processed audio is played in real time during audio processing.<br> Only equalizer effect processing is supported in this mode.|

### OH_AudioSuite_PipelineState

```c
enum OH_AudioSuite_PipelineState
```

**Description**

Enumerates the operational states of the audio creation pipeline.

**Since**: 22

| Value| Description|
| -- | -- |
| AUDIOSUITE_PIPELINE_STOPPED = 1 | The pipeline is stopped.|
| AUDIOSUITE_PIPELINE_RUNNING = 2 | The pipeline is running.|

### OH_AudioSuite_Result

```c
enum OH_AudioSuite_Result
```

**Description**

Enumerates the error codes for audio creation.

**Since**: 22

| Value| Description|
| -- | -- |
| AUDIOSUITE_SUCCESS = 0 | The call is successful.|
| AUDIOSUITE_ERROR_INVALID_PARAM = 1 | Invalid input parameters.|
| AUDIOSUITE_ERROR_INVALID_STATE = 2 | Invalid state.|
| AUDIOSUITE_ERROR_SYSTEM = 3 | General system error.|
| AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT = 4 | Unsupported audio format, such as unsupported encoding type or sample format.|
| AUDIOSUITE_ERROR_ENGINE_NOT_EXIST = 5 | The engine does not exist.|
| AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST = 6 | The pipeline does not exist.|
| AUDIOSUITE_ERROR_NODE_NOT_EXIST = 7 | The node does not exist.|
| AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT = 8 | Nodes do not support connection.|
| AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION = 9 | Unsupported operation. For example, the audio format cannot be set for effect nodes.|
| AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS = 10 | The number of pipelines or nodes created reaches the upper limit. Specifically:<br> An engine supports the creation of up to 10 pipelines, with a maximum of 1 dedicated to real-time rendering.<br> Each pipeline can have up to 5 input nodes, 1 output node, 3 mixer nodes, 1 audio separation node, and up to 5 other effect nodes.|
| AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING = 11 | Mandatory parameters are missing. For example, the callback function is not set for the input node, or the audio format is not set for the output node.|
| AUDIOSUITE_ERROR_TIMEOUT = 12 | Operation timed out.|
| AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED = 13 | Memory allocation failed.|

### OH_Audio_SampleFormat

```c
enum OH_Audio_SampleFormat
```

**Description**

Enumerates the bit depth of audio streams in an audio creation node.

**Since**: 22

| Value| Description|
| -- | -- |
| AUDIO_SAMPLE_U8 = 0 | Unsigned 8-bit.|
| AUDIO_SAMPLE_S16LE = 1 | Short 16-bit little-endian.|
| AUDIO_SAMPLE_S24LE = 2 | Short 24-bit little-endian.|
| AUDIO_SAMPLE_S32LE = 3 | Short 32-bit little-endian.|
| AUDIO_SAMPLE_F32LE = 4 | Float 32-bit little-endian.|

### OH_Audio_EncodingType

```c
enum OH_Audio_EncodingType
```

**Description**

Enumerates the encoding types of audio streams.

**Since**: 22

| Value| Description|
| -- | -- |
| AUDIO_ENCODING_TYPE_RAW = 0 | PCM encoding.|

### OH_Audio_SampleRate

```c
enum OH_Audio_SampleRate
```

**Description**

Enumerates the sample rates of audio streams.

**Since**: 22

| Value| Description|
| -- | -- |
| SAMPLE_RATE_8000 = 8000 | Sample rate of 8 kHz.|
| SAMPLE_RATE_11025 = 11025 | Sample rate of 11.025 kHz.|
| SAMPLE_RATE_12000 = 12000 | Sample rate of 12 kHz.|
| SAMPLE_RATE_16000 = 16000 | Sample rate of 16 kHz.|
| SAMPLE_RATE_22050 = 22050 | Sample rate of 22.05 kHz.|
| SAMPLE_RATE_24000 = 24000 | Sample rate of 24 kHz.|
| SAMPLE_RATE_32000 = 32000 | Sample rate of 32 kHz.|
| SAMPLE_RATE_44100 = 44100 | Sample rate 44.1 kHz.|
| SAMPLE_RATE_48000 = 48000 | Sample rate of 48 kHz.|
| SAMPLE_RATE_64000 = 64000 | Sample rate of 64 kHz.|
| SAMPLE_RATE_88200 = 88200 | Sample rate of 88.2 kHz.|
| SAMPLE_RATE_96000 = 96000 | Sample rate of 96 kHz.|
| SAMPLE_RATE_176400 = 176400 | Sample rate of 176.4 kHz.|
| SAMPLE_RATE_192000 = 192000 | Sample rate of 192 kHz.|

### OH_SoundFieldType

```c
enum OH_SoundFieldType
```

**Description**

Enumerates the effect modes of sound field effect nodes used for audio creation.

**Since**: 22

| Value| Description|
| -- | -- |
| SOUND_FIELD_FRONT_FACING = 1 | Front-facing sound field effect.|
| SOUND_FIELD_GRAND = 2 | Grand sound field effect.|
| SOUND_FIELD_NEAR = 3 | Near-listening sound field effect.|
| SOUND_FIELD_WIDE = 4 | Wide sound field effect.|

### OH_EnvironmentType

```c
enum OH_EnvironmentType
```

**Description**

Enumerates the types of environment effect nodes used for audio creation.

**Since**: 22

| Value| Description|
| -- | -- |
| ENVIRONMENT_TYPE_BROADCAST = 1 | Broadcast environment effect.|
| ENVIRONMENT_TYPE_EARPIECE = 2 | Earpiece environment effect.|
| ENVIRONMENT_TYPE_UNDERWATER = 3 | Underwater environment effect.|
| ENVIRONMENT_TYPE_GRAMOPHONE = 4 | Gramophone environment effect.|

### OH_VoiceBeautifierType

```c
enum OH_VoiceBeautifierType
```

**Description**

Enumerates the types of voice beautifier effect nodes used for audio creation.

**Since**: 22

| Value| Description|
| -- | -- |
| VOICE_BEAUTIFIER_TYPE_CLEAR = 1 | Clear voice beautifier effect.|
| VOICE_BEAUTIFIER_TYPE_THEATRE = 2 | Theatre voice beautifier effect.|
| VOICE_BEAUTIFIER_TYPE_CD = 3 | CD-quality voice beautifier effect.|
| VOICE_BEAUTIFIER_TYPE_RECORDING_STUDIO = 4 | Recording studio voice beautifier effect.|

### OH_AudioSuite_SurroundDirection

```c
enum OH_AudioSuite_SurroundDirection
```

**Description**

Defines the surround direction of the spatial rendering effect node in rotation mode.

**Since**: 23

| Value| Description|
| -- | -- |
| SPACE_RENDER_CCW = 0 | Turn counterclockwise.|
| SPACE_RENDER_CW = 1 | Turn clockwise.|

### OH_AudioSuite_PureVoiceChangeGenderOption

```c
enum OH_AudioSuite_PureVoiceChangeGenderOption
```

**Description**

Defines the gender of the voice change effect node used for audio creation.

**Since**: 23

| Value| Description|
| -- | -- |
| PURE_VOICE_CHANGE_FEMALE = 1 | Sets the voice to female.|
| PURE_VOICE_CHANGE_MALE = 2 | Sets the voice to male.|

### OH_AudioSuite_PureVoiceChangeType

```c
enum OH_AudioSuite_PureVoiceChangeType
```

**Description**

Defines the voice change type of the pure voice change effect node used for audio creation.

**Since**: 23

| Value| Description|
| -- | -- |
| PURE_VOICE_CHANGE_TYPE_CARTOON = 1 | Sets the pure voice change type to cartoon.|
| PURE_VOICE_CHANGE_TYPE_CUTE = 2 | Sets the pure voice change type to cute.|
| PURE_VOICE_CHANGE_TYPE_FEMALE = 3 | Sets the pure voice change type to female.|
| PURE_VOICE_CHANGE_TYPE_MALE = 4 | Sets the pure voice change type to male.|
| PURE_VOICE_CHANGE_TYPE_MONSTER = 5 | Sets the pure voice change type to monster.|
| PURE_VOICE_CHANGE_TYPE_ROBOTS = 6 | Sets the pure voice change type to robot.|
| PURE_VOICE_CHANGE_TYPE_SEASONED = 7 | Sets the pure voice change type to seasoned.|

### OH_AudioSuite_GeneralVoiceChangeType

```c
enum OH_AudioSuite_GeneralVoiceChangeType
```

**Description**

Defines the general voice change type for audio creation.

**Since**: 23

| Value| Description|
| -- | -- |
| GENERAL_VOICE_CHANGE_TYPE_CUTE = 1 | Sets the general voice change type to cute.|
| GENERAL_VOICE_CHANGE_TYPE_CYBERPUNK = 2 | Sets the general voice change type to cuberpunk.|
| GENERAL_VOICE_CHANGE_TYPE_FEMALE = 3 | Sets the general voice change type to female.|
| GENERAL_VOICE_CHANGE_TYPE_MALE = 4 | Sets the general voice change type to male.|
| GENERAL_VOICE_CHANGE_TYPE_MIX = 5 | Sets the general voice change type to mix.|
| GENERAL_VOICE_CHANGE_TYPE_MONSTER = 6 | Sets the general voice change type to monster.|
| GENERAL_VOICE_CHANGE_TYPE_SEASONED = 7 | Sets the general voice change type to seasoned.|
| GENERAL_VOICE_CHANGE_TYPE_SYNTH = 8 | Sets the general voice change type to synthesizer.|
| GENERAL_VOICE_CHANGE_TYPE_TRILL = 9 | Sets the general voice change type to trill.|
| GENERAL_VOICE_CHANGE_TYPE_WAR = 10 | Sets the general voice change type to war.|
<!--no_check-->