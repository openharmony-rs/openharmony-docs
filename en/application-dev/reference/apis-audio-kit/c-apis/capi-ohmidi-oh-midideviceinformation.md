# OH_MIDIDeviceInformation

```c
typedef struct OH_MIDIDeviceInformation {...} OH_MIDIDeviceInformation
```

## Overview

Device Information. Used for enumeration and display.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

**Header file**: [native_midi_base.h](capi-native-midi-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t midiDeviceId | Unique identifier for the MIDI device.<br>**Since**: 24 |
| [OH_MIDIDeviceType](capi-native-midi-base-h.md#oh_mididevicetype) deviceType | Type of the device (USB, BLE, etc.).<br>**Since**: 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) nativeProtocol | The native protocol supported by the hardware.<br> - If OH_MIDI_PROTOCOL_1_0: The device is a legacy device or currently configured as such. - If OH_MIDI_PROTOCOL_2_0: The device supports MIDI 2.0 features.<br>**Since**: 24 |
| char deviceName[256] | Device name.<br>**Since**: 24 |
| uint64_t vendorId | Vendor ID.<br>**Since**: 24 |
| uint64_t productId | Product ID.<br>**Since**: 24 |
| char deviceAddress[64] | Physical address (for BLE device).<br>**Since**: 24 |


