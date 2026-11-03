# OH_AudioCapturer_Callbacks_Struct

```c
struct OH_AudioCapturer_Callbacks_Struct {...}
```

## Overview

Declaring the callback struct for capturer stream.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Deprecated**: 20

**Replaced by**: Use the callback type: OH_AudioCapturer_OnReadDataCallback, OH_AudioCapturer_OnDeviceChangeCallback, OH_AudioCapturer_OnInterruptCallback and OH_AudioCapturer_OnErrorCallback separately.

**Related module**: [OHAudio](capi-others-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)](#oh_audiocapturer_onreaddata) | - | This function pointer will point to the callback function that is used to read audio data. |
| [int32_t (\*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)](#oh_audiocapturer_onstreamevent) | - | This function pointer will point to the callback function that is used to handle audio capturer stream events. |
| [int32_t (\*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptevent) | - | This function pointer will point to the callback function that is used to handle audio interrupt events. |
| [int32_t (\*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)](#oh_audiocapturer_onerror) | - | This function pointer will point to the callback function that is used to handle audio error result. |

## Member function description

### OH_AudioCapturer_OnReadData()

```c
int32_t (*OH_AudioCapturer_OnReadData)(OH_AudioCapturer* capturer,void* userData,void* buffer,int32_t length)
```

**Description**

This function pointer will point to the callback function thatis used to read audio data.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioCapturer_OnReadDataCallback

### OH_AudioCapturer_OnStreamEvent()

```c
int32_t (*OH_AudioCapturer_OnStreamEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Event event)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio capturer stream events.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioCapturer_OnDeviceChangeCallback

### OH_AudioCapturer_OnInterruptEvent()

```c
int32_t (*OH_AudioCapturer_OnInterruptEvent)(OH_AudioCapturer* capturer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio interrupt events.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioCapturer_OnInterruptCallback

### OH_AudioCapturer_OnError()

```c
int32_t (*OH_AudioCapturer_OnError)(OH_AudioCapturer* capturer,void* userData,OH_AudioStream_Result error)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio error result.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioCapturer_OnErrorCallback


