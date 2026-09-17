# OH_AudioRenderer_Callbacks_Struct

```c
typedef struct OH_AudioRenderer_Callbacks_Struct {...} OH_AudioRenderer_Callbacks
```

## Overview

Declaring the callback struct for renderer stream.

**Since**: 10

**Deprecated**: 20

**Replaced by**: Use the callback type: OH_AudioRenderer_OnWriteDataCallback, OH_AudioRenderer_OutputDeviceChangeCallback, OH_AudioRenderer_OnInterruptCallback, OH_AudioRenderer_OnErrorCallback separately.

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)](#oh_audiorenderer_onwritedata) |  |
| [int32_t (\*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)](#oh_audiorenderer_onstreamevent) |  |
| [int32_t (\*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptevent) |  |
| [int32_t (\*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)](#oh_audiorenderer_onerror) |  |

## Member function description

### OH_AudioRenderer_OnWriteData()

```c
int32_t (*OH_AudioRenderer_OnWriteData)(OH_AudioRenderer* renderer,void* userData,void* buffer,int32_t length)
```

**Description**

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnWriteDataCallback.

### OH_AudioRenderer_OnStreamEvent()

```c
int32_t (*OH_AudioRenderer_OnStreamEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Event event)
```

**Description**

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OutputDeviceChangeCallback.

### OH_AudioRenderer_OnInterruptEvent()

```c
int32_t (*OH_AudioRenderer_OnInterruptEvent)(OH_AudioRenderer* renderer,void* userData,OH_AudioInterrupt_ForceType type,OH_AudioInterrupt_Hint hint)
```

**Description**

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnInterruptCallback.

### OH_AudioRenderer_OnError()

```c
int32_t (*OH_AudioRenderer_OnError)(OH_AudioRenderer* renderer,void* userData,OH_AudioStream_Result error)
```

**Description**

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OnErrorCallback.


