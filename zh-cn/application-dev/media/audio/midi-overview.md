# OH_MIDI开发概述(C/C++)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## MIDI简介

MIDI（Musical Instrument Digital Interface，乐器数字接口）是一种用于电子乐器、计算机和其他设备之间进行通信的国际标准协议。它定义了音符、控制信号等音乐数据的传输方式，广泛应用于音乐制作、舞台演出和游戏开发等领域。

### MIDI 1.0 与 MIDI 2.0

- **MIDI 1.0**：1983年发布的经典协议，使用7位分辨率（0-127），单向通信，广泛兼容现有设备。
- **MIDI 2.0**：2020年发布的新一代协议，支持32位高分辨率、双向通信、自动配置（MIDI-CI）等特性。

### UMP统一格式

UMP（Universal MIDI Packet）是MIDI 2.0标准中定义的统一数据包格式，采用32位对齐结构，可同时承载MIDI 1.0和MIDI 2.0协议消息。这种设计使开发者无需关心底层协议差异，统一处理所有MIDI数据。

**协议与数据格式的关系**：可以类比为"信封"和"信的内容语言"。
- **UMP** = 信封格式（统一的32位对齐容器）
- **MIDI 1.0/2.0 协议** = 信的内容语言（传统/现代语义）
- 无论选择哪种协议，数据封装格式（UMP）都是统一的。

从 API version 24 开始，Audio Kit 支持 MIDI（Musical Instrument Digital Interface，乐器数字接口）功能。**OH_MIDI 采用 UMP（Universal MIDI Packet）作为统一的数据交互格式**，使开发者无需关心底层协议差异，在 OpenHarmony 平台上以现代化的方式构建音乐创作、乐器控制和 MIDI 数据处理等应用。

OH_MIDI 支持连接标准 MIDI 1.0 设备，并通过系统服务层自动将传统的 MIDI 1.0 字节流转换为 32 位 UMP 格式，从而简化应用开发。同时，该架构设计在数据格式上兼容 MIDI 2.0 标准，为未来系统内核支持高分辨率 MIDI 设备提供了必要的技术基础。

OH_MIDI 包含客户端、设备、端口和事件四个核心概念，具体介绍如下。

## OH_MIDI客户端 (Client)

客户端是应用使用 MIDI 服务的入口点，所有 MIDI 操作都需要先创建客户端。客户端负责管理与 MIDI 服务的连接，提供设备枚举、设备打开、端口管理等核心功能。

通过 `OH_MIDIClient_Create` 创建客户端后，应用可以获取当前连接的所有 MIDI 设备列表，并通过注册的回调监听设备的热插拔事件（`OH_MIDICallback_OnDeviceChange`）和系统级错误（`OH_MIDICallback_OnError`）。

> **说明**：关闭客户端时，系统会自动关闭该客户端名下打开的所有设备和端口（自动资源回收机制）。但建议应用按相反顺序（端口→设备→客户端）主动释放资源，以保证代码逻辑清晰。

## OH_MIDI设备 (Device)

MIDI 设备是指物理或虚拟的 MIDI 接口设备，包括 USB MIDI 键盘、蓝牙 MIDI 控制器等。每个设备都有唯一的标识符（`midiDeviceId`）用于区分和管理。

设备信息包含设备类型（USB 或蓝牙）、原生协议能力、设备名称、厂商ID、产品ID和设备地址等属性。

* **连接方式**：USB 设备通过 `OH_MIDIClient_OpenDevice` 同步打开，蓝牙 LE 设备则需要通过 `OH_MIDIClient_OpenBLEDevice` 异步连接。
* **原生协议能力**：指示设备当前的通讯协议模式。**在当前版本中，当设备支持多种协议时，系统会优先以 MIDI 1.0 模式与设备通讯，并在 MIDI 服务层将数据封装为 MIDI 2.0 UMP 格式提供给应用。**

## OH_MIDI端口 (Port)

MIDI 端口是设备上的数据传输端点，分为输入端口和输出端口。

