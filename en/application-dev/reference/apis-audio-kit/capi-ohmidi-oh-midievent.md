# OH_MIDIEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=634d132e8abe7b7c43dfeb8e3f424ff260f676a7 translatedAt=2026-11-09T10:27:45.900Z pushedAt=2026-11-09T11:32:09.037Z nl=1 -->

```c
typedef struct {...} OH_MIDIEvent
```

## Overview

The MIDI event struct (general-purpose) is used to carry and transmit MIDI event data in the UMP (Universal MIDI Packet) format. It applies to scenarios of receiving, sending, and processing MIDI messages, for example, receiving and processing MIDI controller input events in music production applications, processing MIDI messages in digital audio workstations, and interacting with MIDI devices in music education applications. Raw byte stream (MIDI 1.0) data must be converted to the UMP format before being filled into this struct.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t timestamp | Timestamp, in nanoseconds.<br> The reference time is obtained through clock_gettime(CLOCK_MONOTONIC, &time). A value of 0 indicates immediate sending.|
| size_t length | Number of 32-bit words in the UMP packet, rather than the number of bytes. The value depends on the UMP message type.<br> For example, a Type 1 message (such as a UMP system real-time and common message) occupies 1 word (32 bits), and a Type 4 message (such as a UMP MIDI 2.0 channel voice message) occupies 2 words (64 bits).|
| uint32_t *data | Pointer to the UMP data, which contains UMP words (uint32_t). Raw byte stream (MIDI 1.0) data must be converted to the UMP format before being filled into this field. This pointer must point to a 4-byte-aligned memory address to meet the 32-bit boundary alignment requirement of the UMP specification.|


