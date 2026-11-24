# native_audio_common.h

## Overview

Declare the audio common base data structure.<br> Defines the types of public return values for audio interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Related module**: [OHAudio](capi-audio-kit-ohaudio.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioCommon_Result](#oh_audiocommon_result) | OH_AudioCommon_Result | Define the result of the function execution. |
| [OH_AudioScene](#oh_audioscene) | OH_AudioScene | Defines the audio scene. |
| [OH_AudioRingerMode](#oh_audioringermode) | OH_AudioRingerMode | Defines the ringer mode. |
| [OH_AudioNoiseReductionMode](#oh_audionoisereductionmode) | OH_AudioNoiseReductionMode | Enumerates the noise reduction modes. |

## Enum type description

### OH_AudioCommon_Result

```c
enum OH_AudioCommon_Result
```

**Description**

Define the result of the function execution.

<!--Device-enum OH_AudioCommon_Result--><!--Device-enum OH_AudioCommon_Result-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIOCOMMON_RESULT_SUCCESS = 0 | &nbsp;The call was successful.<br><!--Device-AUDIOCOMMON_RESULT_SUCCESS = 0--><!--Device-AUDIOCOMMON_RESULT_SUCCESS = 0-End--> |
| AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED = 201 | &nbsp;This means that caller does not have the required permission.<br>**Since**: 26.0.0<br><!--Device-AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED = 201--><!--Device-AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED = 201-End--> |
| AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101 | &nbsp;This means that the input parameter is invalid.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101--><!--Device-AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101-End--> |
| AUDIOCOMMON_RESULT_ERROR_NO_MEMORY = 6800102 | &nbsp;This means there is no memory left.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_NO_MEMORY = 6800102--><!--Device-AUDIOCOMMON_RESULT_ERROR_NO_MEMORY = 6800102-End--> |
| AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE = 6800103 | &nbsp;Execution status exception.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE = 6800103--><!--Device-AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE = 6800103-End--> |
| AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED = 6800104 | &nbsp;This means the operation is unsupported.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED = 6800104--><!--Device-AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED = 6800104-End--> |
| AUDIOCOMMON_RESULT_ERROR_TIMEOUT = 6800105 | &nbsp;This means the operation timed out.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_TIMEOUT = 6800105--><!--Device-AUDIOCOMMON_RESULT_ERROR_TIMEOUT = 6800105-End--> |
| AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH = 6800106 | &nbsp;This means the input audio data does not match the required frame length.<br>**Since**: 26.0.0<br><!--Device-AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH = 6800106--><!--Device-AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH = 6800106-End--> |
| AUDIOCOMMON_RESULT_ERROR_STREAM_LIMIT = 6800201 | &nbsp;This means the stream limit is reached.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_STREAM_LIMIT = 6800201--><!--Device-AUDIOCOMMON_RESULT_ERROR_STREAM_LIMIT = 6800201-End--> |
| AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301 | &nbsp;A system error has occurred.<br><!--Device-AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301--><!--Device-AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301-End--> |
| AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED = 6800302 | System service process terminated.<br>**Since**: 26.0.1<br><!--Device-AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED = 6800302--><!--Device-AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED = 6800302-End--> |
| AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET = 6800501 | Required network conditions not met.<br>**Since**: 26.0.1<br><!--Device-AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET = 6800501--><!--Device-AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET = 6800501-End--> |
| AUDIOCOMMON_RESULT_ERROR_STORAGE_NOT_ENOUGH = 6800502 | Insufficient storage space.<br>**Since**: 26.0.1<br><!--Device-AUDIOCOMMON_RESULT_ERROR_STORAGE_NOT_ENOUGH = 6800502--><!--Device-AUDIOCOMMON_RESULT_ERROR_STORAGE_NOT_ENOUGH = 6800502-End--> |

### OH_AudioScene

```c
enum OH_AudioScene
```

**Description**

Defines the audio scene.

<!--Device-enum OH_AudioScene--><!--Device-enum OH_AudioScene-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_SCENE_DEFAULT = 0 | Default audio scene.<br>**Since**: 12<br><!--Device-AUDIO_SCENE_DEFAULT = 0--><!--Device-AUDIO_SCENE_DEFAULT = 0-End--> |
| AUDIO_SCENE_RINGING = 1 | Ringing scene.<br>**Since**: 12<br><!--Device-AUDIO_SCENE_RINGING = 1--><!--Device-AUDIO_SCENE_RINGING = 1-End--> |
| AUDIO_SCENE_PHONE_CALL = 2 | Phone call scene.<br>**Since**: 12<br><!--Device-AUDIO_SCENE_PHONE_CALL = 2--><!--Device-AUDIO_SCENE_PHONE_CALL = 2-End--> |
| AUDIO_SCENE_VOICE_CHAT = 3 | Voice chat scene.<br>**Since**: 12<br><!--Device-AUDIO_SCENE_VOICE_CHAT = 3--><!--Device-AUDIO_SCENE_VOICE_CHAT = 3-End--> |

### OH_AudioRingerMode

```c
enum OH_AudioRingerMode
```

**Description**

Defines the ringer mode.

<!--Device-enum OH_AudioRingerMode--><!--Device-enum OH_AudioRingerMode-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| AUDIO_RINGER_MODE_SILENT = 0 | Silent ringer mode.<br>**Since**: 20<br><!--Device-AUDIO_RINGER_MODE_SILENT = 0--><!--Device-AUDIO_RINGER_MODE_SILENT = 0-End--> |
| AUDIO_RINGER_MODE_VIBRATE = 1 | Vibrate ringer mode.<br>**Since**: 20<br><!--Device-AUDIO_RINGER_MODE_VIBRATE = 1--><!--Device-AUDIO_RINGER_MODE_VIBRATE = 1-End--> |
| AUDIO_RINGER_MODE_NORMAL = 2 | Normal ringer mode.<br>**Since**: 20<br><!--Device-AUDIO_RINGER_MODE_NORMAL = 2--><!--Device-AUDIO_RINGER_MODE_NORMAL = 2-End--> |

### OH_AudioNoiseReductionMode

```c
enum OH_AudioNoiseReductionMode
```

**Description**

Enumerates the noise reduction modes.

<!--Device-enum OH_AudioNoiseReductionMode--><!--Device-enum OH_AudioNoiseReductionMode-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| AUDIO_NOISE_REDUCTION_MODE_FIDELITY = 0 | Fidelity mode, no noise reduction.<br>**Since**: 26.0.0<br><!--Device-AUDIO_NOISE_REDUCTION_MODE_FIDELITY = 0--><!--Device-AUDIO_NOISE_REDUCTION_MODE_FIDELITY = 0-End--> |
| AUDIO_NOISE_REDUCTION_MODE_PURE_VOCALS = 1 | Pure vocals mode, strong noise reduction.<br>**Since**: 26.0.0<br><!--Device-AUDIO_NOISE_REDUCTION_MODE_PURE_VOCALS = 1--><!--Device-AUDIO_NOISE_REDUCTION_MODE_PURE_VOCALS = 1-End--> |
| AUDIO_NOISE_REDUCTION_MODE_STANDARD = 2 | Standard mode, weak noise reduction.<br>**Since**: 26.0.0<br><!--Device-AUDIO_NOISE_REDUCTION_MODE_STANDARD = 2--><!--Device-AUDIO_NOISE_REDUCTION_MODE_STANDARD = 2-End--> |


