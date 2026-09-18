# OH_MIDIEvent

```c
typedef struct OH_MIDIEvent {...} OH_MIDIEvent
```

## Overview

MIDI Event Structure (Universal). The event data is transferred in Universal MIDI Packets (UMP) format. MIDI 1.0 byte stream data should be converted to UMP format before filling this structure.

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t timestamp | Timestamp in nanoseconds. Base time obtained via clock_gettime(CLOCK_MONOTONIC, &time) 0 indicates "send immediately".<br>**Since**: 24 |
| size_t length | Number of 32-bit words in the packet. e.g., 1 for Type 2/4 (64-bit messages use 2 words)<br>**Since**: 24 |
| uint32_t *data | Pointer to UMP data (Must be 4-byte aligned). This contains the raw UMP words (uint32_t).<br>**Since**: 24 |


