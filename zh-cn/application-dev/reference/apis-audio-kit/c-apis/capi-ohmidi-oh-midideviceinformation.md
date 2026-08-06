# OH_MIDIDeviceInformation

```c
typedef struct OH_MIDIDeviceInformation {...} OH_MIDIDeviceInformation
```

## 概述

设备信息结构体。存储设备ID等相关信息。

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

**所在头文件：** [native_midi_base.h](capi-native-midi-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t midiDeviceId | Unique identifier for the MIDI device.<br>**起始版本：** 24 |
| [OH_MIDIDeviceType](capi-native-midi-base-h.md#oh_mididevicetype) deviceType | Type of the device (USB, BLE, etc.).<br>**起始版本：** 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) nativeProtocol | The native protocol supported by the hardware.- If OH_MIDI_PROTOCOL_1_0: The device is a legacy device or currently configured as such.- If OH_MIDI_PROTOCOL_2_0: The device supports MIDI 2.0 features.<br>**起始版本：** 24 |
| char deviceName[256] | Device name.<br>**起始版本：** 24 |
| uint64_t vendorId | Vendor ID.<br>**起始版本：** 24 |
| uint64_t productId | Product ID.<br>**起始版本：** 24 |
| char deviceAddress[64] | Physical address (for BLE device).<br>**起始版本：** 24 |


