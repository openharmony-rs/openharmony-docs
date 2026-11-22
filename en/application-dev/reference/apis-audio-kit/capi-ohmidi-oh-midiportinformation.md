# OH_MIDIPortInformation
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1921c8e6e7890c2fb18f9ddb830a4261dd424757 translatedAt=2026-11-03T04:32:17.063Z pushedAt=2026-11-04T03:11:47.056Z nl=1 -->

```c
typedef struct {...} OH_MIDIPortInformation
```

## Overview

Defines a port information structure used to enumerate and identify MIDI device ports. It contains key information such as the displayable port name, port index, owning device ID, and port direction (input or output), helping developers manage and operate each port in MIDI applications.

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


