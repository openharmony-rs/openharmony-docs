# lowpower_audio_sink_base.h

## Overview

The file declares the structs and enums of the LowPowerAudioSink.

**Library**: liblowpower_avsink.so

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Related module**: [LowPowerAudioSink](capi-lowpoweraudiosink.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md) | OH_LowPowerAudioSink | The struct describes the declaration for the LowPowerAudioSink. |
| [OH_LowPowerAudioSinkCallback](capi-lowpoweraudiosink-oh-lowpoweraudiosinkcallback.md) | OH_LowPowerAudioSinkCallback | The struct contains a set of callback function pointers for the LowPowerAudioSink. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_LowPowerAudioSink_OnError)(OH_LowPowerAudioSink* sink, OH_AVErrCode errCode, const char* errorMsg, void* userData)](#oh_lowpoweraudiosink_onerror) | OH_LowPowerAudioSink_OnError | Called when an error occurs in the LowPowerAudioSink. |
| [typedef void (\*OH_LowPowerAudioSink_OnPositionUpdated)(OH_LowPowerAudioSink* sink, int64_t currentPosition, void* userData)](#oh_lowpoweraudiosink_onpositionupdated) | OH_LowPowerAudioSink_OnPositionUpdated | Called when the playback position is updated in the LowPowerAudioSink. |
| [typedef void (\*OH_LowPowerAudioSink_OnDataNeeded)(OH_LowPowerAudioSink* sink, OH_AVSamplesBuffer* samples, void* userData)](#oh_lowpoweraudiosink_ondataneeded) | OH_LowPowerAudioSink_OnDataNeeded | Called when the LowPowerAudioSink needs more data. |
| [typedef void (\*OH_LowPowerAudioSink_OnInterrupted)(OH_LowPowerAudioSink* sink, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint, void* userData)](#oh_lowpoweraudiosink_oninterrupted) | OH_LowPowerAudioSink_OnInterrupted | Called when the audio focus is interrupted in the LowPowerAudioSink. |
| [typedef void (\*OH_LowPowerAudioSink_OnDeviceChanged)(OH_LowPowerAudioSink* sink, OH_AudioStream_DeviceChangeReason reason, void* userData)](#oh_lowpoweraudiosink_ondevicechanged) | OH_LowPowerAudioSink_OnDeviceChanged | Called when the audio device changes in the LowPowerAudioSink. |
| [typedef void (\*OH_LowPowerAudioSink_OnEos)(OH_LowPowerAudioSink* sink, void* userData)](#oh_lowpoweraudiosink_oneos) | OH_LowPowerAudioSink_OnEos | Called when the playback is complete in the LowPowerAudioSink. This callback is included in [OH_LowPowerAudioSinkCallback](capi-lowpoweraudiosink-oh-lowpoweraudiosinkcallback.md). |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_LowPowerAudioSink_OnError)( OH_LowPowerAudioSink* sink, OH_AVErrCode errCode, const char* errorMsg, void* userData) | Called when an error occurs in the LowPowerAudioSink.<br>**Since**: 20 |
| void (*OH_LowPowerAudioSink_OnPositionUpdated)( OH_LowPowerAudioSink* sink, int64_t currentPosition, void* userData) | Called when the playback position is updated in the LowPowerAudioSink.<br>**Since**: 20 |
| void (*OH_LowPowerAudioSink_OnDataNeeded)( OH_LowPowerAudioSink* sink, OH_AVSamplesBuffer* samples, void* userData) | Called when the LowPowerAudioSink needs more data.<br>**Since**: 20 |
| void (*OH_LowPowerAudioSink_OnInterrupted)( OH_LowPowerAudioSink* sink, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint, void* userData) | Called when the audio focus is interrupted in the LowPowerAudioSink.<br>**Since**: 20 |
| void (*OH_LowPowerAudioSink_OnDeviceChanged)( OH_LowPowerAudioSink* sink, OH_AudioStream_DeviceChangeReason reason, void* userData) | Called when the audio device changes in the LowPowerAudioSink.<br>**Since**: 20 |
| void (*OH_LowPowerAudioSink_OnEos)(OH_LowPowerAudioSink* sink, void* userData) | Called when the playback is complete in the LowPowerAudioSink. This callback is included in [OH_LowPowerAudioSinkCallback](capi-lowpoweraudiosink-oh-lowpoweraudiosinkcallback.md).<br>**Since**: 20 |

## Function description

### OH_LowPowerAudioSink_OnError()

```c
typedef void (*OH_LowPowerAudioSink_OnError)(OH_LowPowerAudioSink* sink, OH_AVErrCode errCode, const char* errorMsg, void* userData)
```

**Description**

Called when an error occurs in the LowPowerAudioSink.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| errorCode | Error code when an error occurs |
| const char\* errorMsg | Error description information |
| void\* userData | User specific data |

### OH_LowPowerAudioSink_OnPositionUpdated()

```c
typedef void (*OH_LowPowerAudioSink_OnPositionUpdated)(OH_LowPowerAudioSink* sink, int64_t currentPosition, void* userData)
```

**Description**

Called when the playback position is updated in the LowPowerAudioSink.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| int64_t currentPosition | Returns the current playback progress value of the service, in milliseconds |
| void\* userData | User specific data |

### OH_LowPowerAudioSink_OnDataNeeded()

```c
typedef void (*OH_LowPowerAudioSink_OnDataNeeded)(OH_LowPowerAudioSink* sink, OH_AVSamplesBuffer* samples, void* userData)
```

**Description**

Called when the LowPowerAudioSink needs more data.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| OH_AVSamplesBuffer\* samples | OH_AVSamplesBuffer instance that will be written in |
| void\* userData | User specific data |

### OH_LowPowerAudioSink_OnInterrupted()

```c
typedef void (*OH_LowPowerAudioSink_OnInterrupted)(OH_LowPowerAudioSink* sink, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint, void* userData)
```

**Description**

Called when the audio focus is interrupted in the LowPowerAudioSink.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| OH_AudioInterrupt_ForceType type | The audio interrupt type, please refer to {@link OH_AudioInterrupt_ForceType} |
| OH_AudioInterrupt_Hint hint | The audio interrupt hint type, please refer to {@link OH_AudioInterrupt_Hint} |
| void\* userData | User specific data |

### OH_LowPowerAudioSink_OnDeviceChanged()

```c
typedef void (*OH_LowPowerAudioSink_OnDeviceChanged)(OH_LowPowerAudioSink* sink, OH_AudioStream_DeviceChangeReason reason, void* userData)
```

**Description**

Called when the audio device changes in the LowPowerAudioSink.

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| OH_AudioStream_DeviceChangeReason reason | Indicates that why does the output device changes, please refer to {@link OH_AudioStream_DeviceChangeReason} |
| void\* userData | User specific data |

### OH_LowPowerAudioSink_OnEos()

```c
typedef void (*OH_LowPowerAudioSink_OnEos)(OH_LowPowerAudioSink* sink, void* userData)
```

**Description**

Called when the playback is complete in the LowPowerAudioSink. This callback is included in [OH_LowPowerAudioSinkCallback](capi-lowpoweraudiosink-oh-lowpoweraudiosinkcallback.md).

**System capability**: SystemCapability.Multimedia.Media.LowPowerAVSink

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md)\* sink | OH_LowPowerAudioSink instance |
| void\* userData | User specific data |


