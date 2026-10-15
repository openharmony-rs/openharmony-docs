# OHMIDI

## 概述

提供乐器数字接口MIDI（Musical Instrument Digital Interface）模块的C接口定义，用于MIDI设备管理和数据传输。 支持MIDI设备的发现与连接、设备热插拔状态监控、端口能力的查询与开关、UMP（通用MIDI数据包）格式的数据收发等功能， 适用于需要在应用中对接电子乐器、MIDI控制器等外设并进行MIDI数据交互的场景。

**系统能力：** SystemCapability.Multimedia.Audio.MIDI

**起始版本：** 24

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_midi.h](capi-native-midi-h.md) | 声明MIDI相关的接口。MIDI是一种用于电子乐器、计算机和其他设备之间通信的技术标准。 <br> 该文件中的接口用于MIDI设备管理（包括BLE MIDI设备）、MIDI消息发送和接收、设备状态监控等。 <br> 使用OHMIDI连接MIDI设备的典型流程如下： 1. **创建客户端**：初始化MIDI客户端上下文，并注册设备热插拔回调及服务异常回调。 2. **发现设备与端口**：获取当前连接的设备列表，并查询设备的端口能力。 3. **打开设备**：建立设备连接会话。 4. **打开端口**：根据端口方向（输入/输出）分别打开端口。 5. **数据交互**： - **接收**：通过回调函数接收UMP（Universal MIDI Packet）格式的MIDI数据。 - **发送**：构建UMP（Universal MIDI Packet）并通过输出端口发送。 6. **释放资源**：使用完毕后关闭端口、设备并销毁客户端。 |
| [native_midi_base.h](capi-native-midi-base-h.md) | 声明MIDI模块的基础数据结构，定义MIDI接口的基础类型、枚举、结构体和回调函数。MIDI模块提供标准化的MIDI数据通信能力， 支持USB和BLE设备的连接与枚举，基于UMP格式兼容MIDI 1.0和MIDI 2.0协议，适用于音乐演奏数据传输、MIDI设备控制等需要 与外部MIDI硬件交互的场景。 |
