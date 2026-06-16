# ipc_cparcel.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

## 概述

提供IPC序列化/反序列化C接口，用于在IPC通信过程中对数据进行序列化和反序列化操作。

对应的开发指南及样例可参考[IPC与RPC通信开发指导(C/C++)](../../ipc/ipc-capi-development-guideline.md)。

**引用文件：** <IPCKit/ipc_cparcel.h>

**库：** libipc_capi.so

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**相关模块：**[OHIPCParcel](capi-ohipcparcel.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| ---- | ------------- | ---- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md)| OHIPCParcel | IPC序列化对象。 |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) | OHIPCRemoteProxy | IPC远端代理对象。 |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) | OHIPCRemoteStub | IPC远端服务对象。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| ---- | ------------- | ---- |
| [typedef void* (\*OH_IPC_MemAllocator)(int32_t len)](#oh_ipc_memallocator) | [OH_IPC_MemAllocator](#oh_ipc_memallocator) | 内存分配函数类型。 |
| [OHIPCParcel* OH_IPCParcel_Create(void)](#oh_ipcparcel_create) | - | 创建OHIPCParcel对象，对象可序列化大小不能超过204800字节。 |
| [void OH_IPCParcel_Destroy(OHIPCParcel *parcel)](#oh_ipcparcel_destroy) | - | 销毁OHIPCParcel对象。 |
| [int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)](#oh_ipcparcel_getdatasize) | - | 获取OHIPCParcel对象包含的数据的大小。 |
| [int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getwritablebytes) | - | 获取OHIPCParcel对象可以写入的字节数。 |
| [int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadablebytes) | - | 获取OHIPCParcel对象还可以读取的字节数。 |
| [int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadposition) | - | 获取OHIPCParcel对象当前读取位置。 |
| [int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getwriteposition) | - | 获取OHIPCParcel对象当前写入位置。 |
| [int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)](#oh_ipcparcel_rewindreadposition) | - | 重置OHIPCParcel对象读取位置。 |
| [int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)](#oh_ipcparcel_rewindwriteposition) | - | 重置OHIPCParcel对象写入位置。 |
| [int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)](#oh_ipcparcel_writeint8) | - | 向OHIPCParcel对象写入一个int8_t值。 |
| [int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)](#oh_ipcparcel_readint8) | - | 从OHIPCParcel对象中读取一个int8_t值。 |
| [int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)](#oh_ipcparcel_writeint16) | - | 向OHIPCParcel对象写入一个int16_t值。 |
| [int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)](#oh_ipcparcel_readint16) | - | 从OHIPCParcel对象中读取一个int16_t值。 |
| [int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)](#oh_ipcparcel_writeint32) | - | 向OHIPCParcel对象写入一个int32_t值。 |
| [int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)](#oh_ipcparcel_readint32) | - | 从OHIPCParcel对象中读取一个int32_t值。 |
| [int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)](#oh_ipcparcel_writeint64) | - | 向OHIPCParcel对象写入一个int64_t值。 |
| [int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)](#oh_ipcparcel_readint64) | - | 从OHIPCParcel对象中读取一个int64_t值。 |
| [int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)](#oh_ipcparcel_writeuint8) | - | 向OHIPCParcel对象写入一个uint8_t值。 |
| [int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)](#oh_ipcparcel_readuint8) | - | 从OHIPCParcel对象中读取一个uint8_t值。 |
| [int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)](#oh_ipcparcel_writeuint16) | - | 向OHIPCParcel对象写入一个uint16_t值。 |
| [int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)](#oh_ipcparcel_readuint16) | - | 从OHIPCParcel对象中读取一个uint16_t值。 |
| [int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)](#oh_ipcparcel_writeuint32) | - | 向OHIPCParcel对象写入一个uint32_t值。 |
| [int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)](#oh_ipcparcel_readuint32) | - | 从OHIPCParcel对象中读取一个uint32_t值。 |
| [int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)](#oh_ipcparcel_writeuint64) | - | 向OHIPCParcel对象写入一个uint64_t值。 |
| [int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)](#oh_ipcparcel_readuint64) | - | 从OHIPCParcel对象中读取一个uint64_t值。 |
| [int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)](#oh_ipcparcel_writefloat) | - | 向OHIPCParcel对象写入一个float值。 |
| [int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)](#oh_ipcparcel_readfloat) | - | 从OHIPCParcel对象中读取一个float值。 |
| [int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)](#oh_ipcparcel_writedouble) | - | 向OHIPCParcel对象写入一个double值。 |
| [int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)](#oh_ipcparcel_readdouble) | - | 从OHIPCParcel对象中读取一个double值。 |
| [int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)](#oh_ipcparcel_writestring) | - | 向OHIPCParcel对象写入字符串，包含字符串结束符。 |
| [const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)](#oh_ipcparcel_readstring) | - | 从OHIPCParcel对象读取字符串，用户可通过strlen获取字符串长度。 |
| [int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)](#oh_ipcparcel_writebuffer) | - | 向OHIPCParcel对象写入指定长度的内存信息。 |
| [const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)](#oh_ipcparcel_readbuffer) | - | 从OHIPCParcel对象读取指定长度的内存信息。 |
| [int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)](#oh_ipcparcel_writeremotestub) | - | 向OHIPCParcel对象写入OHIPCRemoteStub对象。 |
| [OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)](#oh_ipcparcel_readremotestub) | - | 从OHIPCParcel对象读取OHIPCRemoteStub对象。 |
| [int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)](#oh_ipcparcel_writeremoteproxy) | - | 向OHIPCParcel对象写入OHIPCRemoteProxy对象。 |
| [OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)](#oh_ipcparcel_readremoteproxy) | - | 从OHIPCParcel对象读取OHIPCRemoteProxy对象。 |
| [int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)](#oh_ipcparcel_writefiledescriptor) | - | 向OHIPCParcel对象写入文件描述符。 |
| [int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)](#oh_ipcparcel_readfiledescriptor) | - | 从OHIPCParcel对象读取文件描述符。 |
| [int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)](#oh_ipcparcel_append) | - | OHIPCParcel对象数据拼接。 |
| [int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)](#oh_ipcparcel_writeinterfacetoken) | - | 向OHIPCParcel对象写入接口描述符，用于接口身份校验。 |
| [int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcparcel_readinterfacetoken) | - | 从OHIPCParcel对象读取接口描述符信息，用于接口身份校验。 |

## 函数说明

### OH_IPC_MemAllocator()

```C
typedef void* (*OH_IPC_MemAllocator)(int32_t len);
```

**描述：**

内存分配函数类型，用于IPC通信中自定义内存分配策略。常用于需要特殊内存管理的场景，例如：共享内存传输、内存池管理、限制内存使用上限等。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | int32_t len  | len申请内存的长度，单位：字节。取值原则：必须大于0。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| void* | 成功返回分配的内存地址；失败返回NULL。 |

### OH_IPCParcel_Create()

```C
OHIPCParcel* OH_IPCParcel_Create(void)
```

**描述：**

创建OHIPCParcel对象，用于IPC通信中的数据序列化。

**调用后的行为**

调用此函数后：

1. 在内存中分配并初始化一个OHIPCParcel对象。
2. 对象初始状态为空，可写入数据大小最大为204800字节。
3. 返回对象指针用于后续的数据读写操作。

**原理说明**

该函数内部会：

- 分配固定大小的内存缓冲区。
- 初始化读写位置指针。
- 设置对象引用计数。

**约束和限制**

- **内存限制**：创建的对象可序列化大小不能超过204800字节。
- **生命周期**：使用完毕后必须调用[OH_IPCParcel_Destroy()](#oh_ipcparcel_destroy)释放资源，否则会导致内存泄漏。
- **线程安全**：不支持多线程并发访问同一对象。

**使用流程：**

典型使用流程：[OH_IPCParcel_Create](#oh_ipcparcel_create) → 数据读写操作 → [OH_IPCParcel_Destroy()](#oh_ipcparcel_destroy)。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| OHIPCParcel* | 成功返回OHIPCParcel对象指针；失败返回NULL。 |

### OH_IPCParcel_Destroy()

```C
void OH_IPCParcel_Destroy(OHIPCParcel *parcel)
```

**描述：**

销毁OHIPCParcel对象。

**调用后的行为**

调用此函数后：

1. 释放OHIPCParcel对象占用的内存缓冲区。
2. 清除对象内部的所有数据。
3. 释放对象自身的内存。
4. 传入的指针将变为无效指针，不应再被使用。

**原理说明**

该函数会：

- 检查对象引用计数。
- 释放数据缓冲区。
- 释放对象结构体内存。

**约束和限制**

- **使用前检查**：确保没有其他线程正在使用该对象。
- **指针置空**：销毁后建议将指针置为NULL，避免悬垂指针。
- **销毁时机**：确保已读取完所有需要的数据后再销毁。
- **多次销毁**：禁止对同一对象多次调用销毁函数。

**配对调用：**

- 必须与[OH_IPCParcel_Create](#oh_ipcparcel_create)方法配对使用。
- 只能销毁由[OH_IPCParcel_Create](#oh_ipcparcel_create)创建的对象。
- 销毁后不能再访问该对象。

**注意事项：**

- 调用此方法前，确保不再需要该Parcel对象。
- 销毁后，所有指向该对象的指针都将失效。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel需要销毁OHIPCParcel对象的指针。 |

### OH_IPCParcel_GetDataSize()

```C
int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)
```

**描述：**

获取OHIPCParcel对象包含的数据的大小。常用于监控数据传输进度、检查是否超过IPC序列化大小限制、调试数据读写过程等场景。

**调用后的行为**

1. 计算Parcel对象中已写入数据的总字节数。
2. 返回数据大小值。
3. 不改变Parcel对象的读写位置或数据内容。

**原理说明**

该函数用于查询Parcel对象的数据状态:

- 返回已写入数据的累计大小。
- 不包括未写入的空间。
- 用于了解当前数据量，辅助后续读写操作规划。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回数据大小，单位：字节，参数不合法时返回-1。 |

### OH_IPCParcel_GetWritableBytes()

```C
int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)
```

**描述：**

获取OHIPCParcel对象可以写入的字节数。常用于检查是否还有空间写入更多数据、防止写入溢出、批量写入前预检查等场景。

**调用后的行为**

调用此函数后:

1. 计算Parcel对象剩余可写入空间的大小。
2. 返回可写字节数值。
3. 不改变Parcel对象的读写位置或数据内容。

**原理说明**

该函数用于查询Parcel对象的剩余容量:

- 返回最大容量减去已写入数据大小的剩余空间。
- 用于在写入前检查是否有足够空间。
- 辅助避免写入超出容量导致失败。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回可写字节数大小，参数不合法时返回-1。 |

### OH_IPCParcel_GetReadableBytes()

```C
int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)
```

**描述：**

获取OHIPCParcel对象还可以读取的字节数。常用于检查还有多少数据可读、循环读取数据、调试数据读取过程等场景。

**调用后的行为**

调用此函数后:

1. 计算Parcel对象中未读取数据的字节数。
2. 返回可读字节数值。
3. 不改变Parcel对象的读写位置或数据内容。

**原理说明**

该函数用于查询Parcel对象的剩余可读数据量:

- 返回数据总大小减去当前读取位置的剩余字节数。
- 用于在读取前检查是否有足够数据可读。
- 辅助避免读取超出数据范围导致失败。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回可读字节数大小，参数不合法时返回-1。 |

### OH_IPCParcel_GetReadPosition()

```C
int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)
```

**描述：**

获取OHIPCParcel对象当前读取位置。常用于记录读取位置以便后续恢复、配合RewindReadPosition实现重复读取、调试数据读取进度等场景。

**调用后的行为**

调用此函数后:

1. 返回Parcel对象当前的读取位置值。
2. 不改变读取位置或数据内容。

**原理说明**

该函数用于查询Parcel对象的读取指针状态:

- 返回当前读取指针的位置偏移量。
- 用于了解读取进度或配合RewindReadPosition重置位置。
- 支持复杂读取场景中的位置追踪。

**系统能力：** SystemCapability.Communication.IPC.Core
 
**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回当前读位置，参数不合法时返回-1。 |

### OH_IPCParcel_GetWritePosition()

```C
int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)
```

**描述：**

获取OHIPCParcel对象当前写入位置。常用于记录写入位置、配合RewindWritePosition修正写入错误、调试数据写入进度等场景。

**调用后的行为**

调用此函数后:

1. 返回Parcel对象当前的写入位置值。
2. 不改变写入位置或数据内容。

**原理说明**

该函数用于查询Parcel对象的写入指针状态:

- 返回当前写入指针的位置偏移量。
- 用于了解写入进度或配合RewindWritePosition重置位置。
- 支持复杂写入场景中的位置追踪。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | --------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 返回当前写入位置，参数不合法时返回-1。 |

### OH_IPCParcel_RewindReadPosition()

```c
int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)
```

**描述：**

重置OHIPCParcel对象的读取位置到指定位置。

**调用后的行为**

调用此函数后：

1. 读取位置指针移动到newReadPos指定的位置。
2. 已写入的数据保持不变。
3. 后续读取操作从新位置开始。

**原理说明**

该函数通过修改内部读取指针位置实现：

- 不移动或修改已存储的数据。
- 仅改变读取起始位置。
- 允许重复读取已读取过的数据。

**约束和限制**

- **位置范围**：newReadPos必须在[0, 当前数据大小]范围内。
- **写入影响**：重置读取位置不影响写入位置。
- **使用场景**：常用于需要重复解析数据的场景。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。必须先通过[OH_IPCParcel_Create()](#oh_ipcparcel_create)创建。 |
  | uint32_t newReadPos | newReadPos新的读取位置，范围：[0，当前数据大小]，单位：字节。超出范围时返回OH_IPC_CHECK_PARAM_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_RewindWritePosition()

```C
int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)
```

**描述：**

重置OHIPCParcel对象的写入位置到指定位置。

**调用后的行为** 

调用此函数后：

1. 写入位置指针移动到newWritePos指定的位置。
2. 位置之后的数据将被覆盖或无效。
3. 后续写入操作从新位置开始。

**原理说明**

该函数通过修改内部写入指针位置实现：

- 允许覆盖已写入的数据。
- 可用于修正错误写入的数据。
- 调整数据大小。

**使用场景**：常用于写入数据后发现前序数据错误需要修正、实现数据的分段重写、撤销部分写入操作等场景。

### 约束和限制

- **位置范围**：newWritePos必须在[0, 当前数据大小]范围内。
- **数据风险**：重置位置可能导致部分数据被覆盖，需谨慎使用。
- **读取影响**：重置写入位置不影响读取位置。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint32_t newWritePos | newWritePos新的写入位置，范围：[0, 当前数据大小]，单位：字节。超出范围时返回OH_IPC_CHECK_PARAM_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteInt8()

```C
int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)
```

**描述：**

向OHIPCParcel写入一个int8_t值。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int8_t value | value要写入的int8_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| -----| ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadInt8()

```C
int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)
```

**描述：**

从OHIPCParcel对象中读取int8_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int8_t *value | value用于存储读取到的int8_t数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteInt16()

```C
int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)
```

**描述：**

向OHIPCParcel对象写入int16_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int16_t value | value要写入的int16_t数据值，用于IPC通信数据序列化。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadInt16()

```C
int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)
```

**描述：**

从OHIPCParcel对象读取int16_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int16_t *value | value用于存储读取到的int16_t数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteInt32()

```C
int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)
```

**描述：**

向OHIPCParcel对象写入int32_t值。写入数据受IPC序列化总大小限制，参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int32_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadInt32()

```C
int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)
```

**描述：**

从OHIPCParcel对象读取int32_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int32_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteInt64()

```C
int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)
```

**描述：**

向OHIPCParcel对象写入int64_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int64_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadInt64()

```C
int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)
```

**描述：**

从OHIPCParcel对象读取int64_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int64_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteUint8()

```C
int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)
```

**描述：**

向OHIPCParcel对象写入uint8_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint8_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadUint8()

```C
int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)
```

**描述：**

从OHIPCParcel对象读取uint8_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint8_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteUint16()

```C
int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)
```

**描述：**

向OHIPCParcel对象写入uint16_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint16_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadUint16()

```C
int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)
```

**描述：**

从OHIPCParcel对象读取uint16_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint16_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteUint32()

```C
int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)
```

**描述：**

向OHIPCParcel对象写入uint32_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint32_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadUint32()

```C
int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)
```

**描述：**

从OHIPCParcel对象读取uint32_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint32_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteUint64()

```C
int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)
```

**描述：**

向OHIPCParcel对象写入uint64_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint64_t value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadUint64()

```C
int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)
```

**描述：**

从OHIPCParcel对象读取uint64_t值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 26.0.0

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | uint64_t *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteFloat()

```C
int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)
```

**描述：**

向OHIPCParcel对象写入float值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | float value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadFloat()

```C
int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)
```

**描述：**

从OHIPCParcel对象读取float值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | float *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteDouble()

```C
int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)
```

**描述：**

向OHIPCParcel对象写入double值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | double value | value要写入的值。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadDouble()

```C
int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)
```

**描述：**

从OHIPCParcel对象读取double值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | double *value | value存储读取数据的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteString()

```C
int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)
```

**描述：**

向OHIPCParcel对象写入字符串，包括字符串结束符。

**调用后的行为**

调用此函数后:

1. 将字符串内容(包括结束符'\0')写入到OHIPCParcel对象的当前写入位置。
2. 写入位置自动后移(字符串长度+1)字节。
3. 字符串数据被序列化存储在Parcel对象中。

**约束和限制**

- **长度限制**: 写入的字符串长度受IPC序列化大小限制(参见[OH_IPCParcel_Create](#oh_ipcparcel_create)，最大204800字节)。
- **空指针检查**: str参数不能为空，否则会返回参数错误。
- **内存管理**: 写入的字符串内存由Parcel对象内部管理，无需调用者管理。
- **编码说明**: 字符串应为有效的UTF-8或ASCII编码。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const char *str | str写入字符串，用于IPC通信中的字符串数据传输，不能为空。长度范围[0, 204800]，单位：字节（含结束符，实际长度受parcel已写入数据与结束符开销的动态影响）。写入的字符串长度受IPC序列化大小限制（参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。超出限制时返回OH_IPC_PARCEL_WRITE_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadString()

```C
const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)
```

**描述：**

从OHIPCParcel对象读取字符串，用户可通过strlen获取字符串长度。

**调用后的行为**

调用此函数后:

1. 从当前读取位置读取字符串内容。
2. 返回字符串的内存地址指针。
3. 读取位置自动后移到字符串结束符之后。

**原理说明**

该函数用于从序列化的Parcel对象中恢复字符串数据:

- 返回的指针指向Parcel对象内部存储的字符串数据。
- 不需要额外的内存分配或复制。
- 字符串生命周期与Parcel对象绑定。

**约束和限制**

- **内存管理**: 返回的字符串内存由Parcel对象管理，无需调用者释放。
- **生命周期**: 字符串有效性与Parcel对象绑定，销毁Parcel后字符串失效。
- **空指针检查**: 参数不合法或读取失败时返回NULL，需检查返回值。
- **使用方式**: 可通过strlen获取长度，直接使用返回的指针访问字符串内容。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| const char* | 成功返回读取字符串地址；参数不合法或读取失败时返回NULL。 |

### OH_IPCParcel_WriteBuffer()

```C
int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)
```

**描述：**

向OHIPCParcel对象写入指定长度的内存信息。常用于写入二进制数据、图片数据、自定义结构体、共享内存内容等场景。

**调用后的行为**

调用此函数后:

1. 将buffer指向的内存数据写入到OHIPCParcel对象的当前写入位置。
2. 写入位置自动后移len字节。
3. 内存数据被序列化存储在Parcel对象中。

**原理说明**

该函数用于写入原始内存数据块:

- 直接将内存缓冲区的内容复制到Parcel对象中。
- 不对数据进行任何转换或处理。
- 适合传输自定义结构体或二进制数据。

**约束和限制**

- **缓冲区管理**: buffer必须提前分配足够的内存空间，且内存有效。
- **长度限制**: len取值范围[0, parcel可写字节数]，超出范围会返回错误。
- **空指针检查**: buffer不能为空，否则会返回参数错误。
- **数据有效性**: 写入的数据应在调用期间保持有效，写入完成后无限制。
- **内存释放**: 写入完成后，buffer内存由调用者自行管理，Parcel内部存储副本。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const uint8_t *buffer  | buffer写入内存的起始地址，要写入的数据缓冲区的起始地址，指向需要通过IPC传输的二进制数据，不能为空。缓冲区必须提前分配好足够的内存空间。 |
  | int32_t len | len写入信息长度，单位：字节，取值范围[0, parcel可读字节数]。写入数据大小受IPC序列化大小限制（参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。超出可写字节数时返回OH_IPC_PARCEL_WRITE_ERROR错误。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadBuffer()

```C
const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)
```

**描述：**

从OHIPCParcel对象读取指定长度内存信息。常用于读取二进制数据、图片数据、自定义结构体、共享内存内容等场景。

**调用后的行为**

调用此函数后:

1. 从当前读取位置读取len字节的内存数据。
2. 返回指向Parcel对象内部存储数据的指针。
3. 读取位置自动后移len字节。

**原理说明**

该函数用于从序列化的Parcel对象中读取原始内存数据:

- 返回的指针指向Parcel对象内部存储的数据区域。
- 不进行数据转换，直接返回原始二进制数据。
- 适合读取自定义结构体或二进制数据。

**约束和限制**

- **长度限制**: len取值范围[0, parcel可读字节数]，超出范围会返回NULL。
- **内存管理**: 返回的内存由Parcel对象管理，无需调用者释放。
- **生命周期**: 数据有效性与Parcel对象绑定，销毁Parcel后数据失效。
- **空指针检查**: len超过可读长度或参数不合法时返回NULL，需检查返回值。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int32_t len | len读取内存的长度，单位：字节，取值范围[0, parcel当前剩余可读字节数]。超出可读字节数时返回NULL。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| const uint8_t* | 成功返回读取到的内存地址；参数不合法或len超过parcel可读长度时返回NULL。 |

### OH_IPCParcel_WriteRemoteStub()

```C
int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)
```

**描述：**

向OHIPCParcel对象写入OHIPCRemoteStub对象。常用于跨进程传递服务对象、实现IPC服务端的远程调用、服务对象共享等场景。写入数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。

**调用后的行为**

调用此函数后:

1. 将OHIPCRemoteStub对象的引用信息写入到OHIPCParcel对象中。
2. 写入位置自动后移。
3. Stub对象的引用信息被序列化存储。

**原理说明**

该函数用于IPC通信中传递服务端Stub对象:

- 写入Stub对象的引用而非对象本身。
- 接收端可通过ReadRemoteStub获取Stub对象的引用。
- 实现IPC通信中服务端Stub对象的跨进程传递。
- 支持服务端在IPC通信中传递自己的Stub对象给客户端。

**约束和限制**

- **对象有效性**: stub必须为有效的OHIPCRemoteStub对象指针。
- **空指针检查**: stub不能为空，否则会返回参数错误。
- **引用管理**: 写入后Stub对象的引用计数增加，需确保Stub对象生命周期足够。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | stub需要写入的OHIPCRemoteStub对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadRemoteStub()

```C
OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)
```

**描述：**

从OHIPCParcel对象读取OHIPCRemoteStub对象。常用于跨进程接收服务对象、实现IPC服务端的远程调用、服务对象共享等场景。

**调用后的行为**

调用此函数后:

1. 从当前读取位置读取Stub对象的引用信息。
2. 返回OHIPCRemoteStub对象的指针。
3. 读取位置自动后移。

**原理说明**

该函数用于IPC通信中接收服务端传递的Stub对象:

- 通过IPC机制接收对方进程传递的Stub对象引用。
- 返回Stub对象指针可用于后续IPC通信。
- 实现服务端Stub对象的跨进程传递。

**约束和限制**

- **对象管理**: 返回的Stub对象指针由系统管理，需按IPC规范使用。
- **有效性检查**: 读取失败时返回NULL，需检查返回值。
- **使用场景**: 通常用于接收服务端传递的Stub对象，用于建立IPC通信。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| OHIPCRemoteStub* | 成功返回OHIPCRemoteStub对象指针；失败返回NULL。 |

### OH_IPCParcel_WriteRemoteProxy()

```C
int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)
```

**描述：**

向OHIPCParcel对象写入OHIPCRemoteProxy对象。常用于跨进程传递代理对象、实现IPC客户端的远程调用、代理对象共享等场景。

**调用后的行为**

调用此函数后:

1. 将OHIPCRemoteProxy对象的引用信息写入到OHIPCParcel对象中。
2. 写入位置自动后移。
3. Proxy对象的引用信息被序列化存储。

**原理说明**

该函数用于IPC通信中传递客户端Proxy对象:

- 写入Proxy对象的引用而非对象本身。
- 接收端可通过ReadRemoteProxy获取Proxy对象的引用。
- 实现IPC通信中客户端Proxy对象的跨进程传递。
- 支持客户端在IPC通信中传递自己的Proxy对象给服务端。

**约束和限制**

- **对象有效性**: proxy必须为有效的OHIPCRemoteProxy对象指针。
- **空指针检查**: proxy不能为空，否则会返回参数错误。
- **引用管理**: 写入后Proxy对象的引用计数增加，需确保Proxy对象生命周期足够。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | proxy需要写入的OHIPCRemoteProxy对象指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadRemoteProxy()

```C
OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)
```

**描述：**

从OHIPCParcel对象读取OHIPCRemoteProxy对象。常用于跨进程接收代理对象、实现IPC客户端的远程调用、代理对象共享等场景。

**调用后的行为**

调用此函数后:

1. 从当前读取位置读取Proxy对象的引用信息。
2. 返回OHIPCRemoteProxy对象的指针。
3. 读取位置自动后移。

**原理说明**

该函数用于IPC通信中接收客户端传递的Proxy对象:

- 通过IPC机制接收对方进程传递的Proxy对象引用。
- 返回Proxy对象指针可用于后续IPC通信。
- 实现客户端Proxy对象的跨进程传递。

**约束和限制**

- **对象管理**: 返回的Proxy对象指针由系统管理，需按IPC规范使用。
- **有效性检查**: 读取失败时返回NULL，需检查返回值。
- **使用场景**: 通常用于接收客户端传递的Proxy对象，用于建立IPC通信。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| OHIPCRemoteProxy* | 成功返回OHIPCRemoteProxy对象指针；失败返回NULL。 |

### OH_IPCParcel_WriteFileDescriptor()

```C
int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)
```

**描述：**

向OHIPCParcel对象写入文件描述符。常用于跨进程传递文件句柄、共享内存文件描述符、管道文件描述符等场景。

**调用后的行为**

调用此函数后:

1. 将文件描述符的副本写入到OHIPCParcel对象中。
2. 写入位置自动后移。
3. 文件描述符信息被序列化存储，可在IPC通信中传递。

**原理说明**

该函数用于IPC通信中传递文件描述符:

- 文件描述符在IPC通信中通过特殊机制传递。
- 写入的是文件描述符的副本，而非文件内容本身。
- 接收端可通过ReadFileDescriptor获取有效的文件描述符。
- 实现了跨进程的文件描述符传递能力。

**约束和限制**

- **文件描述符有效性**: fd必须为有效的非负整数文件描述符。
- **资源管理**: 写入后原文件描述符仍由调用者管理，需自行关闭。
- **权限传递**: 接收端获得的文件描述符具有相同的访问权限。
- **系统限制**: 文件描述符传递受系统限制，某些特殊文件描述符可能无法传递。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int32_t fd | fd要写入的文件描述符，取值原则：有效的文件描述符，为非负整数。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadFileDescriptor()

```C
int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)
```

**描述：**

从OHIPCParcel对象读取文件描述符。常用于跨进程接收文件句柄、共享内存文件描述符、管道文件描述符等场景。

**调用后的行为**

调用此函数后:

1. 从当前读取位置读取文件描述符信息。
2. 返回一个新的有效的文件描述符。
3. 读取位置自动后移。
4. 新文件描述符指向与原文件相同的资源。

**原理说明**

该函数用于IPC通信中接收文件描述符:

- 通过IPC机制接收对方进程传递的文件描述符。
- 创建一个新的文件描述符副本指向原文件资源。
- 新文件描述符在当前进程中有效。
- 实现跨进程文件共享和访问。

**约束和限制**

- **资源管理**: 读取到的文件描述符需要由接收方管理，使用完毕后应关闭。
- **有效性检查**: 返回的文件描述符应检查是否有效(非负值)。
- **访问权限**: 新文件描述符继承原文件描述符的访问权限。
- **生命周期**: 文件描述符的生命周期独立于Parcel对象。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | int32_t *fd | fd存储读取文件描述符的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_Append()

```C
int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)
```

**描述：**

OHIPCParcel对象数据拼接。常用于合并多个Parcel的数据、数据包组装、分段写入数据的合并等场景。拼接数据受IPC序列化总大小限制（参见[OH_IPCParcel_Create](#oh_ipcparcel_create)）。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数名 |说明                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const [OHIPCParcel](capi-ohipcparcel.md) *data | data源OHIPCParcel对象的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 拼接失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_WriteInterfaceToken()

```C
int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)
```

**描述：**

向OHIPCParcel对象写入接口描述符，用于接口身份校验。常用于IPC通信中的安全验证场景，例如：防止恶意进程发送伪造请求、确保消息发送到正确的服务接口、多接口服务中区分不同的接口调用。

**调用后的行为**

调用此函数后:

1. 将接口描述符字符串写入到OHIPCParcel对象的当前写入位置。
2. 写入位置自动后移相应的字节数。
3. 接口描述符数据被序列化存储在Parcel对象中。

**原理说明**

该函数用于IPC通信中的接口身份验证机制:

- 在发送请求前，客户端通过此函数写入接口描述符。
- 服务端接收请求后，通过ReadInterfaceToken读取并校验。
- 确保请求被发送到正确的服务接口，防止接口混淆。

**约束和限制**

- **内存限制**: 接口描述符字符串长度不能超过Parcel剩余可写空间。
- **空指针检查**: token参数不能为空，否则会返回参数错误。
- **校验时机**: 建议在写入其他请求数据前先写入接口描述符。
- **唯一性**: 接口描述符应为接口的全限定名或唯一标识字符串。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | const char *token | 需要写入的接口描述符信息，不能为空，接口描述符通常为接口的全限定名或唯一标识字符串，用于接口身份校验。字符串长度不能超过parcel剩余可写空间。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 写入失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |

### OH_IPCParcel_ReadInterfaceToken()

```C
int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)
```

**描述：**

从OHIPCParcel对象读取接口描述符信息，用于接口身份校验。

**调用后的行为**

调用此函数后：

1. 从当前读取位置读取接口描述符字符串。
2. 通过用户提供的allocator分配内存存储描述符。
3. 返回描述符地址和长度。
4. 读取位置自动后移。

**原理说明**

该函数用于IPC通信中的接口身份验证：

- 发送方通过WriteInterfaceToken写入接口描述符。
- 接收方通过ReadInterfaceToken读取并校验。
- 确保消息发送到正确的接口。

### 约束和限制

- **内存管理**：token内存由用户提供的allocator分配，使用后必须主动释放。
- **错误处理**：即使函数返回失败，也需要检查token是否为空并释放。
- **内存泄漏风险**：未正确释放token会导致内存泄漏。
- **接口校验**：建议在处理请求前先校验接口描述符。

**系统能力：** SystemCapability.Communication.IPC.Core

**起始版本：** 12

**参数：**

  | 参数项 | 描述                                               |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | parcel OHIPCParcel对象的指针，不能为空。 |
  | char **token | token用于存储接口描述符信息的内存地址，该内存由用户提供的分配器进行内存分配，用户使用完后需要主动释放，不能为空。接口返回失败时，用户依然需要判断该内存是否为空，并主动释放，否则会造成内存泄漏。 |
  | int32_t *len | len存储读取接口描述符的长度（包括结束符），单位：字节，不能为空。 |
  | [OH_IPC_MemAllocator](#oh_ipc_memallocator) allocator | allocator用户指定的用来分配token的内存分配器，不能为空。 |

**返回：**

| 类型 | 说明 |
| ---- | ---- |
| int | 成功返回[OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode)；<br> 参数不合法时返回[OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)；读取失败返回[OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode)。 |
