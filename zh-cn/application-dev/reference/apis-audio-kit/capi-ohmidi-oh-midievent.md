# OH_MIDIEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_MIDIEvent
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
| uint64_t timestamp | 时间戳，单位为纳秒。<br> 通过clock_gettime(CLOCK_MONOTONIC, &time)获取基准时间。值为0表示立即发送。<br>**起始版本：** 24 |
| size_t length | UMP数据包中的32位字（word）数量。<br> 例如：Type 1消息占1个字（32位），Type 2消息占2个字（64位）。<br> 此字段表示UMP数据中uint32_t字的数量，而非字节数。<br>**起始版本：** 24 |
| uint32_t *data | 指向UMP数据的指针，包含原始UMP字（uint32_t）。<br> 此指针必须指向4字节对齐的内存地址，以满足UMP规范对32位边界对齐的要求。<br>**起始版本：** 24 |


