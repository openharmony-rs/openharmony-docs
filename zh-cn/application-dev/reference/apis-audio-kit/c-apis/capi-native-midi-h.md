# native_midi.h

## 概述

声明MIDI相关的接口。MIDI是一种用于电子乐器、计算机和其他设备之间通信的技术标准。<br>该文件中的接口用于MIDI设备管理、MIDI消息发送和接收、设备状态监控等。<br>使用OHMIDI连接MIDI设备的典型流程如下：

**库：** libohmidi.so

**系统能力：** SystemCapability.Multimedia.Audio.MIDI

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)](#oh_midiclient_create) | 创建MIDI客户端实例。客户端是使用MIDI服务的入口，所有MIDI操作都需要先创建客户端。<br>MIDI是对低延迟有严格要求的系统服务。为确保实时性能和系统稳定性，服务强制执行以下限制：<br>1. 系统级限制：全局允许的活动MIDI客户端最大数量为8个。<br>2. 每应用限制：每个应用UID允许的MIDI客户端最大数量为2个。建议应用在整个生命周期内维护单个MIDI客户端实例，用于管理多个设备/端口。<br>在不再需要MIDI功能时，使用[OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy)释放客户端及所有关联资源。 |
| [OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)](#oh_midiclient_destroy) | 销毁MIDI客户端并释放资源。 |
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)](#oh_midiclient_getdevicecount) | 获取连接的MIDI设备数量。此函数用于确定存储设备信息所需的缓冲区大小。<br>如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不计入设备数量。 |
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)](#oh_midiclient_getdeviceinfos) | 获取连接的MIDI设备信息。将设备信息写入infos参数指定的缓冲区。缓冲区大小应基于[OH_MIDIClient_GetDeviceCount](capi-native-midi-h.md#oh_midiclient_getdevicecount)返回的数量进行分配。<br>如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不会包含在返回的设备信息中。 |
| [OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)](#oh_midiclient_opendevice) | 打开指定ID的MIDI设备。 |
| [OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)](#oh_midiclient_openbledevice) | 异步打开蓝牙低功耗（BLE）MIDI设备。此函数为异步操作，调用后立即返回状态码（表示请求是否成功发送），实际连接结果（成功或失败）将在BLE连接过程完成后通过提供的回调异步传递。 |
| [OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)](#oh_midiclient_closedevice) | 关闭MIDI设备。 |
| [OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)](#oh_midiclient_getportcount) | 获取指定MIDI设备的端口数量。此函数用于确定存储端口信息所需的缓冲区大小。 |
| [OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)](#oh_midiclient_getportinfos) | 获取指定MIDI设备的端口信息。将端口信息写入由调用者分配的缓冲区。 |
| [OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)](#oh_mididevice_openinputport) | 打开MIDI输入端口（接收数据）。注册回调函数以接收MIDI数据流。 |
| [OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)](#oh_mididevice_openoutputport) | 打开MIDI输出端口（发送数据）。 |
| [OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeinputport) | 关闭MIDI输入端口。 |
| [OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeoutputport) | 关闭MIDI输出端口。 |
| [OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)](#oh_mididevice_send) | 批量发送MIDI消息（非阻塞模式，每条消息具有原子性）。 |
| [OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)](#oh_mididevice_sendsysex) | 发送超过标准MIDI消息长度的SysEx（System Exclusive，系统独占消息），自动处理分包和阻塞等待。这是一个实用函数，适用于将SysEx作为原始字节流（MIDI 1.0风格，F0...F7）处理的应用。<br>同时适用于[OH_MIDI_PROTOCOL_1_0](capi-native-midi-base-h.md#oh_midiprotocol)和[OH_MIDI_PROTOCOL_2_0](capi-native-midi-base-h.md#oh_midiprotocol)会话。<br>操作系统MIDI服务会自动将数据转换为设备端口所需的格式。 |
| [OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_flushoutputport) | 清空输出缓冲区中的待发送消息。立即丢弃指定端口输出缓冲区中等待的所有MIDI事件，包括用于未来时间戳的事件。 |

## 函数说明

### OH_MIDIClient_Create()

```c
OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)
```

**描述**

创建MIDI客户端实例。客户端是使用MIDI服务的入口，所有MIDI操作都需要先创建客户端。<br>MIDI是对低延迟有严格要求的系统服务。为确保实时性能和系统稳定性，服务强制执行以下限制：<br>1. 系统级限制：全局允许的活动MIDI客户端最大数量为8个。<br>2. 每应用限制：每个应用UID允许的MIDI客户端最大数量为2个。建议应用在整个生命周期内维护单个MIDI客户端实例，用于管理多个设备/端口。<br>在不再需要MIDI功能时，使用[OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy)释放客户端及所有关联资源。

>**说明：** 
>Resource Management & Best Practices**:
 *     MIDI is a delay-sensitive system service. To ensure real-time performance (QoS)
 *     and system stability, the service enforces the following limits:
 *     1. **System-wide limit**: A global maximum number of active MIDI clients that are allowed.
 *     2. **Per-Application limit**: A maximum number of MIDI clients that are allowed per app uid.
  *     Applications are **strongly recommended** to maintain a single `OH_MIDIClient`
 *     instance throughout their lifecycle and use it to manage multiple devices/ports.
  *     Use [OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy) to release the client and all associated resources.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) **client | 指向用于接收新客户端句柄的指针。 |
