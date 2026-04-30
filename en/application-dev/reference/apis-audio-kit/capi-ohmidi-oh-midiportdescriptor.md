# OH_MIDIPortDescriptor
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_MIDIPortDescriptor
```

## Overview

This struct describes the port descriptor, which is used to specify the port index and protocol behavior for opening a port.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t portIndex | Index of the port to be opened.<br>**Since**: 24|
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) protocol | MIDI protocol version to be used (MIDI 1.0 or MIDI 2.0). The service converts data between applications and hardware based on the value of this field. An application merely declares the expected protocol version. The following system behavior applies when the protocol version does not match the hardware:<br> 1. Requesting OH_MIDI_PROTOCOL_1.0 on a MIDI 2.0 device (lossless compatibility): <br>    The application sends UMP Type 2 (MIDI 1.0 channel voice) messages. The service forwards them directly to the device. No data loss occurs.<br> 2. Requesting OH_MIDI_PROTOCOL_2.0 on a MIDI 1.0 device (lossy conversion): <br>    The application sends UMP Type 4 (MIDI 2.0 channel voice) messages. The service down-converts them to Type 2 messages (for example, truncating velocity values and discarding per-note data). Data precision is lost, and advanced messages may be discarded.<br>**Since**: 24|
