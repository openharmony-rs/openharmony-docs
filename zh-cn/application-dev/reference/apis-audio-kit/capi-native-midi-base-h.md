# native_midi_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明MIDI模块的基础数据结构。定义MIDI接口的基础类型、枚举、结构体和回调函数。

**引用文件：** <midi/native_midi_base.h>

**库：** libohmidi.so

**系统能力：** SystemCapability.Multimedia.Audio.MIDI

**起始版本：** 24

**相关模块：** [OH_MIDI](capi-ohmidi.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_MIDIStatusCode](#oh_midistatuscode) | OH_MIDIStatusCode | MIDI状态码枚举。 |
| [OH_MIDIPortDirection](#oh_midiportdirection) | OH_MIDIPortDirection | 端口方向枚举。 |
| [OH_MIDIProtocol](#oh_midiprotocol) | OH_MIDIProtocol | MIDI传输协议语义枚举。 |
| [OH_MIDIDeviceType](#oh_mididevicetype) | OH_MIDIDeviceType | MIDI设备类型枚举。 |
| [OH_MIDIDeviceChangeAction](#oh_mididevicechangeaction) | OH_MIDIDeviceChangeAction | 设备连接状态变化操作枚举。 |

### 结构体

| 名称 | 描述 |
| -- | -- |
| [OH_MIDIEvent](#oh_midievent) | MIDI事件结构体（通用）。 |
| [OH_MIDIDeviceInformation](#oh_midideviceinformation) | 设备信息结构体，用于枚举和显示。 |
| [OH_MIDIPortInformation](#oh_midiportinformation) | 端口信息结构体（详细），用于枚举（包含显示名称）。 |
| [OH_MIDIPortDescriptor](#oh_midiportdescriptor) | 端口描述符结构体。 |
| [OH_MIDICallbacks](#oh_midicallbacks) | 客户端回调结构体。 |

### 回调函数

| 名称 | 描述 |
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](#oh_midicallback_ondevicechange) | 设备连接/断开连接监控回调。 |
| [OH_MIDIDevice_OnReceived](#oh_mididevice_onreceived) | 接收MIDI数据回调（批量处理）。 |
| [OH_MIDICallback_OnError](#oh_midicallback_onerror) | 处理客户端级别错误的回调。 |
| [OH_MIDIClient_OnDeviceOpened](#oh_midiclient_ondeviceopened) | 异步BLE设备连接结果回调。 |

## 枚举类型说明

### OH_MIDIStatusCode

```c
enum OH_MIDIStatusCode
```

**描述**

MIDI状态码枚举。定义MIDI操作的状态码，用于表示操作成功或失败的原因。

**起始版本：** 24

| 枚举项 | 值 | 描述 |
| -- | -- | -- |
| OH_MIDI_STATUS_OK | 0 | 操作成功。 |
| OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT | 35500001 | 无效参数（例如：空指针）。<br><br>**可能原因**：<br>- 指针参数为NULL（客户端、设备、端口或数据缓冲区）<br>- 端口索引超出设备实际端口数量范围<br>- 枚举值不在有效范围内<br><br>**处理步骤**：<br>1. 检查所有指针参数是否为NULL<br>2. 使用OH_MIDIClient_GetPortCount验证端口索引范围<br>3. 参考API文档确认枚举值有效性 |
| OH_MIDI_STATUS_GENERIC_IPC_FAILURE | 35500002 | IPC通信失败。<br><br>**可能原因**：<br>- MIDI系统服务异常终止或重启<br>- 底层Binder通信机制出现临时故障<br>- 系统资源不足导致IPC服务响应超时<br><br>**处理步骤**：<br>1. 销毁并重新创建客户端建立新连接<br>2. 查看系统日志定位服务侧问题 |
| OH_MIDI_STATUS_INVALID_CLIENT | 35500003 | 无效的客户端句柄。<br><br>**可能原因**：<br>- 使用已通过OH_MIDIClient_Destroy销毁的客户端句柄<br>- 客户端创建失败但仍继续使用该句柄<br><br>**处理步骤**：<br>1. 检查OH_MIDIClient_Create返回值确保创建成功<br>2. 使用标志位管理客户端生命周期，避免使用已销毁句柄 |
| OH_MIDI_STATUS_INVALID_DEVICE_HANDLE | 35500004 | 无效的设备句柄。<br><br>**可能原因**：<br>- 使用已通过OH_MIDIClient_CloseDevice关闭的设备句柄<br>- 设备打开失败但继续使用该句柄<br>- 客户端销毁后使用其关联的设备句柄<br><br>**处理步骤**：<br>1. 检查设备打开回调的opened参数确认打开成功<br>2. 确保客户端生命周期有效，设备依赖客户端存在 |
| OH_MIDI_STATUS_INVALID_PORT | 35500005 | 无效的端口索引。<br><br>**可能原因**：<br>- 端口索引小于0或大于等于设备实际端口数量<br>- 端口方向与实际端口类型不匹配<br>- 设备已断开导致原有效索引失效<br><br>**处理步骤**：<br>1. 使用OH_MIDIClient_GetPortCount获取端口总数验证索引<br>2. 使用OH_MIDIClient_GetPortInfos确认端口方向<br>3. 监听设备断开事件，清理失效端口索引 |
| OH_MIDI_STATUS_WOULD_BLOCK | 35500006 | 发送缓冲区暂时已满。表示共享内存缓冲区当前缺乏空间。当消息无法放入缓冲区时由非阻塞发送返回。<br><br>**可能原因**：<br>- 发送速度过快超过缓冲区处理能力<br>- MIDI消息过大超出剩余空间<br>- 系统负载较高缓冲区数据未及时消费<br><br>**处理步骤**：<br>1. 等待约10ms后重试发送<br>2. 降低发送频率控制速率<br>3. 将多个小消息合并为一次批量发送 |
| OH_MIDI_STATUS_TIMEOUT | 35500007 | 操作无法在合理时间内完成。<br><br>**可能原因**：<br>- MIDI设备响应缓慢或无响应<br>- 底层传输链路出现延迟或阻塞<br><br>**处理步骤**：<br>1. 使用OH_MIDIDevice_FlushOutputPort刷新端口缓冲区<br>2. 检查设备物理连接状态<br>3. 实现指数退避重试机制<br>4. 关闭并重新打开设备重置通信状态 |
| OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES | 35500008 | 客户端已达到允许打开的最大设备数量（16个）。要打开新设备，必须先关闭现有设备。<br><br>**可能原因**：<br>- 应用程序打开过多MIDI设备超过系统配额<br>- 设备未正确关闭导致资源泄漏<br><br>**处理步骤**：<br>1. 遍历已打开设备确认哪些仍在使用<br>2. 使用OH_MIDIClient_CloseDevice关闭闲置设备<br>3. 采用LRU策略管理设备资源 |
| OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS | 35500009 | 客户端已达到允许打开的最大端口数量（64个）。要打开新端口，必须先关闭现有端口。<br><br>**可能原因**：<br>- 应用程序打开过多MIDI端口超过系统配额<br>- 端口未正确关闭导致资源泄漏<br><br>**处理步骤**：<br>1. 遍历已打开端口确认哪些仍在使用<br>2. 使用OH_MIDIDevice_CloseInputPort/CloseOutputPort关闭闲置端口<br>3. 按优先级或使用频率制定端口使用计划 |
| OH_MIDI_STATUS_DEVICE_ALREADY_OPEN | 35500010 | 客户端已经打开此设备。同一设备在同一客户端中不允许重复打开。<br><br>**可能原因**：<br>- 对同一设备多次调用打开接口<br>- 设备打开状态管理逻辑存在错误<br><br>**处理步骤**：<br>1. 维护已打开设备列表，打开前查询是否已存在<br>2. 使用设备ID为键的映射管理已打开句柄<br>3. 关闭设备时及时更新状态 |
| OH_MIDI_STATUS_PORT_ALREADY_OPEN | 35500011 | 客户端已经打开此端口。同一端口在同一客户端中不允许重复打开。<br><br>**可能原因**：<br>- 对同一端口多次调用打开接口<br>- 端口打开状态管理逻辑存在错误<br><br>**处理步骤**：<br>1. 维护已打开端口列表，打开前查询是否已存在<br>2. 使用设备ID+端口索引组合键管理已打开句柄<br>3. 关闭端口时及时更新状态 |
| OH_MIDI_STATUS_TOO_MANY_CLIENTS | 35500012 | 系统级（8个）或应用级（2个/UID）客户端数量已达上限。<br><br>**可能原因**：<br>- 系统整体达到允许的客户端数量上限<br>- 当前应用UID达到最大客户端数量<br><br>**处理步骤**：<br>1. 审查代码确保不使用时立即销毁客户端<br>2. 采用"单客户端多设备"架构减少客户端数量<br>3. 关闭闲置的客户端释放配额 |
| OH_MIDI_STATUS_PERMISSION_DENIED | 35500013 | 权限被拒绝。应用未声明或未获得所需权限（如蓝牙权限）。<br><br>**可能原因**：<br>- module.json5未声明ohos.permission.ACCESS_BLUETOOTH<br>- 用户拒绝了权限请求<br>- 应用权限被系统或用户撤销<br><br>**处理步骤**：<br>1. 在module.json5中正确声明权限<br>2. 在操作前检查并请求运行时权限<br>3. 提供USB MIDI设备作为备选方案（无需额外权限） |
| OH_MIDI_STATUS_SERVICE_DIED | 35500014 | MIDI系统服务已崩溃或断开连接。必须销毁并重新创建客户端。<br><br>**可能原因**：<br>- MIDI服务崩溃<br>- MIDI服务被系统或用户强制终止<br><br>**处理步骤**：<br>1. 通过OH_MIDICallback_OnError监听此错误<br>2. 销毁现有客户端及所有句柄<br>3. 等待服务恢复后重新创建客户端<br>4. 重新执行设备枚举、设备打开和端口打开 |
| OH_MIDI_STATUS_SYSTEM_ERROR | 35500100 | 系统内部错误。表示发生了未预期的系统级错误。<br><br>**可能原因**：<br>- 系统资源严重不足（如内存耗尽）<br>- 底层音频或MIDI框架出现异常<br>- 系统服务间协调失败<br><br>**处理步骤**：<br>1. 记录详细错误日志包括操作类型和参数<br>2. 释放并重新初始化所有资源<br>3. 检查系统资源状态关闭不必要应用<br>4. 持续发生时向系统开发者报告问题 |

---

### OH_MIDIPortDirection

```c
enum OH_MIDIPortDirection
```

**描述**

端口方向枚举。定义MIDI端口的数据传输方向。

**起始版本：** 24

| 枚举项 | 值 | 描述 |
| -- | -- | -- |
| OH_MIDI_PORT_DIRECTION_INPUT | 0 | 输入端口（设备 -> 主机）。 |
| OH_MIDI_PORT_DIRECTION_OUTPUT | 1 | 输出端口（主机 -> 设备）。 |

---

### OH_MIDIProtocol

```c
enum OH_MIDIProtocol
```

**描述**

MIDI传输协议语义枚举。

> **说明**
>
> **重要**：SDK始终使用UMP（Universal MIDI Packet）格式进行数据传输，无论选择何种协议。此枚举定义连接的**协议语义**（Protocol Semantics），影响消息的行为特征和数据处理方式，而不是数据结构本身。

**协议与数据格式的关系**：
- **UMP** 是统一的数据封装格式（32位对齐的数据包容器）
- **MIDI 1.0/2.0 协议** 定义消息的语义、分辨率和通信行为
- 选择协议仅影响消息的"行为模式"，数据格式始终是UMP

**类比说明**：
- 数据格式（UMP）= 信封的标准格式
- 协议（MIDI 1.0/2.0）= 信的内容语言
- 无论用哪种语言写信，信封格式都是统一的

**实际影响**：
- 选择 `OH_MIDI_PROTOCOL_1_0`：服务期望接收MIDI 1.0语义的UMP包，如需要会自动转换发送给设备
- 选择 `OH_MIDI_PROTOCOL_2_0`：服务期望接收MIDI 2.0语义的UMP包，支持高分辨率数据，如设备不支持则自动降级

**起始版本：** 24

| 枚举项 | 值 | 核心特性 | 自动转换策略 |
| -- | -- | -- | -- |
| OH_MIDI_PROTOCOL_1_0 | 1 | 传统MIDI 1.0语义，广泛兼容 | MIDI 1.0设备：UMP转字节流；MIDI 2.0设备：直接发送 |
| OH_MIDI_PROTOCOL_2_0 | 2 | MIDI 2.0语义，高分辨率 | 自动降级转换，可能丢失精度 |

**详细行为说明**

**OH_MIDI_PROTOCOL_1_0**：
- 服务期望严格兼容MIDI 1.0的UMP包。
- 支持的消息类型：MT 0x0（实用消息）、MT 0x1（系统消息）、MT 0x2（通道声音，32位）、MT 0x3（SysEx数据，64位）。
- 如果目标硬件是MIDI 1.0：服务将UMP转换回字节流（F0...F7）。
- 如果目标硬件是MIDI 2.0：服务直接发送未经转换的UMP包。

**OH_MIDI_PROTOCOL_2_0**：
- 服务期望利用MIDI 2.0功能的UMP包。
- 支持的消息类型：MT 0x4（通道声音，64位高分辨率）、MT 0x0（JR时间戳）、MT 0xD（Flex数据，128位）、MT 0xF（UMP流消息）、MT 0x3/0x5（数据消息）。
- **回退策略**：如果请求此协议但硬件仅支持MIDI 1.0，服务会尝试自动降级转换，可能会丢失数据精度或某些消息类型（例如：将32位力度降级为7位，将Type 4转换回Type 2）。

---

### OH_MIDIDeviceType

```c
enum OH_MIDIDeviceType
```

**描述**

MIDI设备类型枚举。定义MIDI设备的连接类型。

**起始版本：** 24

| 枚举项 | 值 | 描述 |
| -- | -- | -- |
| OH_MIDI_DEVICE_TYPE_USB | 0 | USB MIDI设备。 |
| OH_MIDI_DEVICE_TYPE_BLE | 1 | 蓝牙LE MIDI设备。 |

---

### OH_MIDIDeviceChangeAction

```c
enum OH_MIDIDeviceChangeAction
```

**描述**

设备连接状态变化操作枚举。用于标识设备的连接和断开事件。

**起始版本：** 24

| 枚举项 | 值 | 描述 |
| -- | -- | -- |
| OH_MIDI_DEVICE_CHANGE_ACTION_CONNECTED | 0 | 设备已连接。 |
| OH_MIDI_DEVICE_CHANGE_ACTION_DISCONNECTED | 1 | 设备已断开。 |

## 结构体类型说明

### OH_MIDIEvent

```c
struct OH_MIDIEvent
```

**描述**

MIDI事件结构体（通用）。设计用于处理原始字节流（MIDI 1.0）和UMP。

**起始版本：** 24

| 成员 | 类型 | 描述 |
| -- | -- | -- |
| timestamp | uint64_t | 时间戳（纳秒）。通过clock_gettime(CLOCK_MONOTONIC, &time)获取基准时间。0表示"立即发送"。 |
| length | size_t | 数据包中的32位字数。例如：Type 2/4为1（64位消息使用2个字）。 |
| data | uint32_t * | 指向UMP数据的指针（必须4字节对齐）。包含原始UMP字（uint32_t）。 |

---

### OH_MIDIDeviceInformation

```c
struct OH_MIDIDeviceInformation
```

**描述**

设备信息结构体，包含设备的唯一标识、类型、协议、设备名称、厂商ID和产品ID等信息。

用于枚举可用设备并在用户界面中显示设备信息。

**起始版本：** 24

| 成员 | 类型 | 描述 |
| -- | -- | -- |
| midiDeviceId | int64_t | MIDI设备的唯一标识符。 |
| deviceType | OH_MIDIDeviceType | MIDI设备类型（USB或BLE）。 |
| nativeProtocol | OH_MIDIProtocol | 设备原生支持的MIDI协议（MIDI 1.0或MIDI 2.0）。 |
| deviceName | char[256] | 设备名称。 |
| vendorId | uint64_t | 厂商ID。 |
| productId | uint64_t | 产品ID。 |
| deviceAddress | char[64] | 设备物理地址（BLE设备）。 |

---

### OH_MIDIPortInformation

```c
struct OH_MIDIPortInformation
```

**描述**

端口信息结构体，包含端口的索引、所属设备ID、方向和名称等信息。

用于枚举端口，包含可在用户界面中显示的端口名称。

**起始版本：** 24

| 成员 | 类型 | 描述 |
| -- | -- | -- |
| portIndex | uint32_t | 端口在设备中的索引号。 |
| deviceId | int64_t | 端口所属的MIDI设备ID。 |
| direction | OH_MIDIPortDirection | 端口方向（输入或输出）。 |
| name | char[64] | 端口名称。 |

---

### OH_MIDIPortDescriptor

```c
struct OH_MIDIPortDescriptor
```

**描述**

端口描述符结构体，用于打开端口时指定端口索引和协议行为（即服务在应用和硬件之间进行数据转换的规则）。

**起始版本：** 24

| 成员 | 类型 | 描述 |
| -- | -- | -- |
| portIndex | uint32_t | 要打开的端口索引号。 |
| protocol | OH_MIDIProtocol | 指定要使用的MIDI协议版本（MIDI 1.0或MIDI 2.0）。服务会根据此字段在应用和硬件之间转换数据。 |

---

### OH_MIDICallbacks

```c
struct OH_MIDICallbacks
```

**描述**

客户端回调结构体，包含设备变化和错误处理的回调函数。

**起始版本：** 24

| 成员 | 类型 | 描述 |
| -- | -- | -- |
| onDeviceChange | OH_MIDICallback_OnDeviceChange | 设备连接状态变化回调函数指针。 |
| onError | OH_MIDICallback_OnError | 错误发生回调函数指针。 |

## 回调函数说明

### OH_MIDICallback_OnDeviceChange

```c
typedef void (*OH_MIDICallback_OnDeviceChange) (void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo)
```

**描述**

设备连接或断开连接时触发回调。

**参数**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 客户端创建期间提供的用户自定义数据指针。 |
| OH_MIDIDeviceChangeAction action | 设备变化操作（已连接/已断开）。 |
| OH_MIDIDeviceInformation deviceInfo | 变化设备的信息。 |

**起始版本：** 24

---

### OH_MIDIDevice_OnReceived

```c
typedef void (*OH_MIDIDevice_OnReceived) (void *userData, const OH_MIDIEvent *events, size_t eventCount)
```

**描述**

接收MIDI数据回调（一次处理多个事件）。

> **警告**
>
> 'events'数组及其中所有数据指针是**临时的，仅在此回调期间有效**。在回调返回后访问这些指针会导致**未定义行为**（崩溃、内存损坏）。调用方必须复制任何需要保留的数据。

此回调在高优先级系统线程上调用。应避免执行阻塞操作、大量计算或I/O操作。

**参数**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 打开端口期间提供的用户自定义数据指针。 |
| const OH_MIDIEvent *events | 指向接收到的MIDI事件数组的指针。 |
| size_t eventCount | 数组中的事件数。 |

**起始版本：** 24

---

### OH_MIDICallback_OnError

```c
typedef void (*OH_MIDICallback_OnError) (void *userData, OH_MIDIStatusCode code)
```

**描述**

处理客户端级别错误的函数。当MIDI服务发生关键错误（如服务崩溃）时调用。

**参数**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 客户端创建时提供的用户自定义数据指针。 |
| OH_MIDIStatusCode code | 错误状态码，指示错误类型。 |

**起始版本：** 24

---

### OH_MIDIClient_OnDeviceOpened

```c
typedef void (*OH_MIDIClient_OnDeviceOpened) (void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)
```

**描述**

异步BLE设备连接结果回调函数。当BLE MIDI设备连接尝试完成后调用。

**参数**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 调用OH_MIDIClient_OpenBleDevice时传入的用户自定义数据指针。 |
| bool opened | 连接是否成功。true表示已连接且device句柄有效，false表示连接失败且device为NULL。 |
| OH_MIDIDevice *device | 连接操作的结果句柄。如果opened为true，此参数为有效的设备句柄，应用必须在不再需要时调用OH_MIDIClient_CloseDevice关闭它；如果opened为false，此参数为NULL。 |
| OH_MIDIDeviceInformation info | 已连接设备的信息。 |

**起始版本：** 24