| [OH_MIDICallbacks](capi-ohmidi-oh-midicallbacks.md) callbacks | 用于系统事件的回调结构体。 |
| void *userData | 传递给回调函数的用户自定义数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数client为nullptr。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。      <br>OH_MIDI_STATUS_TOO_MANY_CLIENTS：因资源限制MIDI客户端创建失败。当调用应用超出其每UID配额或系统全局客户端数量已达上限时发生。 |

### OH_MIDIClient_Destroy()

```c
OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)
```

**描述**

销毁MIDI客户端并释放资源。

>**说明：** 
>Destroying the client will close all devices and ports (fail-safe mechanism) automatically.
 *     It is recommended to close resources in reverse order (ports->devices->client) for code clarity,
 *     but this is not a mandatory requirement.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | 目标客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄为NULL或无效。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIClient_GetDeviceCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)
```

**描述**

获取连接的MIDI设备数量。此函数用于确定存储设备信息所需的缓冲区大小。<br>如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不计入设备数量。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| size_t *count | 输出参数，用于接收设备数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数count为nullptr。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIClient_GetDeviceInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)
```

**描述**

获取连接的MIDI设备信息。将设备信息写入infos参数指定的缓冲区。缓冲区大小应基于[OH_MIDIClient_GetDeviceCount](capi-native-midi-h.md#oh_midiclient_getdevicecount)返回的数量进行分配。<br>如果应用未获得蓝牙权限（ohos.permission.ACCESS_BLUETOOTH），蓝牙MIDI设备将不会包含在返回的设备信息中。

>**说明：** 
>The actual number of connected devices may be larger than the capacity of the input parameter
 *     'infos' array. If this happens, the output 'infos' array will only contain partial devices information,
 *     the output 'actualDeviceCount' will be equal to 'capacity', and the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode).
 *     If the actual number is less than or equal to 'capacity', all available devices information
 *     will be filled into 'infos', and the output 'actualDeviceCount' reflects the actual devices number.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) *infos | 用户分配的该缓冲区，用于存储设备信息。 |
| size_t capacity | 缓冲区可容纳的最大元素数量。 |
| size_t *actualDeviceCount | 输出参数，用于接收实际写入的设备数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数infos或actualDeviceCount为nullptr。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIClient_OpenDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)
```

**描述**

打开指定ID的MIDI设备。

>**说明：** 
>Use [OH_MIDIClient_CloseDevice](capi-native-midi-h.md#oh_midiclient_closedevice) to release the device resource.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | 目标客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| int64_t deviceId | 设备的唯一标识符，由[OH_MIDIClient_GetDeviceInfos](capi-native-midi-h.md#oh_midiclient_getdeviceinfos)获取。 |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) **device | 指向用于接收设备句柄的指针，由系统分配。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_DEVICE_ALREADY_OPEN：设备已被当前客户端打开。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数device为nullptr，或deviceId不存在。      <br>OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES：客户端已达到最大打开设备数量限制。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIClient_OpenBLEDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)
```

