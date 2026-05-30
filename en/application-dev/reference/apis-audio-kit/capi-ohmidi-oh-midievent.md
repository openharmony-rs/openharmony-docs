# OH_MIDIEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_MIDIEvent
```

## Overview

This struct describes a generic MIDI event structure, applicable to both raw byte stream (MIDI 1.0) and Universal MIDI Packet (UMP) data formats.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t timestamp | Timestamp, in nanoseconds.<br> The reference time can be obtained using clock_gettime(CLOCK_MONOTONIC, &time). The value **0** indicates sending messages immediately.<br>**Since**: 24|
| size_t length | Number of 32-bit words in the UMP packet.<br> For example: A Type 2 or Type 4 message occupy 1 word (a 64-bit message occupies 2 words).<br> This field indicates the number of uint32_t words in the UMP data, not the number of bytes.<br>**Since**: 24|
| uint32_t *data | Pointer to the UMP data, including original UMP words (uint32_t).<br> This pointer must point to a 4-byte aligned memory address to comply with the UMP specification's requirement for 32-bit boundary alignment.<br>**Since**: 24|
