# native_audio_common.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96c2f543d580d0d2b2dabb53953551af3ab0252e translatedAt=2026-11-03T03:48:23.919Z pushedAt=2026-11-04T03:11:46.942Z nl=1 -->

## Overview

The file declares the common basic audio data structs.<br> It defines the types of the common return values of audio interfaces.

**File to include**: <ohaudio/native_audio_common.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioCommon_Result](#oh_audiocommon_result) | OH_AudioCommon_Result | Enumerates the audio operation results.|
| [OH_AudioScene](#oh_audioscene) | OH_AudioScene | Enumerates the audio scenes.|
| [OH_AudioRingerMode](#oh_audioringermode) | OH_AudioRingerMode | Defines the ringer modes.|
| [OH_AudioNoiseReductionMode](#oh_audionoisereductionmode) | OH_AudioNoiseReductionMode | Defines the recording noise reduction mode.|

## Enum Description

### OH_AudioCommon_Result

```c
enum OH_AudioCommon_Result
```

**Description**

Enumerates the audio operation results.

**Since**: 12

| Value | Description |
| -- | -- |
| AUDIOCOMMON_RESULT_SUCCESS = 0 | Success. |
| AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED = 201 | The caller does not have the required permission.<br>**Since Version:** 26.0.0 |
| AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101 | Invalid input parameter. |
| AUDIOCOMMON_RESULT_ERROR_NO_MEMORY = 6800102 | Insufficient memory. |
| AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE = 6800103 | Illegal state. |
| AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED = 6800104 | The operation is not supported. |
| AUDIOCOMMON_RESULT_ERROR_TIMEOUT = 6800105 | Operation timed out. |
| AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH = 6800106 | The input audio data does not match the required frame length.<br>**Since Version:** 26.0.0 |
| AUDIOCOMMON_RESULT_ERROR_STREAM_LIMIT = 6800201 | The maximum number supported by the system is reached. |
| AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301 | General system error. |
| AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED = 6800302 | The system service process is terminated.<br>**Since Version:** 26.0.1 |
| AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET = 6800501 | The network condition is not met.<br>**Since Version:** 26.0.1 |
| AUDIOCOMMON_RESULT_ERROR_STORAGE_NOT_ENOUGH = 6800502 | Insufficient storage space.<br>**Since Version:** 26.0.1 |

### OH_AudioScene

```c
enum OH_AudioScene
```

**Description**

Enumerates the audio scenes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_SCENE_DEFAULT = 0 | Default audio scene.|
| AUDIO_SCENE_RINGING = 1 | Ringing scene.|
| AUDIO_SCENE_PHONE_CALL = 2 | Phone call scene.|
| AUDIO_SCENE_VOICE_CHAT = 3 | Voice chat scene.|

### OH_AudioRingerMode

```c
enum OH_AudioRingerMode
```

**Description**

Defines the ringer modes.

**Device behavior difference**: If this API is set to the vibration mode on a device without a vibration component, no vibration effect is generated.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| AUDIO_RINGER_MODE_SILENT = 0 | Silent mode.|
| AUDIO_RINGER_MODE_VIBRATE = 1 | Vibration mode.|
| AUDIO_RINGER_MODE_NORMAL = 2 | Normal mode.|

### OH_AudioNoiseReductionMode

```c
enum OH_AudioNoiseReductionMode
```

**Description**

Defines the recording noise reduction mode.

**Since:** 26.0.0

| Enum Item| Description|
| -- | -- |
| AUDIO_NOISE_REDUCTION_MODE_FIDELITY = 0 | Fidelity mode, with no noise reduction applied.|
| AUDIO_NOISE_REDUCTION_MODE_PURE_VOCALS = 1 | Pure vocals mode, with strong noise reduction.|
| AUDIO_NOISE_REDUCTION_MODE_STANDARD = 2 | Standard mode, with weak noise reduction.|


