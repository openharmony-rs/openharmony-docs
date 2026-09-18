# OH_MIDICallbacks

```c
typedef struct OH_MIDICallbacks {...} OH_MIDICallbacks
```

## Overview

Client callbacks structure.

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](capi-native-midi-base-h.md#oh_midicallback_ondevicechange) onDeviceChange | Handler for device hotplug events.<br>**Since**: 24 |
| [OH_MIDICallback_OnError](capi-native-midi-base-h.md#oh_midicallback_onerror) onError | Handler for critical service errors.<br>**Since**: 24 |


