# OH_MIDICallbacks
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=40b8574cf7284f42e60f2c280c655eafea0c92e5 translatedAt=2026-11-10T03:10:26.581Z pushedAt=2026-11-10T04:48:33.871Z nl=1 -->

```c
typedef struct {...} OH_MIDICallbacks
```

## Overview

The client callback struct is used to listen for hot-plug events of MIDI devices and critical service errors. It contains callback function pointers for device hot-plug and error handling, and is applicable to scenarios where an application needs to sense MIDI device state changes in real time and handle exceptions.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](capi-native-midi-base-h.md#oh_midicallback_ondevicechange) onDeviceChange | Callback function pointer for handling device hot-plug events.<br>**Since Version:** 24 |
| [OH_MIDICallback_OnError](capi-native-midi-base-h.md#oh_midicallback_onerror) onError | Callback function pointer for handling critical errors that occur during service running.<br>**Since Version:** 24 |


