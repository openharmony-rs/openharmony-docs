# OH_MIDIEvent

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T04:01:48.257Z pushedAt=2026-07-22T01:06:43.437Z -->

```c
typedef struct {...} OH_MIDIEvent
```

## Overview

This struct defines a MIDI event (general). Event data is transmitted in the Universal MIDI Packets (UMP) format. Raw byte stream (MIDI 1.0) data must be converted to the UMP format before populating this struct.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t timestamp | Timestamp, in nanoseconds.<br> The reference time can be obtained using `clock_gettime(CLOCK_MONOTONIC, &time)`. The value **0** indicates sending messages immediately.<br>**Since**: 24|
| size_t length | Number of 32-bit words in the UMP packet.<br> For example, a Type 1 message occupies 1 word (32 bits), and a Type 2 message occupies 2 words (64 bits).<br> This parameter indicates the number of uint32_t words in the UMP data, not the number of bytes.<br>**Since:** 24 |
| uint32_t *data | Pointer to the UMP data, including original UMP words (uint32_t).<br> This pointer must point to a 4-byte aligned memory address to comply with the UMP specification's requirement for 32-bit boundary alignment.<br>**Since**: 24|