# OH_MIDIEvent

```c
typedef struct OH_MIDIEvent {...} OH_MIDIEvent
```

## 概述

MIDI事件结构体（通用）。事件数据以Universal MIDI Packets（UMP）格式传输。原始字节流（MIDI 1.0）数据需要先转换为UMP格式后再填充此结构体。

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

**所在头文件：** [native_midi_base.h](capi-native-midi-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t timestamp | Timestamp in nanoseconds.Base time obtained via clock_gettime(CLOCK_MONOTONIC, &time)0 indicates "send immediately".<br>**起始版本：** 24 |
| size_t length | Number of 32-bit words in the packet.e.g., 1 for Type 2/4 (64-bit messages use 2 words)<br>**起始版本：** 24 |
| uint32_t *data | Pointer to UMP data (Must be 4-byte aligned).This contains the raw UMP words (uint32_t).<br>**起始版本：** 24 |


