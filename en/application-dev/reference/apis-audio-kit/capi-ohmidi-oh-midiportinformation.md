# OH_MIDIPortInformation
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_MIDIPortInformation
```

## Overview

This struct defines the port information, which is used to enumerate ports, including port names.

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t portIndex | Index of a port in the device.<br>**Since**: 24|
| int64_t deviceId | ID of the MIDI device to which a port belongs.<br>**Since**: 24|
| [OH_MIDIPortDirection](capi-native-midi-base-h.md#oh_midiportdirection) direction | Port direction (input or output).<br>**Since**: 24|
| char name[64] | Port name.<br>**Since**: 24|
