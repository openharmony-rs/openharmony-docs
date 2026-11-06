# OH_MIDICallbacks
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=c7c129955ac3e0a437f10080843a22cc9c8a307d translatedAt=2026-11-03T04:31:06.176Z pushedAt=2026-11-04T03:11:47.050Z nl=1 -->

```c
typedef struct {...} OH_MIDICallbacks
```

## Overview

Client callback struct used to listen for hot-plug events of MIDI devices and critical service errors. It contains callback function pointers for device hot-plug and error handling, and is suitable for scenarios where an application needs to perceive MIDI device state changes in real time and handle exceptions.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](capi-native-midi-base-h.md#oh_midicallback_ondevicechange) onDeviceChange | Pointer to the callback invoked to handle device hot-swap events.<br>**Since:** 24 |
| [OH_MIDICallback_OnError](capi-native-midi-base-h.md#oh_midicallback_onerror) onError | Callback function pointer for handling critical errors that occur during service running.<br>**Since:** 24 |


