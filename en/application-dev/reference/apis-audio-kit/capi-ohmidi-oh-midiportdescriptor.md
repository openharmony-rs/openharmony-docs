# OH_MIDIPortDescriptor
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1e020c03bdc7e8347d2df773c6dec6050603f0f7 translatedAt=2026-11-10T03:11:16.689Z pushedAt=2026-11-10T04:49:27.941Z nl=1 -->

```c
typedef struct {...} OH_MIDIPortDescriptor
```

## Overview

Defines a port descriptor struct, which specifies the port index and MIDI protocol version (MIDI 1.0 or MIDI 2.0) when opening a port. The system automatically performs protocol adaptation and data conversion between the application and the hardware. It is suitable for scenarios that require compatible communication between different MIDI protocol versions.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t portIndex | Index of the port to open. The value ranges from 0 to the actual number of ports on the device minus 1. The valid index must be obtained through the device enumeration API.<br>**Since:** 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) protocol | Specifies the MIDI protocol version to use (MIDI 1.0 or MIDI 2.0). The service converts data between the application and the hardware based on this field. The application only needs to declare the expected protocol version. The following describes the system behavior when the protocol version does not match the hardware:<br> 1. Requesting OH_MIDI_PROTOCOL_1_0 on a MIDI 2.0 device: (lossless compatibility)<br>    The application sends UMP Type 2 (MIDI 1.0 channel voice) messages, and the service forwards them directly to the device without data loss.<br> 2. Requesting OH_MIDI_PROTOCOL_2_0 on a MIDI 1.0 device: (lossy conversion)<br>    The application sends UMP Type 4 (MIDI 2.0 channel voice) messages, and the service downgrades Type 4 to Type 2 (for example, truncating velocity values and discarding per-note data), which loses data precision. Messages newly added in MIDI 2.0 that cannot be expressed in MIDI 1.0 (such as Per-Note controller messages) may be discarded.<br>**Since:** 24 |


