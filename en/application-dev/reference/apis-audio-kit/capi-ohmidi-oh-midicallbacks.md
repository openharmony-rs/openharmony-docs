# OH_MIDICallbacks

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T04:01:40.664Z pushedAt=2026-07-21T09:00:09.134Z -->

```c
typedef struct {...} OH_MIDICallbacks
```

## Overview

Client callback struct, containing pointers to callback functions for device change events and error handling.

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](capi-native-midi-base-h.md#oh_midicallback_ondevicechange) onDeviceChange | Pointer to the callback invoked to handle device hot-swap events.<br>**Since:** 24 |
| [OH_MIDICallback_OnError](capi-native-midi-base-h.md#oh_midicallback_onerror) onError | Pointer to the callback invoked to handle critical service errors.<br>**Since:** 24 |