# OH_MIDIPortInformation

```c
typedef struct OH_MIDIPortInformation {...} OH_MIDIPortInformation
```

## Overview

Port Information (detailed). Used for enumeration (contains display names).

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t portIndex | The index of the port.<br>**Since**: 24 |
| int64_t deviceId | The ID of the device this port belongs to.<br>**Since**: 24 |
| [OH_MIDIPortDirection](capi-native-midi-base-h.md#oh_midiportdirection) direction | Direction of the port (Input/Output).<br>**Since**: 24 |
| char name[64] | Name of the port.<br>**Since**: 24 |


