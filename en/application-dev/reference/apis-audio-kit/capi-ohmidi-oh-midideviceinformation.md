# OH_MIDIDeviceInformation
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=97f0cf519f319092069e1d5a968f84961b25ec9e translatedAt=2026-11-10T03:10:36.756Z pushedAt=2026-11-10T04:48:48.170Z nl=1 -->

```c
typedef struct {...} OH_MIDIDeviceInformation
```

## Overview

Defines a device information struct used to store detailed information about a MIDI device, including the device unique identifier, device type (such as USB and BLE), supported MIDI protocol, device name, vendor ID, product ID, and physical address. It is used to obtain and pass the complete attribute information of a device in scenarios such as MIDI device enumeration, identification, and connection management.

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int64_t midiDeviceId | Unique ID of a MIDI device.<br>**Since**: 24|
| [OH_MIDIDeviceType](capi-native-midi-base-h.md#oh_mididevicetype) deviceType | Device type (USB or BLE).<br>**Since:** 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) nativeProtocol | MIDI protocol natively supported by the device. - OH_MIDI_PROTOCOL_1_0: The device is a legacy device or is currently configured as MIDI 1.0.<br> - OH_MIDI_PROTOCOL_2_0: The device uses the MIDI 2.0 protocol.<br>**Since:** 24 |
| char deviceName[256] | Device name.<br>**Since**: 24|
| uint64_t vendorId | Vendor ID.<br>**Since**: 24|
| uint64_t productId | Product ID.<br>**Since**: 24|
| char deviceAddress[64] | Physical address of the device, in the colon-separated hexadecimal MAC address format, for example, "00:11:22:33:44:55". This field is valid only for the BLE device type.<br>**Since:** 24 |


