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

## 概述

设备信息结构体。储存设备ID等相关信息。

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

**所在头文件：** [native_midi_base.h](capi-native-midi-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t midiDeviceId | MIDI设备的唯一标识符。<br>**起始版本：** 24 |
| [OH_MIDIDeviceType](capi-native-midi-base-h.md#oh_mididevicetype) deviceType | 设备类型（USB、BLE等）。<br>**起始版本：** 24 |
| [OH_MIDIProtocol](capi-native-midi-base-h.md#oh_midiprotocol) nativeProtocol | 设备原生支持的MIDI协议。- OH_MIDI_PROTOCOL_1_0：设备是传统设备或当前配置为MIDI 1.0。<br> - OH_MIDI_PROTOCOL_2_0：设备支持MIDI 2.0功能。<br>**起始版本：** 24 |
| char deviceName[256] | 设备名称。<br>**起始版本：** 24 |
| uint64_t vendorId | 厂商ID。<br>**起始版本：** 24 |
| uint64_t productId | 产品ID。<br>**起始版本：** 24 |
| char deviceAddress[64] | 设备物理地址（BLE设备）。<br>**起始版本：** 24 |


