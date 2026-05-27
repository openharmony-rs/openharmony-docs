# OH_MIDIDeviceInformation
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_MIDIDeviceInformation
```

## Overview

This struct defines device information, such as the storage device ID.

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int64_t midiDeviceId | Unique ID of a MIDI device.<br>**Since**: 24|
| [OH_MIDIDeviceType](capi-native-midi-base-h.md#oh_mididevicetype) deviceType | Device type (such as USB and BLE).<br>**Since**: 24|
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) nativeProtocol | MIDI protocol natively supported by the device. - **OH_MIDI_PROTOCOL_1_0**: The device is a traditional device or the current configuration is MIDI 1.0.<br> - **OH_MIDI_PROTOCOL_2_0**: The device supports MIDI 2.0.<br>**Since**: 24|
| char deviceName[256] | Device name.<br>**Since**: 24|
| uint64_t vendorId | Vendor ID.<br>**Since**: 24|
| uint64_t productId | Product ID.<br>**Since**: 24|
| char deviceAddress[64] | Physical address of a device (BLE device).<br>**Since**: 24|
