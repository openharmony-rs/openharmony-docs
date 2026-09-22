# OH_MIDIPortDescriptor

```c
typedef struct OH_MIDIPortDescriptor {...} OH_MIDIPortDescriptor
```

## Overview

Port Descriptor.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t portIndex | The unique ID of the port within the device (index).<br>**Since**: 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) protocol | The requested protocol behavior for this session.<br> This field dictates how the Service translates data between the app and the hardware.<br> **Compatibility Behavior:**<br> 1. **Request OH_MIDI_PROTOCOL_1_0 on a 2.0 Device**: (Safe) - The service creates a virtual 1.0 view. - App sends UMP Type 2 (MIDI 1.0 Channel Voice). - Device receives UMP Type 2. - Fully compatible.<br> 2. **Request OH_MIDI_PROTOCOL_2_0 on a 1.0 Device**: (Lossy) - The service creates a virtual 2.0 view. - App sends UMP Type 4 (MIDI 2.0 Voice). - Service **down-converts** Type 4 to Type 2 (e.g., clipping velocity, dropping per-note data). - **Warning**: Data precision will be lost. Advanced messages may be dropped.<br>**Since**: 24 |


