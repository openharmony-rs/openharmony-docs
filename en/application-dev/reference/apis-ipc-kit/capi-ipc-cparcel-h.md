# ipc_cparcel.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

## Overview

This file provides C APIs for IPC serialization and deserialization, which are used to serialize and deserialize data during IPC communication.

For the corresponding development guide and samples, please refer to [IPC and RPC Development (C/C++)](../../ipc/ipc-capi-development-guideline.md)

**File to include**: <IPCKit/ipc_cparcel.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCParcel](capi-ohipcparcel.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md)| OHIPCParcel | Defines an IPC serialized object.|
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) | OHIPCRemoteProxy | Defines an IPC remote proxy object.|
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) | OHIPCRemoteStub | Defines an IPC remote service object.|

### Function

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [typedef void* (\*OH_IPC_MemAllocator)(int32_t len)](#oh_ipc_memallocator) | [OH_IPC_MemAllocator](#oh_ipc_memallocator) | Defines the type of a memory allocation function.|
| [OHIPCParcel* OH_IPCParcel_Create(void)](#oh_ipcparcel_create) | - | Creates an **OHIPCParcel** object, which cannot exceed 204,800 bytes.|
| [void OH_IPCParcel_Destroy(OHIPCParcel *parcel)](#oh_ipcparcel_destroy) | - | Destroys an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)](#oh_ipcparcel_getdatasize) | - | Obtains the size of the data contained in an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getwritablebytes) | - | Obtains the number of bytes that can be written to an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadablebytes) | - | Obtains the number of bytes that can be read from an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadposition) | - | Obtains the position where data is read in an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getwriteposition) | - | Obtains the position where data is written in an **OHIPCParcel** object.|
| [int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)](#oh_ipcparcel_rewindreadposition) | - | Resets the position to read data in an **OHIPCParcel** object.|
| [int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)](#oh_ipcparcel_rewindwriteposition) | - | Resets the position to write data in an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)](#oh_ipcparcel_writeint8) | - | Writes an int8_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)](#oh_ipcparcel_readint8) | - | Reads an int8_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)](#oh_ipcparcel_writeint16) | - | Writes an int16_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)](#oh_ipcparcel_readint16) | - | Reads an int16_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)](#oh_ipcparcel_writeint32) | - | Writes an int32_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)](#oh_ipcparcel_readint32) | - | Reads an int32_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)](#oh_ipcparcel_writeint64) | - | Writes an int64_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)](#oh_ipcparcel_readint64) | - | Reads an int64_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)](#oh_ipcparcel_writeuint8) | - | Writes a uint8_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)](#oh_ipcparcel_readuint8) | - | Reads a uint8_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)](#oh_ipcparcel_writeuint16) | - | Writes a uint16_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)](#oh_ipcparcel_readuint16) | - | Reads a uint16_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)](#oh_ipcparcel_writeuint32) | - | Writes a uint32_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)](#oh_ipcparcel_readuint32) | - | Reads a uint32_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)](#oh_ipcparcel_writeuint64) | - | Writes a uint64_t value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)](#oh_ipcparcel_readuint64) | - | Reads a uint64_t value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)](#oh_ipcparcel_writefloat) | - | Writes a float value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)](#oh_ipcparcel_readfloat) | - | Reads a float value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)](#oh_ipcparcel_writedouble) | - | Writes a double value to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)](#oh_ipcparcel_readdouble) | - | Reads a double value from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)](#oh_ipcparcel_writestring) | - | Writes a string including a string terminator to an **OHIPCParcel** object.|
| [const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)](#oh_ipcparcel_readstring) | - | Reads a string from an **OHIPCParcel** object. You can obtain the length of the string from **strlen**.|
| [int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)](#oh_ipcparcel_writebuffer) | - | Writes data of the specified length from the memory to an **OHIPCParcel** object.|
| [const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)](#oh_ipcparcel_readbuffer) | - | Reads memory information of the specified length from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)](#oh_ipcparcel_writeremotestub) | - | Writes an **OHIPCRemoteStub** object to an **OHIPCParcel** object.|
| [OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)](#oh_ipcparcel_readremotestub) | - | Reads the **OHIPCRemoteStub** object from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)](#oh_ipcparcel_writeremoteproxy) | - | Writes an **OHIPCRemoteProxy** object to an **OHIPCParcel** object.|
| [OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)](#oh_ipcparcel_readremoteproxy) | - | Reads the **OHIPCRemoteProxy** object from an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)](#oh_ipcparcel_writefiledescriptor) | - | Writes a file descriptor to an **OHIPCParcel** object.|
| [int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)](#oh_ipcparcel_readfiledescriptor) | - | Reads a file descriptor from an **OHIPCParcel** object.|
| [int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)](#oh_ipcparcel_append) | - | Appends data to an **OHIPCParcel** object.|
| [int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)](#oh_ipcparcel_writeinterfacetoken) | - | Writes an interface token to an **OHIPCParcel** object for interface identity verification.|
| [int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcparcel_readinterfacetoken) | - | Reads an interface token from an **OHIPCParcel** object for interface identity verification.|

## Function Description

### OH_IPC_MemAllocator()

```C
typedef void* (*OH_IPC_MemAllocator)(int32_t len);
```

**Description**

Defines the memory allocation function type, which is used to customize the memory allocation policy for IPC communication. This function is commonly used in scenarios that require special memory management, such as shared memory transmission, memory pool management, and limiting memory usage.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | int32_t len  | Length of the memory to be allocated, in bytes. The value must be greater than 0.|

**Returns**

| Type| Description|
| ---- | ---- |
| void* | Returns the address of the memory allocated if the operation is successful; returns NULL otherwise.|

### OH_IPCParcel_Create()

```C
OHIPCParcel* OH_IPCParcel_Create(void)
```

**Description**

Creates an **OHIPCParcel** object for data serialization in IPC communication.

When this function is called:
- An **OHIPCParcel** object is allocated and initialized in memory.
- The object is initially empty, and its serializable size must not exceed 204800 bytes.
- The returned object pointer can be used for subsequent data read and write operations.
- Concurrent access to the same object from multiple threads is not supported.
- Typical usage flow: [OH_IPCParcel_Create](#oh_ipcparcel_create) → Data read/write operations → [OH_IPCParcel_Destroy](#oh_ipcparcel_destroy)

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| OHIPCParcel* | Returns the pointer to the **OHIPCParcel** object created if the operation is successful; returns NULL otherwise.|

### OH_IPCParcel_Destroy()

```C
void OH_IPCParcel_Destroy(OHIPCParcel *parcel)
```

**Description**

Destroys an **OHIPCParcel** object.

When this function is called:
- The memory buffer occupied by the **OHIPCParcel** object is released.
- All data in the object is released. The memory occupied by the object itself is released.
- The input pointer becomes invalid and should not be used any more.
- Before calling this function, ensure that no other thread is using the object.
- It is advised to set the pointer to NULL to avoid dangling pointers.
- This function and [OH_IPCParcel_Create](#oh_ipcparcel_create) must be used in pairs.
- Ensure that all required data has been read before destroying the object.
- Do not call the destruction function multiple times for the same object.
- Only objects created by [OH_IPCParcel_Create](#oh_ipcparcel_create) can be destroyed.
- The object cannot be accessed after destruction.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object to be destroyed. It cannot be NULL.|

### OH_IPCParcel_GetDataSize()

```C
int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)
```

**Description**

Obtains the size of the data contained in an **OHIPCParcel** object. This function is commonly used in scenarios such as monitoring data transmission progress, checking whether the IPC serialization size limit has been exceeded, and debugging data read/write processes.

When this function is called:
- The total number of bytes of data that has been written to the **OHIPCParcel** object is calculated. 
- The total size of the written data is returned.
- The read/write position and the data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Total size of data that has been written to the **OHIPCParcel** object, in bytes. If the parameter is invalid, **-1** is returned.|

### OH_IPCParcel_GetWritableBytes()

```C
int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can be written to an **OHIPCParcel** object. This function is commonly used in scenarios such as checking whether there is enough space to write more data, preventing write overflow, and performing pre-checks before batch writes.

When this function is called:
- The size of the remaining writable space in the **OHIPCParcel** object is calculated.
- The number of writable bytes is returned.
- Neither the read/write position nor the data content of the **OHIPCParcel** object is changed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Size of the writable bytes, in bytes. If the parameter is invalid, **-1** is returned.|

### OH_IPCParcel_GetReadableBytes()

```C
int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can be read from an **OHIPCParcel** object. This function is commonly used in scenarios such as checking how much data is available to read, reading data cyclically, and debugging the data reading process.

When this function is called:
- The number of bytes of unread data in the **OHIPCParcel** object is calculated.
- The number of readable bytes is returned.
- Neither the read/write position nor the data content of the **OHIPCParcel** object is changed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Size of the readable bytes, in bytes. If the parameter is invalid, **-1** is returned.|

### OH_IPCParcel_GetReadPosition()

```C
int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the position where data is read in an **OHIPCParcel** object. This function is commonly used in scenarios such as recording the read position for later restoration, working with **RewindReadPosition** to enable repeated reads, and debugging the data reading progress.

When this function is called:
- The current read position of the **OHIPCParcel** object is returned.
- The read position and data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core
 
**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Current read position, in bytes. If the parameter is invalid, **-1** is returned.|

### OH_IPCParcel_GetWritePosition()

```C
int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the position where data is written in an **OHIPCParcel** object. This function is commonly used in scenarios such as recording the write position, working with **RewindWritePosition** to correct write errors, and debugging the data write progress.

When this function is called:
- The current write position of the **OHIPCParcel** object is returned.
- The write position and data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | --------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Current write position, in bytes. If the parameter is invalid, **-1** is returned.|

### OH_IPCParcel_RewindReadPosition()

```c
int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)
```

**Description**

Resets the read position of the **OHIPCParcel** object to the specified position. This function is commonly used in scenarios where data needs to be parsed repeatedly.

When this function is called:
- The read position pointer is moved to the position specified by **newReadPos**, which must be within the range of [0, current data size].
- The data already written remains unchanged.
- Subsequent read operations start from the new position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint32_t newReadPos | New position to read data, in bytes. The value ranges from 0 to the current data size. If the value is out of range, the **OH_IPC_CHECK_PARAM_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.|

### OH_IPCParcel_RewindWritePosition()

```C
int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)
```

**Description**

Resets the write position of the **OHIPCParcel** object to the specified position. This function is usually used in scenarios where data errors need to be corrected after data is written, data needs to be rewritten by segment, or some write operations need to be canceled.

When this function is called:
- The write position pointer is moved to the position specified by **newWritePos**, which must be within the range of [0, current data size].
- Resetting the position may cause some data to be overwritten or invalidated. Use this function with caution.
- Subsequent write operations start from the new position.
- Resetting the write position does not affect the read position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint32_t newWritePos | New position to write data, in bytes. The value ranges from 0 to the current data size. If the value is out of range, the **OH_IPC_CHECK_PARAM_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.|

### OH_IPCParcel_WriteInt8()

```C
int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)
```

**Description**

Writes an int8_t value to an **OHIPCParcel** object. Concurrent access to the same object from multiple threads is not supported. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadInt8](#oh_ipcparcel_readint8) must be used in pairs.
- Calling sequence: First you call **OH_IPCParcel_WriteInt()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt8](#oh_ipcparcel_readint8) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int8_t value | int8_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| -----| ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt8()

```C
int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)
```

**Description**

Reads an int8_t value from an **OHIPCParcel** object. Concurrent access to the same object from multiple threads is not supported.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int8_t *value | Pointer to store the read int8_t data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteInt16()

```C
int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)
```

**Description**

Writes an int16_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadInt16](#oh_ipcparcel_readint16) must be used in pairs.
- Calling sequence: First you call **OH_IPCParcel_WriteInt16()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt16](#oh_ipcparcel_readint16) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int16_t value | int16_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt16()

```C
int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)
```

**Description**

Reads an int16_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int16_t *value | Pointer to store the read int16_t data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteInt32()

```C
int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)
```

**Description**

Writes an int32_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit. For details, see [OH_IPCParcel_Create](#oh_ipcparcel_create).

- This function and [OH_IPCParcel_ReadInt32](#oh_ipcparcel_readint32) must be used in pairs.
- Calling sequence: First you call **WriteInt()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt32](#oh_ipcparcel_readint32) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int32_t value | int32_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt32()

```C
int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)
```

**Description**

Reads an int32_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int32_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteInt64()

```C
int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)
```

**Description**

Writes an int64_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadInt64](#oh_ipcparcel_readint64) must be used in pairs.
- Calling sequence: First you call **WriteInt()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt64](#oh_ipcparcel_readint64) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int64_t value | int64_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt64()

```C
int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)
```

**Description**

Reads an int64_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int64_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint8()

```C
int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)
```

**Description**

Writes a uint8_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadUint8](#oh_ipcparcel_readuint8) must be used in pairs.
- Calling sequence: First you call **WriteUint()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadUint8](#oh_ipcparcel_readuint8) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint8_t value | uint8_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint8()

```C
int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)
```

**Description**

Reads a uint8_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint8_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint16()

```C
int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)
```

**Description**

Writes a uint16_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadUint16](#oh_ipcparcel_readuint16) must be used in pairs.
- Calling sequence: First you call **WriteUint()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadUint16](#oh_ipcparcel_readuint16) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint16_t value | uint16_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint16()

```C
int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)
```

**Description**

Reads a uint16_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint16_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint32()

```C
int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)
```

**Description**

Writes a uint32_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadUint32](#oh_ipcparcel_readuint32) must be used in pairs.
- Calling sequence: First you call **WriteUint()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadUint32](#oh_ipcparcel_readuint32) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint32_t value | uint32_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint32()

```C
int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)
```

**Description**

Reads a uint32_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint32_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint64()

```C
int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)
```

**Description**

Writes a uint64_t value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadUint64](#oh_ipcparcel_readuint64) must be used in pairs.
- Calling sequence: First you call **WriteUint()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadUint64](#oh_ipcparcel_readuint64) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint64_t value | uint64_t data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint64()

```C
int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)
```

**Description**

Reads a uint64_t value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | uint64_t *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteFloat()

```C
int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)
```

**Description**

Writes a float value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadFloat](#oh_ipcparcel_readfloat) must be used in pairs.
- Calling sequence: First you call **WriteFloat()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadFloat](#oh_ipcparcel_readfloat) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | float value | float data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadFloat()

```C
int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)
```

**Description**

Reads a float value from an **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | float *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteDouble()

```C
int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)
```

**Description**

Writes a double value to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

- This function and [OH_IPCParcel_ReadDouble](#oh_ipcparcel_readdouble) must be used in pairs.
- Calling sequence: First you call **WriteDouble()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadDouble](#oh_ipcparcel_readdouble) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | double value | Double data value to be written, which is used for IPC data serialization.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadDouble()

```C
int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)
```

**Description**

Reads a double value from an **OHIPCParcel** object. After this function is called, an 8-byte double value is read from the current read position. The read position is automatically advanced by 8 bytes, and the read value is stored in the memory pointed to by the **value** pointer.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | double *value | Pointer to store the read data. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteString()

```C
int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)
```

**Description**

Writes a string including a string terminator to an **OHIPCParcel** object. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The string content (including the null terminator '\0') is written to the current write position of the **OHIPCParcel** object.
- The write position is automatically advanced by (string length + 1) bytes.
- The string data is serialized and stored in the **OH_IPCParcel** object. No manual memory management is required by the caller.
- The length of the string to be written is subject to the IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create); up to 204,800 bytes).
- The **str** parameter must not be NULL; otherwise, a parameter error is returned.
- Encoding note: The string must be encoded in valid UTF-8 or ASCII.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const char *str | Pointer to the string to write, which is used for string data transmission in IPC communication. It cannot be NULL. The length range is [0, 204800], in bytes (including the null terminator. The actual length is dynamically affected by the data already written to the parcel and the overhead of the terminator). The length of the written string is subject to the IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)). If the limit is exceeded, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadString()

```C
const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)
```

**Description**

Reads a string from an **OHIPCParcel** object. You can obtain the length of the string from **strlen**.

When this function is called:
1. The string content is read from the current read position.
2. The memory address pointer to the string is returned.
3. The read position is automatically advanced to the position after the string terminator.
4. The memory of the returned string is managed by the **OHIPCParcel** object, so the caller does not need to free it.
5. The validity of the string is bound to the **OHIPCParcel** object. Once the object is destroyed, the string becomes invalid.
6. If the parameter is invalid or the read operation fails, NULL is returned. You should check the return value.
7. The string length can be obtained via **strlen**, and the string content can be accessed directly using the returned pointer.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| const char* | Returns the address of the string read if the operation is successful; returns NULL if the operation fails or invalid parameters are found.|

### OH_IPCParcel_WriteBuffer()

```C
int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)
```

**Description**

Writes data of the specified length from the memory to an **OHIPCParcel** object. This function is commonly used in scenarios such as writing binary data, image data, custom structures, and shared memory content. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The memory data pointed to by **buffer** is written to the current write position of the **OHIPCParcel** object.
- The write position is automatically advanced by **len** bytes.
- The memory data is serialized and stored in the **OHIPCParcel** object.
- The buffer must have sufficient memory space allocated in advance, and the memory must be valid.
- The value of **len** must be within the range [0, available writable bytes of the parcel]. If the value is out of range, an error is returned.
- **buffer** must not be NULL; otherwise, a parameter error is returned.
- The data being written must remain valid during the call. After the write operation is completed, there is no such restriction.
- After the write operation is completed, the memory of **buffer** is managed by the caller, and the parcel stores an internal copy.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const uint8_t *buffer  | Starting address of the memory to be written. This is the starting address of the data buffer to be written, pointing to the binary data to be transmitted via IPC. It cannot be NULL. The buffer must have sufficient memory space allocated in advance.|
  | int32_t len | Length of the data to be written, in bytes. The value range is [0, available writable bytes of the parcel]. The size of the written data is subject to the IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)). If a negative value is passed, the **OH_IPC_CHECK_PARAM_ERROR** error is returned. If the value exceeds the available writable bytes, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadBuffer()

```C
const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)
```

**Description**

Reads memory information of the specified length from an **OHIPCParcel** object. This function is commonly used in scenarios such as reading binary data, image data, custom structures, and shared memory content.

When this function is called:
- **len** bytes of memory data are read from the current read position. The value of **len** must be in the range of [0, the number of readable bytes in the parcel]. If the value is out of range, NULL is returned.
- A pointer to the internal data of the **OHIPCParcel** object is returned.
- The read position is automatically advanced by **len** bytes.
- The returned memory is managed by the **OHIPCParcel** object, so the caller does not need to free it.
- Lifecycle: The data validity is bound to the **OHIPCParcel** object. After the object is destroyed, the data becomes invalid.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int32_t len | Length of memory to be read, in bytes. The value range is [0, the number of remaining readable bytes in the parcel]. If the value exceeds the readable bytes, NULL is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| const uint8_t* | Returns the memory address read if the operation is successful; returns NULL if invalid parameters are found or **len** exceeds the readable length of **parcel**.|

### OH_IPCParcel_WriteRemoteStub()

```C
int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)
```

**Description**

Writes an **OHIPCRemoteStub** object to an **OHIPCParcel** object. This function is commonly used in scenarios such as passing service objects across processes, implementing remote calls in an IPC server, and sharing service objects. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The reference information of the **OHIPCRemoteStub** object is written into the **OHIPCParcel** object, and the write position is automatically advanced.
- The reference information of the **Stub** object is serialized and stored.
- Calling sequence: First you call **WriteRemoteStub()** to write the **Stub** object, and then the receiving side calls [OH_IPCParcel_ReadRemoteStub](#oh_ipcparcel_readremotestub) to read the object.
- Incorrect pairing: If the functions are not called in the correct sequence or the calls are not properly paired, the receiving side will be unable to correctly obtain the reference to the **Stub** object, which will affect the establishment of IPC communication.
- Object validity: **stub** must not be NULL and must be a valid pointer to an **OHIPCRemoteStub** object; otherwise, a parameter error is returned.
- Reference management: After the write operation, the reference count of the **Stub** object is incremented. You must ensure that the **Stub** object has a sufficient lifecycle.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | Pointer to the **OHIPCRemoteStub** object to write. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadRemoteStub()

```C
OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)
```

**Description**

Reads the **OHIPCRemoteStub** object from an **OHIPCParcel** object. This function is commonly used in scenarios such as receiving service objects across processes, implementing remote calls in an IPC server, and sharing service objects.

When this function is called:
- The reference information of the **Stub** object is read from the current read position.
- The pointer to the **OHIPCRemoteStub** object is returned.
- The read position is automatically advanced.
- This function and [OH_IPCParcel_WriteRemoteStub](#oh_ipcparcel_writeremotestub) must be used in pairs.
- The returned pointer to the **Stub** object is managed by the system and must be used in accordance with IPC specifications.
- If the read operation fails, NULL is returned. The caller should check the return value.
- This function is commonly used to receive the **Stub** object passed from the server side for establishing IPC communication.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| OHIPCRemoteStub* | Returns the pointer to the **OHIPCRemoteStub** object read if the operation is successful; returns NULL otherwise.|

### OH_IPCParcel_WriteRemoteProxy()

```C
int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)
```

**Description**

Writes an **OHIPCRemoteProxy** object to an **OHIPCParcel** object. This function is commonly used in scenarios such as passing proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The reference information of the **OHIPCRemoteProxy** object is written to the **OHIPCParcel** object.
- The write position is automatically advanced.
- The reference information of the **OHIPCRemoteProxy** object is serialized and stored.
- Calling sequence: First you call [OH_IPCParcel_WriteRemoteProxy](#oh_ipcparcel_writeremoteproxy) to write the **OHIPCRemoteProxy** object, and then the receiving side calls [OH_IPCParcel_ReadRemoteProxy](#oh_ipcparcel_readremoteproxy) to read the object.
- Incorrect pairing: If the functions are not called in the correct sequence or the calls are not properly paired, the receiving side will be unable to correctly obtain the reference to the **OHIPCRemoteProxy** object, which will affect the establishment of IPC communication.
- Object validity: **proxy** must not be NULL and must be a valid pointer to an **OHIPCRemoteProxy** object; otherwise, a parameter error is returned.
- Reference management: After the write operation, the reference count of the **OHIPCRemoteProxy** object is incremented. You must ensure that the **OHIPCRemoteProxy** object has a sufficient lifecycle.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to write. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadRemoteProxy()

```C
OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)
```

**Description**

Reads the **OHIPCRemoteProxy** object from an **OHIPCParcel** object. This function is commonly used in scenarios such as receiving proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects.

When this function is called:
- The reference information of the **OHIPCRemoteProxy** object is read from the current read position.
- The pointer to the **OHIPCRemoteProxy** object is returned.
- The read position is automatically advanced.
- This function and [OH_IPCParcel_WriteRemoteProxy](#oh_ipcparcel_writeremoteproxy) must be used in pairs.
- The returned pointer to the **OHIPCRemoteProxy** object is managed by the system and must be used in accordance with IPC specifications.
- If the read operation fails, NULL is returned. The caller should check the return value.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| OHIPCRemoteProxy* | Returns the pointer to the **OHIPCRemoteProxy** object created if the operation is successful; returns NULL otherwise.|

### OH_IPCParcel_WriteFileDescriptor()

```C
int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)
```

**Description**

Writes a file descriptor to an **OHIPCParcel** object. This function is commonly used in scenarios such as passing file handles across processes, shared memory file descriptors, and pipe file descriptors. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- A copy of the file descriptor is written to the **OHIPCParcel** object.
- The write position is automatically advanced.
- The file descriptor information is serialized for storage and can be transferred during IPC communication.
- Call sequence: You call [OH_IPCParcel_WriteFileDescriptor](#oh_ipcparcel_writefiledescriptor) to write the file descriptor, and then the receiving side call
- [OH_IPCParcel_ReadFileDescriptor](#oh_ipcparcel_readfiledescriptor) to read it.
- Incorrect pairing: If the functions are not called in sequence or the calls are not properly paired, the receiving side cannot obtain the correct file descriptor, affecting cross-process file sharing and access.
- File descriptor validity: **fd** must be a valid non-negative integer file descriptor.
- Resource management: After the write operation is complete, the original file descriptor is still managed by the caller and needs to be closed by the caller.
- Permission transfer: The file descriptor obtained by the receiving side has the same access permissions.
- System restrictions: File descriptor transfer is subject to system restrictions, and some special file descriptors may not be transferred.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int32_t fd | File descriptor to write. The value must be a valid file descriptor, which is a non-negative integer. If a negative value or an invalid file descriptor is passed, the **OH_IPC_CHECK_PARAM_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadFileDescriptor()

```C
int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)
```

**Description**

Reads a file descriptor from an **OHIPCParcel** object. This function is commonly used in scenarios such as receiving file handles across processes, shared memory file descriptors, and pipe file descriptors. Concurrent access to the same object from multiple threads is not supported.


When this function is called:
- The file descriptor information is read from the current read position.
- A new valid file descriptor is returned.
- The read position is automatically advanced.
- The new file descriptor points to the same resource as the original file and inherits the access permissions of the original file descriptor.
- This function and [OH_IPCParcel_WriteFileDescriptor](#oh_ipcparcel_writefiledescriptor) must be used in pairs.
- The read file descriptor must be managed by the receiver and closed after use.
- The returned file descriptor should be checked for validity (non-negative value).
- The lifecycle of the file descriptor is independent of the **OHIPCParcel** object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | int32_t *fd | Pointer to store the read file descriptor. It cannot be NULL. Before reading, ensure that valid file descriptor data has been written to the parcel.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_Append()

```C
int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)
```

**Description**

Appends data to an **OHIPCParcel** object. This function is commonly used in scenarios such as merging data from multiple parcels, packet assembly, and merging data written in segments. The data appended is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The data from the source **OHIPCParcel** object (specified by **data**) is copied and appended to the current write position of the target **OHIPCParcel** object (specified by **parcel**).
- The write position of the target **OHIPCParcel** object is automatically advanced by the number of bytes of the appended data.
- The read position and the content of the source **OHIPCParcel** object remain unchanged.
- The append operation copies the source data to the target parcel, and the memory is managed by the target parcel.
- The total size of the data after appending must not exceed the IPC serialization limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).
- Neither the **parcel** parameter nor the **data** parameter can be NULL; otherwise, a parameter error is returned.
- Both parameters must be valid objects created by [OH_IPCParcel_Create](#oh_ipcparcel_create).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to data source **OHIPCParcel** object. It cannot be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the concatenation fails.|

### OH_IPCParcel_WriteInterfaceToken()

```C
int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)
```

**Description**

Writes an interface token to an **OHIPCParcel** object for interface identity verification. This function is commonly used in security verification scenarios in IPC communication, such as preventing malicious processes from sending forged requests, ensuring that messages are sent to the correct service API, and distinguishing different API calls in multi-API services. Concurrent access to the same object from multiple threads is not supported. The data written is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create](#oh_ipcparcel_create)).

When this function is called:
- The interface token string is written to the current write position of the **OHIPCParcel** object.
- The write position is automatically advanced by the corresponding number of bytes.
- The interface token data is serialized and stored in the **OHIPCParcel** object.
- The length of the interface token string must not exceed the remaining writable space of the parcel.
- Calling sequence: The client first calls [OH_IPCParcel_WriteInterfaceToken](#oh_ipcparcel_writeinterfacetoken) to write the interface token, and then the server calls [OH_IPCParcel_ReadInterfaceToken](#oh_ipcparcel_readinterfacetoken) to read and verify it.
- If the calls are not made in the correct order or are not properly paired, the interface identity verification will fail, and the request may be rejected or sent to the wrong interface, resulting in interface confusion.
- The **token** parameter must not be NULL; otherwise, a parameter error is returned.
- It is advised to write the interface token before writing other request data.
- The interface token should be the fully qualified name or a unique identifier string of an interface.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | const char *token | Pointer to the interface token to write. It cannot be NULL. The interface token is usually the fully qualified name or a unique identifier string of an interface, and is used for interface identity verification. The string length range is [0, remaining writable space of the parcel]. The unit is bytes. If the limit is exceeded, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInterfaceToken()

```C
int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Reads an interface token from an **OHIPCParcel** object for interface identity verification.

When this function is called:
- This function and [OH_IPCParcel_WriteInterfaceToken](#oh_ipcparcel_writeinterfacetoken) must be used in pairs.
- The interface token string is read from the current read position.
- The memory for storing the interface token is allocated using the user-provided allocator.
- The address and length of the interface token are returned.
- The read position is automatically advanced.
- The memory of **token** is allocated by the user-provided allocator, and it must be explicitly freed after use.
- Even if the function returns a failure, you should check whether **token** is not NULL and free it accordingly.
- Failure to properly free **token** may result in memory leaks.
- It is advised to verify the interface token before processing requests.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description                                              |
  | ------ | -------------------------------------------------- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL.|
  | char **token | Memory address for storing the interface token information. The memory is allocated using the user-provided allocator, and must be explicitly freed by the user after use. It must not be NULL. If an error code is returned, you still need to check whether the memory is empty and release the memory. Otherwise, memory leaks may occur.|
  | int32_t *len | Pointer to store the length of the read interface token (including the null terminator). The unit is bytes. It must not be NULL.|
  | [OH_IPC_MemAllocator](#oh_ipc_memallocator) allocator | Memory allocator specified by the user for allocating the memory for **token**. It must not be NULL.|

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|