**描述**

异步打开蓝牙低功耗（BLE）MIDI设备。此函数为异步操作，调用后立即返回状态码（表示请求是否成功发送），实际连接结果（成功或失败）将在BLE连接过程完成后通过提供的回调异步传递。

>**说明：** 
>This function triggers a BLE scan so the opening process may take time.
 *     Use [OH_MIDIClient_CloseDevice](capi-native-midi-h.md#oh_midiclient_closedevice) to release the device resource.

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | 目标客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| const char *deviceAddr | BLE设备的MAC地址（例如："AA:BB:CC:DD:EE:FF"）。 |
| [OH_MIDIClient_OnDeviceOpened](capi-native-midi-base-h.md#oh_midiclient_ondeviceopened) callback | 连接过程完成时要调用的回调函数。 |
| void *userData | 传递给回调的用户自定义数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：连接请求已成功分发。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_DEVICE_ALREADY_OPEN：设备已被当前客户端打开。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数deviceAddr或callback为nullptr。      <br>OH_MIDI_STATUS_PERMISSION_DENIED：权限被拒绝。应用未声明或未获得所需权限。      <br>OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES：客户端已达到最大打开设备数量限制。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：服务无法访问。 |

### OH_MIDIClient_CloseDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)
```

**描述**

关闭MIDI设备。

>**说明：** 
>Closing a device automatically closes all opened ports on that device.
 *     Paired with [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | 目标客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。 |

### OH_MIDIClient_GetPortCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)
```

**描述**

获取指定MIDI设备的端口数量。此函数用于确定存储端口信息所需的缓冲区大小。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| int64_t deviceId | 目标设备ID。 |
| size_t *count | 输出参数，用于接收端口数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数count为nullptr，或deviceId无效。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIClient_GetPortInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)
```

**描述**

获取指定MIDI设备的端口信息。将端口信息写入由调用者分配的缓冲区。

>**说明：** 
>The actual number of connected devices may be larger than the capacity of the input parameter
 *     'infos' array. If this happens, the output 'infos' array will only contain partial devices information,
 *     the output 'actualPortCount' will be equal to 'capacity', and the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode).
 *     If the actual number is less than or equal to 'capacity', all available ports information
 *     will be filled into 'infos', and the output 'actualPortCount' reflects the actual ports number.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI客户端句柄。传入的client指针必须为[OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create)创建的实例。 |
| int64_t deviceId | 目标设备ID。 |
| [OH_MIDIPortInformation](capi-ohmidi-oh-midiportinformation.md) *infos | 用户分配的缓冲区，用于存储端口信息。 |
| size_t capacity | infos缓冲区可容纳的最大元素数量。 |
| size_t *actualPortCount | 输出参数，用于接收实际写入的端口数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_CLIENT：客户端句柄无效。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数infos或actualPortCount为nullptr，或deviceId无效。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_OpenInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)
```

**描述**

打开MIDI输入端口（接收数据）。注册回调函数以接收MIDI数据流。

>**说明：** 
>Use [OH_MIDIDevice_CloseInputPort](capi-native-midi-h.md#oh_mididevice_closeinputport) to close the input port.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) descriptor | 端口索引和协议配置。 |
| [OH_MIDIDevice_OnReceived](capi-native-midi-base-h.md#oh_mididevice_onreceived) callback | 有数据可用时调用的回调函数。 |
| void *userData | 传递给回调的用户自定义数据指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效或不是输入端口。      <br>OH_MIDI_STATUS_PORT_ALREADY_OPEN：端口已被此客户端打开。      <br>OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS：已达到最大打开端口数量限制。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数callback为nullptr。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_OpenOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)
```

**描述**

打开MIDI输出端口（发送数据）。

>**说明：** 
>Use [OH_MIDIDevice_CloseOutputPort](capi-native-midi-h.md#oh_mididevice_closeoutputport) to close the output port.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) descriptor | 端口索引和协议配置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效或不是输出端口。      <br>OH_MIDI_STATUS_PORT_ALREADY_OPEN：端口已被此客户端打开。      <br>OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS：已达到最大打开端口数量限制。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_CloseInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

关闭MIDI输入端口。

>**说明：** 
>Paired with [OH_MIDIDevice_OpenInputPort](capi-native-midi-h.md#oh_mididevice_openinputport).

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| uint32_t portIndex | 要关闭的输入端口索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效，或未打开。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_CloseOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

关闭MIDI输出端口。

>**说明：** 
>Paired with [OH_MIDIDevice_OpenOutputPort](capi-native-midi-h.md#oh_mididevice_openoutputport).

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| uint32_t portIndex | 要关闭的输出端口索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效，或不是打开的输出端口。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_Send()

```c
OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)
```

**描述**

批量发送MIDI消息（非阻塞模式，每条消息具有原子性）。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| uint32_t portIndex | 目标端口索引。 |
| [const OH_MIDIEvent](capi-ohmidi-oh-midievent.md) *events | 指向要发送的事件数组的指针，内存空间需要由开发者分配。 |
| uint32_t eventCount | 数组中的事件数量。 |
| uint32_t *eventsWritten | 输出参数，返回成功发送的事件数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：所有数据均已成功处理并写入。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效，或未打开。      <br>OH_MIDI_STATUS_WOULD_BLOCK：缓冲区已满（检查eventsWritten）。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数无效。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |

### OH_MIDIDevice_SendSysEx()

```c
OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)
```

**描述**

发送超过标准MIDI消息长度的SysEx（System Exclusive，系统独占消息），自动处理分包和阻塞等待。这是一个实用函数，适用于将SysEx作为原始字节流（MIDI 1.0风格，F0...F7）处理的应用。<br>同时适用于[OH_MIDI_PROTOCOL_1_0](capi-native-midi-base-h.md#oh_midiprotocol)和[OH_MIDI_PROTOCOL_2_0](capi-native-midi-base-h.md#oh_midiprotocol)会话。<br>操作系统MIDI服务会自动将数据转换为设备端口所需的格式。

>**警告：** 
>BLOCKING CALL**: This function executes a loop and may block if the buffer fills up.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| uint32_t portIndex | 目标端口索引。 |
| const uint8_t *data | 指向要发送的字节数据流的指针，内存空间需要由开发者分配。 |
| uint32_t byteSize | 数据的字节大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：所有数据均已成功处理并写入。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效，或未打开。      <br>OH_MIDI_STATUS_TIMEOUT：无法在合理时间内完成，可使用[OH_MIDIDevice_FlushOutputPort](capi-native-midi-h.md#oh_mididevice_flushoutputport)重置。      <br>OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT：参数无效。 |

### OH_MIDIDevice_FlushOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**描述**

清空输出缓冲区中的待发送消息。立即丢弃指定端口输出缓冲区中等待的所有MIDI事件，包括用于未来时间戳的事件。

>**说明：** 
>This function does not send "All Notes Off" event. It simply clears the queue.

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | 目标设备句柄。传入的device指针必须为[OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice)或[OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice)返回的实例。 |
| uint32_t portIndex | 目标端口索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | OH_MIDI_STATUS_OK：操作成功。      <br>OH_MIDI_STATUS_INVALID_DEVICE_HANDLE：设备句柄无效。      <br>OH_MIDI_STATUS_INVALID_PORT：端口索引无效或不是输出端口。      <br>OH_MIDI_STATUS_GENERIC_IPC_FAILURE：连接系统服务失败。 |