* **输入端口 (Input Port)**：用于从设备接收 MIDI 数据。通过 `OH_MIDIDevice_OpenInputPort` 打开并注册 `OH_MIDIDevice_OnReceived` 回调，实现批量消息接收。
* **输出端口 (Output Port)**：用于向设备发送 MIDI 数据。通过 `OH_MIDIDevice_OpenOutputPort` 打开后，使用 `OH_MIDIDevice_Send` 发送 UMP 格式消息。

**数据流向说明**：
* **输入端口 (Input Port)**：设备向应用发送数据，应用通过回调接收
* **输出端口 (Output Port)**：应用向设备发送数据，应用调用 `OH_MIDIDevice_Send` 接口

```
[应用] <--接收-- [输入端口] <-- [设备]
[应用] --发送--> [输出端口] --> [设备]
```

每个设备可以有多个输入和输出端口。每个端口在打开时，可以通过 `OH_MIDIPortDescriptor` 结构配置期望的协议行为：

* **数据转换**：无论底层设备是 MIDI 1.0 还是 2.0，应用层均统一收发 UMP 数据包。
* **协议降级**：如果应用请求发送 MIDI 2.0 高精度消息（UMP Type 4），但底层设备仅支持 MIDI 1.0，OpenHarmony MIDI 服务层会自动将其降级转换为 MIDI 1.0 消息发送。
* **自动转换说明**：系统服务层会在接收方向自动将底层协议数据转换为 UMP 格式供应用处理。但在发送方向，应用需要按照 UMP 规范自行构造 `OH_MIDIEvent` 数据。

## OH_MIDI事件 (Event)

MIDI 事件是 MIDI 数据传输的基本单元。OH_MIDI 强制使用 **UMP (Universal MIDI Packet)** 格式，统一承载 MIDI 1.0 和 MIDI 2.0 数据。

每个事件包含三个核心字段：

* **时间戳 (`timestamp`)**：纳秒级精度。0 表示立即发送。
* **数据长度 (`length`)**：表示 `data` 数组中 32 位字（Word）的数量。
* **UMP 数据指针 (`data`)**：指向 4 字节对齐的 `uint32_t` 数组。

UMP格式通过 **消息类型 (Message Type, MT)** 区分不同消息。MT是UMP数据包的最高4位，决定了消息的功能范围、数据包大小和状态字段大小。

### 常用消息类型

| MT值 | 名称 | 大小 | 说明 |
|------|------|------|------|
| 0x2 | MIDI 1.0 Channel Voice | 32位 | MIDI 1.0通道声音消息，兼容现有设备 |
| 0x4 | MIDI 2.0 Channel Voice | 64位 | MIDI 2.0高分辨率通道声音消息 |

> **开发提示**：大多数应用场景下，开发者主要使用 MT 0x2（MIDI 1.0）和 MT 0x4（MIDI 2.0）通道声音消息。

### 完整消息类型参考

| MT值 | 名称 | 大小 | 说明 |
|------|------|------|------|
| 0x0 | Utility Messages | 32位 | 实用消息，如JR时间戳 |
| 0x1 | System Common & Real-Time | 32位 | 系统公共消息和实时消息 |
| 0x2 | MIDI 1.0 Channel Voice | 32位 | MIDI 1.0通道声音消息，兼容现有设备 |
| 0x3 | Data Messages | 64位 | 数据消息，如SysEx（7位有效载荷） |
| 0x4 | MIDI 2.0 Channel Voice | 64位 | MIDI 2.0高分辨率通道声音消息 |
| 0x5 | Extended Data Messages | 128位 | 扩展数据消息 |
| 0x6-0xD | Reserved | - | 保留供未来使用 |
| 0xE | Flex Data | 128位 | 灵活数据消息，如文本、歌词 |
| 0xF | Stream Messages | 128位 | UMP流消息，如端点发现、功能块配置 |

> **注意**：接收回调中的 `events` 数组及其包含的 `data` 指针仅在回调执行期间有效。应用如需保留 MIDI 数据供后续处理，**必须在回调返回前将数据深拷贝到应用自己的内存中**，以避免访问过期指针导致的未定义行为。

