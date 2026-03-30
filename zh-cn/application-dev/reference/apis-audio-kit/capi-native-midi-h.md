# native_midi.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明MIDI相关的接口。该文件中的接口用于MIDI设备管理、MIDI消息发送和接收、设备状态监控等。

**引用文件：** <midi/native_midi.h>

**库：** libohmidi.so

**系统能力：** SystemCapability.Multimedia.Audio.MIDI

**起始版本：** 24

**相关模块：** [OH_MIDI](capi-ohmidi.md)

## 类型说明

### OH_MIDIClient

```c
typedef struct OH_MIDIClient OH_MIDIClient
```

**描述**

MIDI客户端句柄。表示与MIDI系统服务的连接，是所有MIDI操作的主入口点。

客户端通过 [OH_MIDIClient_Create](#oh_midiclient_create) 创建，通过 [OH_MIDIClient_Destroy](#oh_midiclient_destroy) 销毁。

**起始版本：** 24

---

### OH_MIDIDevice

```c
typedef struct OH_MIDIDevice OH_MIDIDevice
```

**描述**

MIDI设备句柄。表示一个已打开的MIDI设备，用于端口操作和数据传输。

设备通过 [OH_MIDIClient_OpenDevice](#oh_midiclient_opendevice) 打开，通过 [OH_MIDIClient_CloseDevice](#oh_midiclient_closedevice) 关闭。

**起始版本：** 24

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_MIDIClient_Create](#oh_midiclient_create) | 创建MIDI客户端实例。 |
| [OH_MIDIClient_Destroy](#oh_midiclient_destroy) | 销毁MIDI客户端并释放资源。 |
| [OH_MIDIClient_GetDeviceCount](#oh_midiclient_getdevicecount) | 获取连接的MIDI设备数量。 |
| [OH_MIDIClient_GetDeviceInfos](#oh_midiclient_getdeviceinfos) | 获取连接的MIDI设备信息。 |
| [OH_MIDIClient_OpenDevice](#oh_midiclient_opendevice) | 打开MIDI设备。 |
| [OH_MIDIClient_OpenBLEDevice](#oh_midiclient_openbledevice) | 异步打开蓝牙MIDI设备。 |
| [OH_MIDIClient_CloseDevice](#oh_midiclient_closedevice) | 关闭MIDI设备。 |
| [OH_MIDIClient_GetPortCount](#oh_midiclient_getportcount) | 获取指定MIDI设备的端口数量。 |
| [OH_MIDIClient_GetPortInfos](#oh_midiclient_getportinfos) | 获取指定MIDI设备的端口信息。 |
| [OH_MIDIDevice_OpenInputPort](#oh_mididevice_openinputport) | 打开MIDI输入端口（接收数据）。 |
| [OH_MIDIDevice_OpenOutputPort](#oh_mididevice_openoutputport) | 打开MIDI输出端口（发送数据）。 |
| [OH_MIDIDevice_CloseInputPort](#oh_mididevice_closeinputport) | 关闭MIDI输入端口。 |
| [OH_MIDIDevice_CloseOutputPort](#oh_mididevice_closeoutputport) | 关闭MIDI输出端口。 |
| [OH_MIDIDevice_Send](#oh_mididevice_send) | 发送MIDI消息（批量、非阻塞、原子操作）。 |
| [OH_MIDIDevice_SendSysEx](#oh_mididevice_sendsysex) | 发送大型系统专有消息（SysEx）。 |
| [OH_MIDIDevice_FlushOutputPort](#oh_mididevice_flushoutputport) | 清空输出缓冲区中的待发送消息。 |

## 函数说明

### OH_MIDIClient_Create

```c
OH_MIDIStatusCode OH_MIDIClient_Create (OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)
```

**描述**

创建MIDI客户端实例。客户端是使用MIDI服务的入口，所有MIDI操作都需要先创建客户端。

> **说明**
>
> **资源管理与最佳实践**：

MIDI 是对低延迟有严格要求的系统服务（典型延迟要求<10ms）。为确保实时性能（QoS）和系统稳定性，服务强制执行以下限制：

1. **系统级限制**：全局允许的活动 MIDI 客户端最大数量为8个
2. **每应用限制**：每个 App UID 允许的 MIDI 客户端最大数量为2个

建议应用在其整个生命周期内维护单个MIDI客户端实例，并使用它管理多个设备/端口。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient **client | 指向用于接收新客户端句柄的指针。 |
| [OH_MIDICallbacks](capi-native-midi-base-h.md#oh_midicallbacks) callbacks | 用于系统事件的回调结构体。 |
| void *userData | 传递给回调函数的用户自定义数据指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | client参数为nullptr。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |
| [OH_MIDI_STATUS_TOO_MANY_CLIENTS](capi-native-midi-base-h.md#oh_midistatuscode) | 因资源限制创建失败。当调用应用超出其每UID配额或系统全局客户端数量已达上限时发生。 |

**起始版本：** 24

**相关接口**

[OH_MIDIClient_Destroy](#oh_midiclient_destroy)

---

### OH_MIDIClient_Destroy

```c
OH_MIDIStatusCode OH_MIDIClient_Destroy (OH_MIDIClient *client)
```

**描述**

销毁MIDI客户端并释放资源。

销毁客户端时会自动关闭所有通过此客户端打开的设备和端口。应用在销毁前应当先关闭设备和端口，以保证代码逻辑清晰：

   1. 关闭所有设备的端口（[OH_MIDIDevice_CloseInputPort](#oh_mididevice_closeinputport)/[OH_MIDIDevice_CloseOutputPort](#oh_mididevice_closeoutputport)）
   2. 关闭所有设备（[OH_MIDIClient_CloseDevice](#oh_midiclient_closedevice)）
   3. 销毁客户端（[OH_MIDIClient_Destroy](#oh_midiclient_destroy)）

此顺序作为最佳实践，用于保证代码逻辑清晰，但系统提供自动资源回收机制确保资源正确释放。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](#oh_midiclient) *client | 目标客户端句柄。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄为NULL或无效。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

**相关接口**

[OH_MIDIClient_Create](#oh_midiclient_create)

---

### OH_MIDIClient_GetDeviceCount

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount (const OH_MIDIClient *client, size_t *count)
```

**描述**

获取连接的MIDI设备数量。

此函数用于确定存储设备信息所需的缓冲区大小。

> **注意**：如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不会包含在设备数量中。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](#oh_midiclient) *client | MIDI客户端句柄。 |
| size_t *count | 指向用于接收设备数量的指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | count参数为nullptr。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIClient_GetDeviceInfos

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos (const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualNumDevices)
```

**描述**

获取连接的MIDI设备信息。

将设备信息写入`infos`参数指定的缓冲区。缓冲区大小应基于[OH_MIDIClient_GetDeviceCount](#oh_midiclient_getdevicecount)返回的数量进行分配。

> **注意**：如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不会包含在返回的设备信息中。

> **说明**
>
> 竞态条件处理：
- 如果在调用[OH_MIDIClient_GetDeviceCount](#oh_midiclient_getdevicecount)和此函数之间设备数量增加，此函数最多将`capacity`个设备信息写入输出数组，`actualNumDevices`设置为`capacity`。
- 如果设备数量减少，则填充当前剩余的可用设备数量。
- 始终检查`actualNumDevices`以获取实际写入的设备数量。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient *client | MIDI客户端句柄。 |
| [OH_MIDIDeviceInformation](capi-native-midi-base-h.md#oh_midideviceinformation) *infos | 用户分配的缓冲区，用于存储设备信息。 |
| size_t capacity | 'infos'缓冲区可容纳的最大元素数量。 |
| size_t *actualNumDevices | 指向用于接收实际写入'infos'缓冲区的设备数量的指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | infos或actualNumDevices参数为nullptr。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIClient_OpenDevice

```c
OH_MIDIStatusCode OH_MIDIClient_OpenDevice (OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)
```

**描述**

打开指定ID的MIDI设备。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient *client | 目标客户端句柄。 |
| int64_t deviceId | 设备的唯一标识符，由[OH_MIDIClient_GetDeviceInfos](#oh_midiclient_getdeviceinfos)获取。 |
| [OH_MIDIDevice](#oh_mididevice) **device | 指向用于接收设备句柄的指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_DEVICE_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) | 设备已被当前客户端打开。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | device参数为nullptr，或deviceId不存在。 |
| [OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端已达到最大打开设备数量限制。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIClient_OpenBLEDevice

```c
OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice (OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)
```

**描述**

异步打开蓝牙LE MIDI设备。

此函数立即返回，而连接结果（成功或失败）将在BLE连接过程完成后通过提供的回调异步传递。

**权限**

ohos.permission.ACCESS_BLUETOOTH

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient *client | 目标客户端句柄。 |
| const char *deviceAddr | BLE设备的MAC地址（例如："AA:BB:CC:DD:EE:FF"）。 |
| [OH_MIDIClient_OnDeviceOpened](capi-native-midi-base-h.md#oh_midiclient_ondeviceopened) callback | 连接过程完成时要调用的回调函数。 |
| void *userData | 传递给回调的用户自定义数据指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 连接请求已成功分发。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | deviceAddr或callback参数为nullptr。 |
| [OH_MIDI_STATUS_PERMISSION_DENIED](capi-native-midi-base-h.md#oh_midistatuscode) | 权限被拒绝。应用未声明或未获得所需权限（如`ohos.permission.ACCESS_BLUETOOTH`）。 |
| [OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端已达到最大打开设备数量限制。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 服务无法访问。 |

> **说明**
>
> - 此函数会触发BLE扫描和连接过程，通常需要几秒钟的时间。
- 确保应用具有必要的蓝牙权限。
- 如果蓝牙权限被拒绝，回调将以opened=false和device=NULL被调用。应用应检查opened参数后再尝试使用设备句柄。

**起始版本：** 24

---

### OH_MIDIClient_CloseDevice

```c
OH_MIDIStatusCode OH_MIDIClient_CloseDevice (OH_MIDIClient *client, OH_MIDIDevice *device)
```

**描述**

关闭MIDI设备。

关闭设备时会同时关闭该设备上所有已打开的端口。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient *client | 目标客户端句柄。 |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIClient_GetPortCount

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortCount (const OH_MIDIClient *client, int64_t deviceId, size_t *count)
```

**描述**

获取指定MIDI设备的端口数量。

此函数用于确定存储端口信息所需的缓冲区大小。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](#oh_midiclient) *client | MIDI客户端句柄。 |
| int64_t deviceId | 目标设备ID。 |
| size_t *count | 指向用于接收端口数量的指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | count参数无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | deviceId参数无效。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIClient_GetPortInfos

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortInfos (const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualNumPorts)
```

**描述**

获取指定MIDI设备的端口信息。

将端口信息写入由调用者分配的缓冲区。

> **说明**
>
> 竞态条件处理：
- 如果在调用[OH_MIDIClient_GetPortCount](#oh_midiclient_getportcount)和此函数之间端口数量增加，此函数最多填充'capacity'个端口，'actualNumPorts'设置为'capacity'。
- 如果端口数量减少，则填充实际可用的端口信息。
- 始终检查'actualNumPorts'以获取实际可用的端口数量。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIClient *client | MIDI客户端句柄。 |
| int64_t deviceId | 目标设备ID。 |
| [OH_MIDIPortInformation](capi-native-midi-base-h.md#oh_midiportinformation) *infos | 用户分配的缓冲区，用于存储端口信息。 |
| size_t capacity | 'infos'缓冲区可容纳的最大元素数量。 |
| size_t *actualNumPorts | 指向用于接收实际写入缓冲区的端口数量的指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) | 客户端句柄无效。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | infos或actualNumPorts参数为nullptr。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | deviceId参数无效。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIDevice_OpenInputPort

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort (OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)
```

**描述**

打开MIDI输入端口（接收数据）。

注册回调函数以接收MIDI数据流。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIDevice *device | 目标设备句柄。 |
| [OH_MIDIPortDescriptor](capi-native-midi-base-h.md#oh_midiportdescriptor) descriptor | 端口索引和协议配置。 |
| [OH_MIDIDevice_OnReceived](capi-native-midi-base-h.md#oh_mididevice_onreceived) callback | 有数据可用时调用的回调函数。 |
| void *userData | 传递给回调的用户自定义数据指针。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效或不是输入端口。 |
| [OH_MIDI_STATUS_PORT_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) | 端口已被此客户端打开。 |
| [OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS](capi-native-midi-base-h.md#oh_midistatuscode) | 已达到最大打开端口数量限制。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | callback参数为nullptr。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIDevice_OpenOutputPort

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort (OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)
```

**描述**

打开MIDI输出端口（发送MIDI数据）。

**参数**

| 参数项 | 描述 |
| -- | -- |
| OH_MIDIDevice *device | 目标设备句柄。 |
| [OH_MIDIPortDescriptor](capi-native-midi-base-h.md#oh_midiportdescriptor) descriptor | 端口索引和协议配置。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效或不是输出端口。 |
| [OH_MIDI_STATUS_PORT_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) | 端口已被此客户端打开。 |
| [OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS](capi-native-midi-base-h.md#oh_midistatuscode) | 已达到最大打开端口数量限制。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIDevice_CloseInputPort

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort (OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

关闭MIDI输入端口。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |
| uint32_t portIndex | 要关闭的输入端口索引。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效，或未打开。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

**相关接口**

[OH_MIDIDevice_OpenInputPort](#oh_mididevice_openinputport)

---

### OH_MIDIDevice_CloseOutputPort

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort (OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

关闭MIDI输出端口。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |
| uint32_t portIndex | 要关闭的输出端口索引。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效，或不是打开的输出端口。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

**相关接口**

[OH_MIDIDevice_OpenOutputPort](#oh_mididevice_openoutputport)

---

### OH_MIDIDevice_Send

```c
OH_MIDIStatusCode OH_MIDIDevice_Send (OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)
```

**描述**

发送MIDI消息（批量、非阻塞、原子操作）。

将MIDI事件数组写入共享内存缓冲区。

- 原子性：数组中的每个事件都被原子性处理。要么完全写入，要么完全不写入。
- 部分成功：如果缓冲区在中间变满，函数返回[OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode)并将eventsWritten设置为成功入队的事件数。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |
| uint32_t portIndex | 目标端口索引。 |
| [OH_MIDIEvent](capi-native-midi-base-h.md#oh_midievent) *events | 指向要发送的事件数组的指针。 |
| uint32_t eventCount | 数组中的事件数量。 |
| uint32_t *eventsWritten | 返回成功消耗的事件数量。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 所有数据均已成功处理并写入。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效，或未打开。 |
| [OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode) | 缓冲区已满（检查eventsWritten）。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | 参数无效。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24

---

### OH_MIDIDevice_SendSysEx

```c
OH_MIDIStatusCode OH_MIDIDevice_SendSysEx (OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)
```

**描述**

发送超过标准MIDI消息长度的SysEx消息，自动处理拆包和阻塞等待。

这是一个实用函数，适用于将SysEx作为原始字节流（MIDI 1.0风格，F0...F7）处理的应用。它同时适用于[OH_MIDI_PROTOCOL_1_0](capi-native-midi-base-h.md#oh_midiprotocol)和[OH_MIDI_PROTOCOL_2_0](capi-native-midi-base-h.md#oh_midiprotocol)会话。操作系统MIDI服务会自动将数据转换为设备端口所需的格式（UMP格式或原始字节流）。

工作原理：

1. 将原始字节流自动碎片化为多个Universal MIDI Packet（UMP）Type 3（64位数据消息）包
2. 使用[OH_MIDIDevice_Send](#oh_mididevice_send)按顺序发送这些包

> **警告**：此函数执行循环写入，当缓冲区填满时将阻塞并重试，直至写入完整。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |
| uint32_t portIndex | 目标端口索引。 |
| uint8_t *data | 指向要发送的事件数组的指针。 |
| uint32_t byteSize | 数组中的字节数。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 所有数据均已成功处理并写入。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效，或未打开。 |
| [OH_MIDI_STATUS_TIMEOUT](capi-native-midi-base-h.md#oh_midistatuscode) | 无法在合理时间内完成，可使用[OH_MIDIDevice_FlushOutputPort](#oh_mididevice_flushoutputport)重置。 |
| [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) | 参数无效。 |

**起始版本：** 24

---

### OH_MIDIDevice_FlushOutputPort

```c
OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort (OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

清空输出缓冲区中的待发送消息。

立即丢弃指定端口输出缓冲区中等待的所有MIDI事件，包括计划用于未来时间戳的事件。

> **说明**
>
> 此操作**不**发送"All Notes Off"消息，仅清空队列。

**参数**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](#oh_mididevice) *device | 目标设备句柄。 |
| uint32_t portIndex | 目标端口索引。 |

**返回值**

| 返回值 | 描述 |
| -- | -- |
| [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) | 操作成功。 |
| [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) | 设备句柄无效。 |
| [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) | 端口索引无效或不是输出端口。 |
| [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) | 连接系统服务失败。 |

**起始版本：** 24
