# ipc_cparcel.h

## 概述

提供IPC序列化/反序列化C接口，用于在IPC通信过程中对数据进行序列化和反序列化操作。

**库：** libipc_capi.so

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**相关模块：** [OHIPCParcel](capi-ohipcparcel.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) | - | IPC序列化对象，用于在跨进程通信中序列化和反序列化数据。该对象需要通过相关函数创建和销毁，开发者需要遵循对象的生命周期管理规范，正确管理内存资源。 |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) | - | IPC（进程间通信）远端代理对象，用于在客户端代理远端服务的能力，实现跨进程通信。该对象封装了远端服务的引用，支持向远端服务发送请求和接收响应。适用于需要跨进程调用服务能力的场景，例如跨进程服务调用、系统服务访问、跨应用数据共享等典型应用。使用该对象可以简化跨进程通信的实现，提高开发效率。 |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) | - | IPC远端服务对象。该结构体用于在服务端表示一个远端服务，作为IPC通信中服务端的服务代理，用于处理客户端的请求并实现跨进程通信。OHIPCRemoteStub是IPC Kit提供的核心结构体，使用OHIPCRemoteStub可以简化IPC服务开发流程，提供统一的请求处理机制，帮助开发者快速实现跨进程通信能力。主要用于： |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void* (\*OH_IPC_MemAllocator)(int32_t len)](#oh_ipc_memallocator) | OH_IPC_MemAllocator | 内存分配函数类型，用于IPC通信中自定义内存分配策略。常用于需要特殊内存管理的场景，例如：共享内存传输、内存池管理、限制内存使用上限等。 |
| [OHIPCParcel* OH_IPCParcel_Create(void)](#oh_ipcparcel_create) | - | 创建OHIPCParcel对象，用于IPC通信中的数据序列化。 |
| [void OH_IPCParcel_Destroy(OHIPCParcel *parcel)](#oh_ipcparcel_destroy) | - | 销毁OHIPCParcel对象。 |
| [int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)](#oh_ipcparcel_getdatasize) | - | 获取OHIPCParcel对象包含的数据的大小。常用于监控数据传输进度、检查是否超过IPC序列化大小限制、调试数据读写过程等场景。 |
| [int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getwritablebytes) | - | 获取OHIPCParcel对象可以写入的字节数。常用于检查是否还有空间写入更多数据、防止写入溢出、批量写入前预检查等场景。 |
| [int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadablebytes) | - | 获取OHIPCParcel对象还可以读取的字节数。常用于检查还有多少数据可读、循环读取数据、调试数据读取过程等场景。 |
| [int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadposition) | - | 获取OHIPCParcel对象当前读取位置。常用于记录读取位置以便后续恢复、配合RewindReadPosition实现重复读取、调试数据读取进度等场景。 |
| [int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getwriteposition) | - | 获取OHIPCParcel对象当前写入位置。常用于记录写入位置、配合RewindWritePosition修正写入错误、调试数据写入进度等场景。 |
| [int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)](#oh_ipcparcel_rewindreadposition) | - | 重置OHIPCParcel对象的读取位置到指定位置。常用于需要重复解析数据的场景。 |
| [int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)](#oh_ipcparcel_rewindwriteposition) | - | 重置OHIPCParcel对象的写入位置到指定位置。常用于写入数据后发现前序数据错误需要修正、实现数据的分段重写、撤销部分写入操作等场景。 |
| [int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)](#oh_ipcparcel_writeint8) | - | 向OHIPCParcel写入一个int8_t值。不支持多线程并发访问同一对象。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)](#oh_ipcparcel_readint8) | - | 从OHIPCParcel对象中读取int8_t值。不支持多线程并发访问同一对象。 |
| [int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)](#oh_ipcparcel_writeint16) | - | 向OHIPCParcel对象写入int16_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)](#oh_ipcparcel_readint16) | - | 从OHIPCParcel对象读取int16_t值。 |
| [int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)](#oh_ipcparcel_writeint32) | - | 向OHIPCParcel对象写入int32_t值。写入数据受IPC序列化总大小限制，参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)。 |
| [int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)](#oh_ipcparcel_readint32) | - | 从OHIPCParcel对象读取int32_t值。 |
| [int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)](#oh_ipcparcel_writeint64) | - | 向OHIPCParcel对象写入int64_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)](#oh_ipcparcel_readint64) | - | 从OHIPCParcel对象读取int64_t值。 |
| [int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)](#oh_ipcparcel_writeuint8) | - | 向OHIPCParcel对象写入uint8_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)](#oh_ipcparcel_readuint8) | - | 从OHIPCParcel对象读取uint8_t值。 |
| [int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)](#oh_ipcparcel_writeuint16) | - | 向OHIPCParcel对象写入uint16_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)](#oh_ipcparcel_readuint16) | - | 从OHIPCParcel对象读取uint16_t值。 |
| [int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)](#oh_ipcparcel_writeuint32) | - | 向OHIPCParcel对象写入uint32_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)](#oh_ipcparcel_readuint32) | - | 从OHIPCParcel对象读取uint32_t值。 |
| [int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)](#oh_ipcparcel_writeuint64) | - | 向OHIPCParcel对象写入uint64_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)](#oh_ipcparcel_readuint64) | - | 从OHIPCParcel对象读取uint64_t值。 |
| [int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)](#oh_ipcparcel_writefloat) | - | 向OHIPCParcel对象写入float值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)](#oh_ipcparcel_readfloat) | - | 从OHIPCParcel对象读取float值。 |
| [int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)](#oh_ipcparcel_writedouble) | - | 向OHIPCParcel对象写入double值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)](#oh_ipcparcel_readdouble) | - | 从OHIPCParcel对象读取double值。调用此函数后，从当前读取位置读取8字节的double值，读取位置自动后移8字节，读取到的值存储到value指针指向的内存中。 |
| [int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)](#oh_ipcparcel_writestring) | - | 向OHIPCParcel对象写入字符串，包括字符串结束符。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)](#oh_ipcparcel_readstring) | - | 从OHIPCParcel对象读取字符串，用户可通过strlen获取字符串长度。 |
| [int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)](#oh_ipcparcel_writebuffer) | - | 向OHIPCParcel对象写入指定长度的内存信息。常用于写入二进制数据、图片数据、自定义结构体、共享内存内容等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)](#oh_ipcparcel_readbuffer) | - | 从OHIPCParcel对象读取指定长度内存信息。常用于读取二进制数据、图片数据、自定义结构体、共享内存内容等场景。 |
| [int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)](#oh_ipcparcel_writeremotestub) | - | 向OHIPCParcel对象写入OHIPCRemoteStub对象。常用于跨进程传递服务对象、实现IPC服务端的远程调用、服务对象共享等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)](#oh_ipcparcel_readremotestub) | - | 从OHIPCParcel对象读取OHIPCRemoteStub对象。常用于跨进程接收服务对象、实现IPC服务端的远程调用、服务对象共享等场景。 |
| [int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)](#oh_ipcparcel_writeremoteproxy) | - | 向OHIPCParcel对象写入OHIPCRemoteProxy对象。常用于跨进程传递代理对象、实现IPC客户端的远程调用、代理对象共享等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)](#oh_ipcparcel_readremoteproxy) | - | 从OHIPCParcel对象读取OHIPCRemoteProxy对象。常用于跨进程接收代理对象、实现IPC客户端的远程调用、代理对象共享等场景。 |
| [int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)](#oh_ipcparcel_writefiledescriptor) | - | 向OHIPCParcel对象写入文件描述符。常用于跨进程传递文件句柄、共享内存文件描述符、管道文件描述符等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)](#oh_ipcparcel_readfiledescriptor) | - | 从OHIPCParcel对象读取文件描述符。常用于跨进程接收文件句柄、共享内存文件描述符、管道文件描述符等场景。不支持多线程并发访问同一对象。 |
| [int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)](#oh_ipcparcel_append) | - | OHIPCParcel对象数据拼接。常用于合并多个Parcel的数据、数据包组装、分段写入数据的合并等场景。拼接数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)](#oh_ipcparcel_writeinterfacetoken) | - | 向OHIPCParcel对象写入接口描述符，用于接口身份校验。常用于IPC通信中的安全验证场景，例如：防止恶意进程发送伪造请求、确保消息发送到正确的服务接口、多接口服务中区分不同的接口调用。不支持多线程并发访问同一对象。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。 |
| [int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcparcel_readinterfacetoken) | - | 从OHIPCParcel对象读取接口描述符信息，用于接口身份校验。 |

## 函数说明

### OH_IPC_MemAllocator()

```c
typedef void* (*OH_IPC_MemAllocator)(int32_t len)
```

**描述**

内存分配函数类型，用于IPC通信中自定义内存分配策略。常用于需要特殊内存管理的场景，例如：共享内存传输、内存池管理、限制内存使用上限等。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (int32_t len | 申请内存的长度，单位：字节。取值原则：必须大于0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| void* | 成功返回分配的内存地址；失败返回NULL。 |

### OH_IPCParcel_Create()

```c
OHIPCParcel* OH_IPCParcel_Create(void)
```

**描述**

创建OHIPCParcel对象，用于IPC通信中的数据序列化。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHIPCParcel*](capi-ohipcparcel-ohipcparcel.md) | 成功返回OHIPCParcel对象指针；失败返回NULL。 |

### OH_IPCParcel_Destroy()

```c
void OH_IPCParcel_Destroy(OHIPCParcel *parcel)
```

**描述**

销毁OHIPCParcel对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | 需要销毁OHIPCParcel对象的指针，不能为空。 |

### OH_IPCParcel_GetDataSize()

```c
int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)
```

**描述**

获取OHIPCParcel对象包含的数据的大小。常用于监控数据传输进度、检查是否超过IPC序列化大小限制、调试数据读写过程等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回Parcel对象已写入数据的累计大小，单位：字节，参数不合法时返回-1。 |

### OH_IPCParcel_GetWritableBytes()

```c
int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)
```

**描述**

获取OHIPCParcel对象可以写入的字节数。常用于检查是否还有空间写入更多数据、防止写入溢出、批量写入前预检查等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回可写字节数大小，单位：字节，参数不合法时返回-1。 |

### OH_IPCParcel_GetReadableBytes()

```c
int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)
```

**描述**

获取OHIPCParcel对象还可以读取的字节数。常用于检查还有多少数据可读、循环读取数据、调试数据读取过程等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回可读字节数大小，单位：字节，参数不合法时返回-1。 |

### OH_IPCParcel_GetReadPosition()

```c
int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)
```

**描述**

获取OHIPCParcel对象当前读取位置。常用于记录读取位置以便后续恢复、配合RewindReadPosition实现重复读取、调试数据读取进度等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回当前读位置，单位：字节，参数不合法时返回-1。 |

### OH_IPCParcel_GetWritePosition()

```c
int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)
```

**描述**

获取OHIPCParcel对象当前写入位置。常用于记录写入位置、配合RewindWritePosition修正写入错误、调试数据写入进度等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回当前写入位置，单位：字节。参数不合法时返回-1。 |

### OH_IPCParcel_RewindReadPosition()

```c
int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)
```

**描述**

重置OHIPCParcel对象的读取位置到指定位置。常用于需要重复解析数据的场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint32_t newReadPos | 新的读取位置，范围：[0，当前数据大小]，单位：字节。超出范围时返回OH_IPC_CHECK_PARAM_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}。 |

### OH_IPCParcel_RewindWritePosition()

```c
int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)
```

**描述**

重置OHIPCParcel对象的写入位置到指定位置。常用于写入数据后发现前序数据错误需要修正、实现数据的分段重写、撤销部分写入操作等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint32_t newWritePos | 新的写入位置，范围：[0, 当前数据大小]，单位：字节。超出范围时返回OH_IPC_CHECK_PARAM_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}。 |

### OH_IPCParcel_WriteInt8()

```c
int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)
```

**描述**

向OHIPCParcel写入一个int8_t值。不支持多线程并发访问同一对象。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int8_t value | 要写入的int8_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadInt8()

```c
int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)
```

**描述**

从OHIPCParcel对象中读取int8_t值。不支持多线程并发访问同一对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int8_t *value | 用于存储读取到的int8_t数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteInt16()

```c
int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)
```

**描述**

向OHIPCParcel对象写入int16_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int16_t value | 要写入的int16_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadInt16()

```c
int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)
```

**描述**

从OHIPCParcel对象读取int16_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int16_t *value | 用于存储读取到的int16_t数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteInt32()

```c
int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)
```

**描述**

向OHIPCParcel对象写入int32_t值。写入数据受IPC序列化总大小限制，参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int32_t value | 要写入的int32_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadInt32()

```c
int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)
```

**描述**

从OHIPCParcel对象读取int32_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int32_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteInt64()

```c
int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)
```

**描述**

向OHIPCParcel对象写入int64_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int64_t value | 要写入的int64_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadInt64()

```c
int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)
```

**描述**

从OHIPCParcel对象读取int64_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int64_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteUint8()

```c
int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)
```

**描述**

向OHIPCParcel对象写入uint8_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint8_t value | 要写入的uint8_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadUint8()

```c
int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)
```

**描述**

从OHIPCParcel对象读取uint8_t值。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint8_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteUint16()

```c
int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)
```

**描述**

向OHIPCParcel对象写入uint16_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint16_t value | 要写入的uint16_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadUint16()

```c
int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)
```

**描述**

从OHIPCParcel对象读取uint16_t值。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint16_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteUint32()

```c
int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)
```

**描述**

向OHIPCParcel对象写入uint32_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint32_t value | 要写入的uint32_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadUint32()

```c
int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)
```

**描述**

从OHIPCParcel对象读取uint32_t值。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint32_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteUint64()

```c
int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)
```

**描述**

向OHIPCParcel对象写入uint64_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint64_t value | 要写入的uint64_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadUint64()

```c
int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)
```

**描述**

从OHIPCParcel对象读取uint64_t值。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| uint64_t *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteFloat()

```c
int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)
```

**描述**

向OHIPCParcel对象写入float值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| float value | 要写入的float数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadFloat()

```c
int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)
```

**描述**

从OHIPCParcel对象读取float值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| float *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteDouble()

```c
int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)
```

**描述**

向OHIPCParcel对象写入double值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| double value | 要写入的double数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadDouble()

```c
int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)
```

**描述**

从OHIPCParcel对象读取double值。调用此函数后，从当前读取位置读取8字节的double值，读取位置自动后移8字节，读取到的值存储到value指针指向的内存中。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| double *value | 存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_WriteString()

```c
int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)
```

**描述**

向OHIPCParcel对象写入字符串，包括字符串结束符。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| const char *str | 写入字符串，用于IPC通信中的字符串数据传输，不能为空。长度范围[0, 204800]，单位：字节（含结束符，实际长度受parcel已写入数据与结束符开销的动态影响）。写入的字符串长度受IPC序列化大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。超出限制时返回OH_IPC_PARCEL_WRITE_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadString()

```c
const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)
```

**描述**

从OHIPCParcel对象读取字符串，用户可通过strlen获取字符串长度。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 成功返回读取字符串地址；参数不合法或读取失败时返回NULL。 |

### OH_IPCParcel_WriteBuffer()

```c
int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)
```

**描述**

向OHIPCParcel对象写入指定长度的内存信息。常用于写入二进制数据、图片数据、自定义结构体、共享内存内容等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| const uint8_t *buffer | 写入内存的起始地址，要写入的数据缓冲区的起始地址，指向需要通过IPC传输的二进制数据，不能为空。缓冲区必须提前分配好足够的内存空间。 |
| int32_t len | 写入信息长度，单位：字节，取值范围[0, parcel可写字节数]。写入数据大小受IPC序列化大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。传入负数时返回OH_IPC_CHECK_PARAM_ERROR；超出可写字节数时返回OH_IPC_PARCEL_WRITE_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadBuffer()

```c
const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)
```

**描述**

从OHIPCParcel对象读取指定长度内存信息。常用于读取二进制数据、图片数据、自定义结构体、共享内存内容等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int32_t len | 读取内存的长度，单位：字节，取值范围[0, parcel当前剩余可读字节数]。超出可读字节数时返回NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const uint8_t* | 成功返回读取到的内存地址；参数不合法或len超过parcel可读长度时返回NULL。 |

### OH_IPCParcel_WriteRemoteStub()

```c
int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)
```

**描述**

向OHIPCParcel对象写入OHIPCRemoteStub对象。常用于跨进程传递服务对象、实现IPC服务端的远程调用、服务对象共享等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| [const OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | 需要写入的OHIPCRemoteStub对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadRemoteStub()

```c
OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)
```

**描述**

从OHIPCParcel对象读取OHIPCRemoteStub对象。常用于跨进程接收服务对象、实现IPC服务端的远程调用、服务对象共享等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHIPCRemoteStub*](capi-ohipcparcel-ohipcremotestub.md) | 成功返回OHIPCRemoteStub对象指针；失败返回NULL。 |

### OH_IPCParcel_WriteRemoteProxy()

```c
int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)
```

**描述**

向OHIPCParcel对象写入OHIPCRemoteProxy对象。常用于跨进程传递代理对象、实现IPC客户端的远程调用、代理对象共享等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| [const OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | 需要写入的OHIPCRemoteProxy对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadRemoteProxy()

```c
OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)
```

**描述**

从OHIPCParcel对象读取OHIPCRemoteProxy对象。常用于跨进程接收代理对象、实现IPC客户端的远程调用、代理对象共享等场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHIPCRemoteProxy*](capi-ohipcparcel-ohipcremoteproxy.md) | 成功返回OHIPCRemoteProxy对象指针；失败返回NULL。 |

### OH_IPCParcel_WriteFileDescriptor()

```c
int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)
```

**描述**

向OHIPCParcel对象写入文件描述符。常用于跨进程传递文件句柄、共享内存文件描述符、管道文件描述符等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int32_t fd | 要写入的文件描述符，取值原则：有效的文件描述符，为非负整数。传入负数或无效文件描述符时返回OH_IPC_CHECK_PAARM_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadFileDescriptor()

```c
int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)
```

**描述**

从OHIPCParcel对象读取文件描述符。常用于跨进程接收文件句柄、共享内存文件描述符、管道文件描述符等场景。不支持多线程并发访问同一对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| int32_t *fd | 存储读取文件描述符的指针，不能为空。读取前需确保parcel中已写入有效的文件描述符数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |

### OH_IPCParcel_Append()

```c
int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)
```

**描述**

OHIPCParcel对象数据拼接。常用于合并多个Parcel的数据、数据包组装、分段写入数据的合并等场景。拼接数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *data | data源OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 拼接失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_WriteInterfaceToken()

```c
int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)
```

**描述**

向OHIPCParcel对象写入接口描述符，用于接口身份校验。常用于IPC通信中的安全验证场景，例如：防止恶意进程发送伪造请求、确保消息发送到正确的服务接口、多接口服务中区分不同的接口调用。不支持多线程并发访问同一对象。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](capi-ipc-cparcel-h.md#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| const char *token | 需要写入的接口描述符信息，不能为空。接口描述符通常为接口的全限定名或唯一标识字符串，用于接口身份校验。字符串长度范围[0, parcel剩余可写空间]，单位：字节。超出限制时返回OH_IPC_PARCEL_WRITE_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；<br> 写入失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR}。 |

### OH_IPCParcel_ReadInterfaceToken()

```c
int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)
```

**描述**

从OHIPCParcel对象读取接口描述符信息，用于接口身份校验。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | OHIPCParcel对象的指针，不能为空。 |
| char **token | 用于存储接口描述符信息的内存地址，该内存由用户提供的分配器进行内存分配，用户使用完后需要主动释放，不能为空。接口返回失败时，用户依然需要判断该内存是否为空，并主动释放，否则会造成内存泄漏。 |
| int32_t *len | 存储读取接口描述符的长度（包括结束符），单位：字节，不能为空。 |
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | 用户指定的用来分配token的内存分配器，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 成功返回{@link OH_IPC_ErrorCode#OH_IPC_SUCCESS}；<br> 参数不合法时返回{@link OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR}；读取失败返回{@link OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR}。 |