## 术语表

| 术语 | 全称 | 说明 |
|------|------|------|
| UMP | Universal MIDI Packet | 通用MIDI数据包，32位对齐的统一容器格式 |
| MT | Message Type | 消息类型，UMP数据包最高4位，决定消息功能和大小 |
| SysEx | System Exclusive | 系统专有消息，用于厂商自定义数据传输 |
| JR | Jitter Reduction | 抖动消除，网络/蓝牙传输时的时间戳同步机制 |
| Channel Voice | 通道声音消息 | 控制音符、力度、控制器等的核心消息类型 |
| Flex Data | 灵活数据 | MIDI 2.0新增，支持文本、歌词等128位长消息 |
| MIDI-CI | MIDI Capability Inquiry | MIDI能力查询，MIDI 2.0的设备自动配置协议 |

## 约束与限制

- **同时打开的设备数量限制**：单个客户端最多可同时打开16个MIDI设备。超过限制时，OH_MIDIClient_OpenDevice将返回OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES错误。

- **每个设备的端口数量限制**：每个MIDI设备最多可有64个端口（输入+输出总计）。单个客户端最多可同时打开64个端口。超过限制时，OH_MIDIDevice_OpenInputPort或OH_MIDIDevice_OpenOutputPort将返回OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS错误。

- **缓冲区大小限制**：共享内存缓冲区大小为4 KB。发送大量MIDI消息时，如果缓冲区填满，OH_MIDIDevice_Send将返回OH_MIDI_STATUS_WOULD_BLOCK。建议应用批量发送消息，并在收到此错误后延迟10 ms再重试。

- **线程模型和回调执行环境**：所有回调（OH_MIDIDevice_OnReceived、OH_MIDICallback_OnDeviceChange、OH_MIDICallback_OnError）在高优先级系统线程上执行。回调中应避免执行阻塞操作、大量计算或I/O操作，以免影响MIDI系统的实时性能。

- **内存安全**：OH_MIDIDevice_OnReceived回调中的events数组及其包含的数据指针仅在回调期间有效。如需保留数据，必须在回调返回前复制。访问过期指针会导致未定义行为（崩溃、内存损坏）。

- **资源管理顺序**：关闭客户端时会自动关闭所有设备和端口。建议应用按相反顺序关闭资源，以保证代码逻辑清晰：
   1. 关闭所有端口（OH_MIDIDevice_CloseInputPort/OH_MIDIDevice_CloseOutputPort）
   2. 关闭所有设备（OH_MIDIClient_CloseDevice）
   3. 销毁客户端（OH_MIDIClient_Destroy）

   此顺序为推荐做法，用于保证代码逻辑清晰，但系统提供自动资源回收机制确保资源正确释放。

- **设备类型特性差异**：
  - USB MIDI设备：通过USB连接，支持低延迟传输，设备枚举通过系统USB驱动完成
  - 蓝牙MIDI设备：通过蓝牙LE连接，需要ohos.permission.ACCESS_BLUETOOTH权限，使用OH_MIDIClient_OpenBLEDevice异步打开

## 相关参考

- [使用OH_MIDI进行MIDI开发](using-ohmidi.md)
- [OH_MIDI API参考](../../reference/apis-audio-kit/capi-ohmidi.md)
- [MIDI状态码](../../reference/apis-audio-kit/capi-native-midi-base-h.md#oh_midistatuscode)

## 外部资源

- [MIDI Manufacturers Association - MIDI 2.0规范](https://midi.org/midi-2-0-specifications)
- [UMP和MIDI 2.0协议规范 (PDF)](https://amei.or.jp/midistandardcommittee/MIDI2.0/MIDI2.0-DOCS/M2-104-UM_v1-1-1_UMP_and_MIDI_2-0_Protocol_Specification.pdf)
- [Linux Kernel - MIDI 2.0文档](https://www.kernel.org/doc/html/latest/sound/designs/midi-2.0.html)
