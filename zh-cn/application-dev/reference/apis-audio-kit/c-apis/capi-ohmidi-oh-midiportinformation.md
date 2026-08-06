# OH_MIDIPortInformation

```c
typedef struct OH_MIDIPortInformation {...} OH_MIDIPortInformation
```

## 概述

端口信息结构体。用于枚举端口，包含可显示的端口名称。

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

**所在头文件：** [native_midi_base.h](capi-native-midi-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t portIndex | The index of the port.<br>**起始版本：** 24 |
| int64_t deviceId | The ID of the device this port belongs to.<br>**起始版本：** 24 |
| [OH_MIDIPortDirection](capi-native-midi-base-h.md#oh_midiportdirection) direction | Direction of the port (Input/Output).<br>**起始版本：** 24 |
| char name[64] | Name of the port.<br>**起始版本：** 24 |


