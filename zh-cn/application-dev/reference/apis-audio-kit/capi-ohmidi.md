# OH_MIDI
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

提供MIDI（Musical Instrument Digital Interface）模块的C接口定义，用于MIDI设备管理和数据传输。

**系统能力：** SystemCapability.Multimedia.Audio.MIDI

**起始版本：** 24

**引用文件：** <midi/native_midi.h>

**库：** libohmidi.so

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | 声明MIDI相关的接口，包括客户端管理、设备管理、端口管理和数据传输。 |
| [native_midi_base.h](capi-native-midi-base-h.md) | 声明MIDI基础数据结构，包括枚举类型、结构体和回调定义。 |

## 使用说明

### 线程安全

**接口线程安全性**

以下接口是线程安全的：
- OH_MIDIDevice_Send：支持多个线程同时调用
- OH_MIDIDevice_SendSysEx：支持多个线程同时调用
- OH_MIDIDevice_FlushOutputPort：支持多个线程同时调用

其他接口（如OH_MIDIClient_OpenDevice、OH_MIDIClient_CloseDevice等）不是线程安全的，需要开发者自行保证同步。

**回调执行环境**

所有回调函数在独立的系统线程上执行：
- **OH_MIDICallback_OnDeviceChange**：在高优先级系统线程上执行
- **OH_MIDIDevice_OnReceived**：在高优先级系统线程上执行
- **OH_MIDICallback_OnError**：在高优先级系统线程上执行

**线程安全注意事项**

在回调中：
1. 避免执行阻塞操作、大量计算或I/O操作，以免影响MIDI系统的实时性能。
2. 如需保留回调中的events数据，必须在回调返回前复制，因为该数据仅在回调期间有效。
3. 访问共享资源时，必须使用互斥锁等同步机制保证线程安全。

### 约束与限制

**资源数量限制**

- **打开设备数量限制**：单个客户端最多可同时打开16个MIDI设备。超过限制时，OH_MIDIClient_OpenDevice将返回OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES错误。

- **打开端口数量限制**：每个MIDI设备最多可有64个端口（输入+输出总计）。单个客户端最多可同时打开64个端口。超过限制时，OH_MIDIDevice_OpenInputPort或OH_MIDIDevice_OpenOutputPort将返回OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS错误。

**缓冲区大小限制**

共享内存缓冲区大小为4KB。发送大量MIDI消息时，如果缓冲区填满，OH_MIDIDevice_Send将返回OH_MIDI_STATUS_WOULD_BLOCK。建议应用批量发送消息，并在收到此错误后延迟10ms再重试。

**内存安全限制**

> **警告**
>
> `OH_MIDIDevice_OnReceived`回调中的`events`数组及其包含的数据指针仅在回调期间有效。如需保留数据，必须在回调返回前复制。
>
> **后果**：访问过期指针会导致未定义行为（崩溃、内存损坏）。

**资源管理顺序**

关闭客户端时会自动关闭所有设备和端口。建议应用按相反顺序关闭资源，以保证代码逻辑清晰：
1. 关闭所有端口（OH_MIDIDevice_CloseInputPort/OH_MIDIDevice_CloseOutputPort）
2. 关闭所有设备（OH_MIDIClient_CloseDevice）
3. 销毁客户端（OH_MIDIClient_Destroy）

此顺序为推荐做法，用于保证代码逻辑清晰，但系统提供自动资源回收机制确保资源正确释放。

## 相关参考

- [native_midi_base.h](capi-native-midi-base-h.md)：包含OH_MIDIStatusCode状态码枚举及详细错误处理说明
