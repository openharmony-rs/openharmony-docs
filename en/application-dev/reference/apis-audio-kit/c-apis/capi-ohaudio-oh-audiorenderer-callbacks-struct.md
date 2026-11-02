# OH_AudioRenderer_Callbacks_Struct

```c
struct OH_AudioRenderer_Callbacks_Struct {...}
```

## Overview

Declaring the callback struct for renderer stream.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Deprecated**: 20

**Replaced by**: Use the callback type: OH_AudioRenderer_OnWriteDataCallback, OH_AudioRenderer_OutputDeviceChangeCallback, OH_AudioRenderer_OnInterruptCallback, OH_AudioRenderer_OnErrorCallback separately.

**Related module**: [OHAudio](capi-others-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)](#oh_audiorenderer_onwritedata) | - | This function pointer will point to the callback function that is used to write audio data |
| [int32_t (\*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)](#oh_audiorenderer_onstreamevent) | - | This function pointer will point to the callback function that is used to handle audio renderer stream events. |
| [int32_t (\*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptevent) | - | This function pointer will point to the callback function that is used to handle audio interrupt events. |
| [int32_t (\*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)](#oh_audiorenderer_onerror) | - | This function pointer will point to the callback function that is used to handle audio error result. |

## Member function description

### OH_AudioRenderer_OnWriteData()

```c
int32_t (*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)
```

**Description**

This function pointer will point to the callback function thatis used to write audio data

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnWriteDataCallback.

### OH_AudioRenderer_OnStreamEvent()

```c
int32_t (*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio renderer stream events.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OutputDeviceChangeCallback.

### OH_AudioRenderer_OnInterruptEvent()

```c
int32_t (*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio interrupt events.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnInterruptCallback.

### OH_AudioRenderer_OnError()

```c
int32_t (*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)
```

**Description**

This function pointer will point to the callback function thatis used to handle audio error result.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnErrorCallback.


