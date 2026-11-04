# ipc_cparcel.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=563b8be563e11a9d9d559f338c53d2269358d4f7 translatedAt=2026-11-04T03:51:20.390Z pushedAt=2026-11-04T10:13:14.892Z nl=1 -->

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
| [typedef void* (\*OH_IPC_MemAllocator)(int32_t len)](#oh_ipc_memallocator) | [OH_IPC_MemAllocator()](#oh_ipc_memallocator) | Defines the memory allocation function type, used to customize the memory allocation strategy in IPC communication. Commonly used when needing special memory management, for example, shared memory transfer, memory pool management, and limiting the upper bound of memory usage. |
| [OHIPCParcel* OH_IPCParcel_Create(void)](#oh_ipcparcel_create) | - | Creates an OHIPCParcel object for data serialization in IPC communication. |
| [void OH_IPCParcel_Destroy(OHIPCParcel *parcel)](#oh_ipcparcel_destroy) | - | Destroys an **OHIPCParcel** object.|
| [int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)](#oh_ipcparcel_getdatasize) | - | Obtains the size of the data contained in the OHIPCParcel object. Commonly used for checking data transfer progress, checking whether the IPC total serialization size limit is exceeded, and debugging the data read/write process. |
| [int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getwritablebytes) | - | Obtains the number of bytes that can be written to the OHIPCParcel object. Commonly used for checking whether there is still space to write more data, preventing write overflow, and pre-checking before batch writing. |
| [int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadablebytes) | - | Obtains the number of bytes that can still be read from the OHIPCParcel object. Commonly used for checking how much data remains to be read, reading data in a loop, and debugging the data read process. |
| [int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadposition) | - | Obtains the current read position of the OHIPCParcel object. Commonly used for recording the read position for later restoration, implementing repeated reads together with OH_IPCParcel_RewindReadPosition(), and debugging the data read progress. |
| [int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getwriteposition) | - | Obtains the current write position of the OHIPCParcel object. Commonly used for recording the write position, correcting write errors together with OH_IPCParcel_RewindWritePosition(), and debugging the data write progress. |
| [int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)](#oh_ipcparcel_rewindreadposition) | - | Resets the read position of the OHIPCParcel object to the specified position. Commonly used when needing to parse data repeatedly. |
| [int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)](#oh_ipcparcel_rewindwriteposition) | - | Resets the write position of the OHIPCParcel object to the specified position. Commonly used for correcting preceding data errors discovered after writing, implementing segmented rewriting of data, and undoing part of the write operations. |
| [int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)](#oh_ipcparcel_writeint8) | - | Writes an int8_t value to the OHIPCParcel object. Does not support multiple threads concurrently accessing the same object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)](#oh_ipcparcel_readint8) | - | Reads an int8_t value from the OHIPCParcel object. Does not support multiple threads concurrently accessing the same object. |
| [int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)](#oh_ipcparcel_writeint16) | - | Writes an int16_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)](#oh_ipcparcel_readint16) | - | Reads an int16_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)](#oh_ipcparcel_writeint32) | - | Writes an int32_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)](#oh_ipcparcel_readint32) | - | Reads an int32_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)](#oh_ipcparcel_writeint64) | - | Writes an int64_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)](#oh_ipcparcel_readint64) | - | Reads an int64_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)](#oh_ipcparcel_writeuint8) | - | Writes a uint8_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)](#oh_ipcparcel_readuint8) | - | Reads a uint8_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)](#oh_ipcparcel_writeuint16) | - | Writes a uint16_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)](#oh_ipcparcel_readuint16) | - | Reads a uint16_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)](#oh_ipcparcel_writeuint32) | - | Writes a uint32_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)](#oh_ipcparcel_readuint32) | - | Reads a uint32_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)](#oh_ipcparcel_writeuint64) | - | Writes a uint64_t value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)](#oh_ipcparcel_readuint64) | - | Reads a uint64_t value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)](#oh_ipcparcel_writefloat) | - | Writes a float value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)](#oh_ipcparcel_readfloat) | - | Reads a float value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)](#oh_ipcparcel_writedouble) | - | Writes a double value to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)](#oh_ipcparcel_readdouble) | - | Reads a double value from the OHIPCParcel object. |
| [int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)](#oh_ipcparcel_writestring) | - | Writes a string, including the string terminator, to the OHIPCParcel object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)](#oh_ipcparcel_readstring) | - | Reads a string from an **OHIPCParcel** object. You can obtain the length of the string from **strlen**.|
| [int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)](#oh_ipcparcel_writebuffer) | - | Writes memory information of the specified length to the OHIPCParcel object. Commonly used for writing binary data, image data, custom structures, and shared memory content. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create). |
| [const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)](#oh_ipcparcel_readbuffer) | - | Reads memory information of the specified length from the OHIPCParcel object. Commonly used for reading binary data, image data, custom structures, and shared memory content. |
| [int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)](#oh_ipcparcel_writeremotestub) | - | Writes an OHIPCRemoteStub object to the OHIPCParcel object. Commonly used for transferring service objects across processes, implementing remote calls on the IPC server side, and sharing service objects. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)](#oh_ipcparcel_readremotestub) | - | Reads an OHIPCRemoteStub object from the OHIPCParcel object. Commonly used for receiving service objects across processes, implementing remote calls on the IPC server side, and sharing service objects. |
| [int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)](#oh_ipcparcel_writeremoteproxy) | - | Writes an OHIPCRemoteProxy object to the OHIPCParcel object. Commonly used for transferring proxy objects across processes, implementing remote calls on the IPC client side, and sharing proxy objects. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)](#oh_ipcparcel_readremoteproxy) | - | Reads an OHIPCRemoteProxy object from the OHIPCParcel object. Commonly used for receiving proxy objects across processes, implementing remote calls on the IPC client side, and sharing proxy objects. |
| [int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)](#oh_ipcparcel_writefiledescriptor) | - | Writes a file descriptor to the OHIPCParcel object. Commonly used for transferring file handles, shared memory file descriptors, and pipe file descriptors across processes. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)](#oh_ipcparcel_readfiledescriptor) | - | Reads a file descriptor from the OHIPCParcel object. Commonly used for receiving file handles, shared memory file descriptors, and pipe file descriptors across processes. Does not support multiple threads concurrently accessing the same object. |
| [int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)](#oh_ipcparcel_append) | - | Appends the data of an OHIPCParcel object. Commonly used for merging data of multiple Parcels, assembling data packets, and merging segmented written data. The appended data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)](#oh_ipcparcel_writeinterfacetoken) | - | Writes an interface descriptor to the OHIPCParcel object for interface identity verification. Commonly used for security verification in IPC communication, for example, preventing malicious processes from sending forged requests, ensuring that messages are sent to the correct service interface, and distinguishing different interface calls in a multi-interface service. Does not support multiple threads concurrently accessing the same object. The written data is subject to the IPC total serialization size limit (see OH_IPCParcel_Create()). |
| [int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcparcel_readinterfacetoken) | - | Reads an interface token from an **OHIPCParcel** object for interface identity verification.|

## Function Description

### OH_IPC_MemAllocator()

```C
typedef void* (*OH_IPC_MemAllocator)(int32_t len)
```

**Description**

Defines the memory allocation function type, which is used to customize the memory allocation policy for IPC communication. This function is commonly used in scenarios that require special memory management, such as shared memory transmission, memory pool management, and limiting memory usage.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | int32_t len  | Length of the memory to be allocated, in bytes. The value must be greater than 0. |

**Returns**

| Type| Description|
| ---- | ---- |
| void* | Returns the address of the memory allocated if the operation is successful; returns NULL otherwise.|

### OH_IPCParcel_Create()

```C
OHIPCParcel* OH_IPCParcel_Create(void)
```

**Description**

Creates an [OHIPCParcel](capi-ohipcparcel.md) object for data serialization in IPC communication.

Call this function to:
- Allocate and initializes an [OHIPCParcel](capi-ohipcparcel.md) object in memory.
- The object is initially empty, and its serializable size cannot exceed 204800 bytes.
- Return the object pointer for subsequent data read and write operations.
- Multiple-thread concurrent access to the same object is not supported.
- Typical usage flow: OH_IPCParcel_Create() → data read/write operations → [OH_IPCParcel_Destroy()](#oh_ipcparcel_destroy).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**

| Type| Description|
| ---- | ---- |
| [OHIPCParcel](capi-ohipcparcel.md)* | OHIPCParcel object pointer on success; NULL on failure. |

### OH_IPCParcel_Destroy()

```C
void OH_IPCParcel_Destroy(OHIPCParcel *parcel)
```

**Description**

Destroys the [OHIPCParcel](capi-ohipcparcel.md) object.

Call this function to:
- Release the memory buffer occupied by the [OHIPCParcel](capi-ohipcparcel.md) object.
- Clear all data inside the object and releases the memory of the object itself.
- The passed pointer becomes invalid and should no longer be used.
- Check before use: ensure that no other thread is using the object.
- Set the pointer to NULL after destruction to avoid a dangling pointer.
- Must be used in pairs with [OH_IPCParcel_Create()](#oh_ipcparcel_create).
- Destruction timing: Ensure that all required data has been read before destruction.
- Multiple destruction: Do not call the destroy function multiple times on the same object.
- Only objects created by [OH_IPCParcel_Create()](#oh_ipcparcel_create) can be destroyed.
- The object cannot be accessed after destruction.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object to be destroyed. It cannot be null. |

### OH_IPCParcel_GetDataSize()

```C
int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)
```

**Description**

Obtains the size of the data contained in the [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for monitoring data transfer progress, checking whether the IPC serialization size limit is exceeded, and debugging the data read/write process.

Call this function:
- Calculates the total number of bytes of data written to the Parcel object.
- Returns the total size of the written data.
- Keeps the read/write position and data content unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type | Description |
| ---- | ---- |
| int | Returns the cumulative size of data written to the Parcel object, in bytes. Returns -1 if invalid parameters are found. |

### OH_IPCParcel_GetWritableBytes()

```C
int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can be written to the [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for checking whether there is still space to write more data, preventing write overflow, and pre-checking before batch writing.

Call this function:
- Calculates the size of the remaining writable space in the Parcel object.
- Returns the number of writable bytes.
- Does not change the read/write position or data content of the Parcel object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Size of the writable bytes, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetReadableBytes()

```C
int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can still be read from the [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for checking how much data remains to be read, reading data in a loop, debugging the data reading process, and other scenarios.

Call this function:
- Calculates the number of unread bytes in the Parcel object.
- Returns the number of readable bytes.
- Does not change the read/write position or data content of the Parcel object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Size of the readable bytes, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetReadPosition()

```C
int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the current read position of the [OHIPCParcel](capi-ohipcparcel.md) object. It is commonly used for recording the read position for later restoration, implementing repeated reads in combination with [OH_IPCParcel_RewindReadPosition()](#oh_ipcparcel_rewindreadposition), and debugging the data read progress.

Call this function:
- Returns the current read position value of the Parcel object.
- Does not change the read position or data content.

**System capability**: SystemCapability.Communication.IPC.Core
 
**Since**: 12

**Parameters**

  | Name| Description|
  | ---- | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Current read position, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetWritePosition()

```C
int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the current write position of the [OHIPCParcel](capi-ohipcparcel.md) object. It is commonly used for recording the write position, correcting write errors in conjunction with [OH_IPCParcel_RewindWritePosition()](#oh_ipcparcel_rewindwriteposition), and tracking the progress of debug data writing.

Calling this function:
- Returns the current write position value of the Parcel object.
- Does not change the write position or data content.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ----- | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Current write position, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_RewindReadPosition()

```c
int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)
```

**Description**

Resets the read position of the [OHIPCParcel](capi-ohipcparcel.md) object to the specified position. It is commonly used in scenarios where data needs to be parsed repeatedly.

Call this function:
- The read position pointer moves to the position specified by newReadPos, which must be within the range [0, current data size].
- The written data remains unchanged.
- Subsequent read operations start from the new position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name | Description |
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint32_t newReadPos | New read position, in the range [0, current data size], in bytes. If the value is out of range, OH_IPC_CHECK_PARAM_ERROR is returned. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.|

### OH_IPCParcel_RewindWritePosition()

```C
int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)
```

**Description**

Resets the write position of the [OHIPCParcel](capi-ohipcparcel.md) object to the specified position. It is commonly used in scenarios such as correcting erroneous preceding data after writing, performing partial data rewriting, and undoing some write operations.

Call this function:
- The write position pointer moves to the position specified by newWritePos, which must be within the range [0, current data size].
- Resetting the position may cause some data to be overwritten or become invalid, so use it with caution.
- Subsequent write operations start from the new position.
- Resetting the write position does not affect the read position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint32_t newWritePos | New write position, in the range [0, current data size], in bytes. Returns OH_IPC_CHECK_PARAM_ERROR if the value is out of range. |

**Returns**

| Type | Description |
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.

### OH_IPCParcel_WriteInt8()

```C
int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)
```

**Description**

Writes an int8_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. Does not support multiple threads accessing the same object concurrently. The written data is subject to the total serialization size limit of IPC (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with the [OH_IPCParcel_ReadInt8()](#oh_ipcparcel_readint8) method.
- Call sequence: call OH_IPCParcel_WriteInt8() to write data first, and then the receiving end calls [OH_IPCParcel_ReadInt8()](#oh_ipcparcel_readint8) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int8_t value | int8_t data value to write, used for data serialization in IPC communication. |

**Returns**

| Type | Description |
| -----| ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInt8()

```C
int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)
```

**Description**

Reads an int8_t value from the [OHIPCParcel](capi-ohipcparcel.md) object. Concurrent access to the same object from multiple threads is not supported.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int8_t *value | Pointer to the int8_t data read, which cannot be null. |

**Returns**

| Type | Description |
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteInt16()

```C
int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)
```

**Description**

Writes an int16_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the IPC total serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with [OH_IPCParcel_ReadInt16()](#oh_ipcparcel_readint16).
- Call sequence: call OH_IPCParcel_WriteInt16() to write the data first, and then the receiving end calls [OH_IPCParcel_ReadInt16()](#oh_ipcparcel_readint16) to read the data.
- Incorrect pairing: If the calls are not made in order or the read type does not match, the read fails or a data error occurs.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int16_t value | int16_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt16()

```C
int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)
```

**Description**

Reads an int16_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int16_t *value | Pointer used to store the read int16_t data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteInt32()

```C
int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)
```

**Description**

Writes an int32_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with [OH_IPCParcel_ReadInt32()](#oh_ipcparcel_readint32).
- Call sequence: first call OH_IPCParcel_WriteInt32() to write data, and then the receiving end calls [OH_IPCParcel_ReadInt32()](#oh_ipcparcel_readint32) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int32_t value | int32_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt32()

```C
int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)
```

**Description**

Reads an int32_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int32_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteInt64()

```C
int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)
```

**Description**

Writes an int64_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with [OH_IPCParcel_ReadInt64()](#oh_ipcparcel_readint64).
- Calling sequence: call OH_IPCParcel_WriteInt64() to write data first, and then the receiving end calls [OH_IPCParcel_ReadInt64()](#oh_ipcparcel_readint64) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int64_t value | int64_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInt64()

```C
int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)
```

**Description**

Reads an int64_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int64_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint8()

```C
int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)
```

**Description**

Writes a uint8_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with the [OH_IPCParcel_ReadUint8()](#oh_ipcparcel_readuint8) method.
- Calling sequence: first call OH_IPCParcel_WriteUint8() to write data, and then the receiving end calls [OH_IPCParcel_ReadUint8()](#oh_ipcparcel_readuint8) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint8_t value | uint8_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint8()

```C
int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)
```

**Description**

Reads a uint8_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint8_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint16()

```C
int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)
```

**Description**

Writes a uint16_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with the [OH_IPCParcel_ReadUint16()](#oh_ipcparcel_readuint16) method.
- Calling sequence: first call OH_IPCParcel_WriteUint16() to write data, and then the receiving end calls [OH_IPCParcel_ReadUint16()](#oh_ipcparcel_readuint16) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint16_t value | uint16_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint16()

```C
int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)
```

**Description**

Reads a uint16_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint16_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint32()

```C
int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)
```

**Description**

Writes a uint32_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with the [OH_IPCParcel_ReadUint32()](#oh_ipcparcel_readuint32) method.
- Calling order: first call OH_IPCParcel_WriteUint32() to write data, then the receiving end calls [OH_IPCParcel_ReadUint32()](#oh_ipcparcel_readuint32) to read data.
- Incorrect pairing: If the calls are not made in order or the read type does not match, the read fails or a data error occurs.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint32_t value | uint32_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint32()

```C
int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)
```

**Description**

Reads a uint32_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint32_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteUint64()

```C
int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)
```

**Description**

Writes a uint64_t value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total serialization size limit of IPC (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with the [OH_IPCParcel_ReadUint64()](#oh_ipcparcel_readuint64) method.
- Call sequence: first call OH_IPCParcel_WriteUint64() to write data, and then the receiving end calls [OH_IPCParcel_ReadUint64()](#oh_ipcparcel_readuint64) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint64_t value | uint64_t data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadUint64()

```C
int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)
```

**Description**

Reads a uint64_t value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | uint64_t *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteFloat()

```C
int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)
```

**Description**

Writes a float value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the IPC total serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with [OH_IPCParcel_ReadFloat()](#oh_ipcparcel_readfloat).
- Calling sequence: call OH_IPCParcel_WriteFloat() first to write data, and then the receiving end calls [OH_IPCParcel_ReadFloat()](#oh_ipcparcel_readfloat) to read data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | float value | Float data value to write, used for data serialization in IPC communication. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadFloat()

```C
int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)
```

**Description**

Reads a float value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | float *value | Pointer to the buffer for storing the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteDouble()

```C
int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)
```

**Description**

Writes a double value to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

- Must be used in pair with [OH_IPCParcel_ReadDouble()](#oh_ipcparcel_readdouble).
- Call order: call OH_IPCParcel_WriteDouble() first to write the data, and then the receiving end calls [OH_IPCParcel_ReadDouble()](#oh_ipcparcel_readdouble) to read the data.
- Incorrect pairing: If the functions are not called in order or the read type does not match, the read fails or the data is incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | double value | Double data value to write, used for IPC communication data serialization. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadDouble()

```C
int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)
```

**Description**

Reads a double value from the [OHIPCParcel](capi-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | double *value | Pointer to the storage for the read data, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_WriteString()

```C
int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)
```

**Description**

Writes a string, including the string terminator, to the [OHIPCParcel](capi-ohipcparcel.md) object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes the string content (including the terminator '\0')) to the current write position of the [OHIPCParcel](capi-ohipcparcel.md) object.
- The write position automatically moves forward by (string length + 1) bytes.
- The string data is serialized and stored in the Parcel object, and the caller does not need to manage it.
- The length of the written string is subject to the IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create), with a maximum of 204800 bytes).
- The str parameter cannot be null; otherwise, a parameter error is returned.
- Encoding note: the string must be valid UTF-8 or ASCII encoding.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const char *str | String to write, used for string data transfer in IPC communication, which cannot be null. The length ranges from 0 to 204800, in bytes (including the terminator; the actual length is dynamically affected by the data already written to the parcel and the terminator overhead). The length of the string to write is subject to the IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)). If the limit is exceeded, the OH_IPC_PARCEL_WRITE_ERROR error code is returned. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadString()

```C
const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)
```

**Description**

Reads a string from the [OHIPCParcel](capi-ohipcparcel.md) object. The user can obtain the string length by using strlen.

Call this function:
1. The string content is read from the current read position.
2. The memory address pointer to the string is returned.
3. The read position is automatically advanced to the position after the string terminator.
4. The memory of the returned string is managed by the Parcel object and does not need to be released by the caller.
5. The validity of the string is bound to the Parcel object. The string becomes invalid after the Parcel is destroyed.
6. NULL is returned when the parameter is invalid or the read fails. Check the return value.
7. The length can be obtained by using strlen, and the returned pointer can be used directly to access the string content.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| const char* | Returns the address of the string read if the operation is successful; returns NULL if the operation fails or invalid parameters are found.|

### OH_IPCParcel_WriteBuffer()

```C
int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)
```

**Description**

Writes memory information of a specified length to the [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for writing binary data, image data, custom structures, shared memory content, and other scenarios. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes the memory data pointed to by buffer to the current write position of the [OHIPCParcel](capi-ohipcparcel.md) object.
- The write position automatically moves backward by len bytes.
- The memory data is serialized and stored in the Parcel object.
- The buffer must be allocated with sufficient memory space in advance, and the memory must be valid.
- The value of len ranges from [0, the number of writable bytes in the parcel]. If it is out of range, an error is returned.
- The buffer cannot be null; otherwise, a parameter error is returned.
- The data to be written must remain valid during the call. There is no restriction after the write is complete.
- After the write is complete, the buffer memory is managed by the caller, and the Parcel stores a copy internally.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const uint8_t *buffer  | Starting address of the memory to write, that is, the starting address of the data buffer to write, which points to the binary data to be transferred over IPC and cannot be null. The buffer must be pre-allocated with sufficient memory space. |
  | int32_t len | Length of the information to write, in bytes. Value range: [0, the number of writable bytes in the parcel]. The size of the written data is subject to the IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)). Returns OH_IPC_CHECK_PARAM_ERROR if a negative number is passed in; returns OH_IPC_PARCEL_WRITE_ERROR if the number of writable bytes is exceeded. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadBuffer()

```C
const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)
```

**Description**

Reads memory information of the specified length from the [OHIPCParcel](capi-ohipcparcel.md) object. This is often used to read binary data, image data, custom structs, and shared memory contents.

Call this function:
- Reads len bytes of memory data from the current read position. The value of len ranges from [0, the number of readable bytes in the parcel]. If the value is out of range, NULL is returned.
- Returns a pointer to the data stored inside the Parcel object.
- The read position automatically moves forward by len bytes.
- The returned memory is managed by the Parcel object and does not need to be released by the caller.
- Lifecycle: The validity of the data is bound to the Parcel object; the data becomes invalid after the Parcel is destroyed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int32_t len | Length of the memory to read, in bytes. The value ranges from 0 to the number of bytes currently remaining readable in the parcel. NULL is returned if the length exceeds the number of readable bytes. |

**Returns**

| Type| Description|
| ---- | ---- |
| const uint8_t* | Returns the memory address read if the operation is successful; returns NULL if invalid parameters are found or **len** exceeds the readable length of **parcel**.|

### OH_IPCParcel_WriteRemoteStub()

```C
int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)
```

**Description**

Writes the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object to the [OHIPCParcel](capi-ohipcparcel.md) object. This function is commonly used for cross-process transfer of service objects, remote calls on the IPC server side, service object sharing, and other scenarios. The written data is subject to the total serialization size limit of IPC (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes the reference information of the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object into the [OHIPCParcel](capi-ohipcparcel.md) object, and the write position automatically advances.
- The reference information of the **Stub** object is serialized and stored.
- Call sequence: first call OH_IPCParcel_WriteRemoteStub() to write the **Stub** object, and then the receiving side calls [OH_IPCParcel_ReadRemoteStub()](#oh_ipcparcel_readremotestub) to read it.
- Incorrect pairing: If the functions are not called in the correct sequence or the calls are not properly paired, the receiving side will be unable to correctly obtain the reference to the **Stub** object, which will affect the establishment of IPC communication.
- Object validity: **stub** cannot be null and must be a valid [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object pointer; otherwise, a parameter error is returned.
- Reference management: after writing, the reference count of the **Stub** object increases, so ensure that the lifecycle of the **Stub** object is sufficient.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | Pointer to the OHIPCRemoteStub object to be written, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadRemoteStub()

```C
OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)
```

**Description**

Reads an [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object from an [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for cross-process receiving of service objects, implementing server-side remote calls in IPC, and sharing service objects.

Call this function:
- Reads the reference information of the Stub object from the current read position.
- Returns the pointer to the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object.
- The read position moves backward automatically.
- Must be used in pair with [OH_IPCParcel_WriteRemoteStub()](#oh_ipcparcel_writeremotestub).
- The returned Stub object pointer is managed by the system and must be used in accordance with IPC specifications.
- Returns NULL if reading fails; check the return value.
- Typically used to receive the Stub object passed by the server to establish IPC communication.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md)* | Return on success: pointer to the OHIPCRemoteStub object; return on failure: NULL. |

### OH_IPCParcel_WriteRemoteProxy()

```C
int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)
```

**Description**

Writes an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object to an [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for cross-process transfer of proxy objects, implementing client-side remote calls in IPC, and sharing proxy objects. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes the reference information of the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object into the [OHIPCParcel](capi-ohipcparcel.md) object.
- The write position moves backward automatically.
- The reference information of the Proxy object is serialized and stored.
- Call sequence: first call OH_IPCParcel_WriteRemoteProxy() to write the Proxy object, and then the receiving side calls [OH_IPCParcel_ReadRemoteProxy()](#oh_ipcparcel_readremoteproxy) to read it.
- Incorrect pairing: If the functions are not called in the correct sequence or the calls are not properly paired, the receiving side will be unable to correctly obtain the reference to the **OHIPCRemoteProxy** object, which will affect the establishment of IPC communication.
- Object validity: proxy cannot be null and must be a valid pointer to an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object; otherwise, a parameter error is returned.
- Reference management: after writing, the reference count of the Proxy object increases, so ensure that the lifecycle of the Proxy object is sufficient.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name | Description |
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the OHIPCRemoteProxy object to be written, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadRemoteProxy()

```C
OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)
```

**Description**

Reads an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object from an [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for receiving proxy objects across processes, implementing remote calls of IPC clients, sharing proxy objects, and other scenarios.

Call this function:
- Reads the reference information of the Proxy object from the current read position.
- Returns the pointer to the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object.
- The read position moves backward automatically.
- This function must be used in pair with [OH_IPCParcel_WriteRemoteProxy()](#oh_ipcparcel_writeremoteproxy).
- The returned Proxy object pointer is managed by the system and must be used in accordance with the IPC specifications.
- NULL is returned when the read fails. Check the return value.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md)* | Return on success: pointer to the OHIPCRemoteProxy object; return on failure: NULL. |

### OH_IPCParcel_WriteFileDescriptor()

```C
int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)
```

**Description**

Writes a file descriptor to the [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for cross-process transfer of file handles, shared memory file descriptors, pipe file descriptors, and other scenarios. The written data is subject to the total serialization size limit of IPC (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes a copy of the file descriptor to the [OHIPCParcel](capi-ohipcparcel.md) object.
- The write position moves backward automatically.
- The file descriptor information is serialized and stored, and can be transferred during IPC communication.
- Call sequence: First call OH_IPCParcel_WriteFileDescriptor() to write the file descriptor, and then the receiving side calls [OH_IPCParcel_ReadFileDescriptor()](#oh_ipcparcel_readfiledescriptor) to read it.
- Incorrect pairing: If the functions are not called in sequence or the calls are not properly paired, the receiving side cannot obtain the correct file descriptor, affecting cross-process file sharing and access.
- File descriptor validity: fd must be a valid non-negative integer file descriptor.
- Resource management: After writing, the original file descriptor is still managed by the caller and must be closed by the caller.
- Permission transfer: The file descriptor obtained by the receiving side has the same access permissions.
- System limitation: File descriptor transfer is subject to system limitations, and some special file descriptors may not be transferable.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int32_t fd | File descriptor to write. It must be a valid non-negative integer. If a negative number or an invalid file descriptor is passed in, OH_IPC_CHECK_PARAM_ERROR is returned. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadFileDescriptor()

```C
int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)
```

**Description**

Reads a file descriptor from an [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for cross-process receiving of file handles, shared memory file descriptors, pipe file descriptors, and other scenarios. Does not support multiple threads concurrently accessing the same object.

Call this function:
- Reads the file descriptor information from the current read position.
- Returns a new valid file descriptor.
- The read position automatically moves backward.
- The new file descriptor points to the same resource as the original file and inherits the access permissions of the original file descriptor.
- It must be used in pair with [OH_IPCParcel_WriteFileDescriptor()](#oh_ipcparcel_writefiledescriptor).
- The file descriptor read must be managed by the receiver and should be closed after use.
- The returned file descriptor should be checked for validity (a non-negative value).
- The lifecycle of the file descriptor is independent of the Parcel object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | int32_t *fd | Pointer to the storage for the read file descriptor, which cannot be null. Before reading, ensure that valid file descriptor data has been written to the parcel. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|

### OH_IPCParcel_Append()

```C
int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)
```

**Description**

Appends the data of an [OHIPCParcel](capi-ohipcparcel.md) object. Commonly used for merging data from multiple Parcel objects, assembling data packets, and merging segmented written data. The appended data is subject to the total serialization size limit of IPC (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Copies the data in the source [OHIPCParcel](capi-ohipcparcel.md) object (data) and appends it to the current write position of the target [OHIPCParcel](capi-ohipcparcel.md) object (parcel).
- The write position automatically moves forward by the number of bytes of the appended data.
- The read position and content of the source [OHIPCParcel](capi-ohipcparcel.md) object remain unchanged.
- The append operation copies the source data to the target [OHIPCParcel](capi-ohipcparcel.md), and the memory is managed by the target [OHIPCParcel](capi-ohipcparcel.md).
- The total size of the concatenated data must not exceed the IPC serialization limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).
- Neither the parcel nor the data parameter can be null; otherwise, a parameter error is returned.
- Both parameters must be valid objects created by [OH_IPCParcel_Create()](#oh_ipcparcel_create).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const [OHIPCParcel](capi-ohipcparcel.md) *data | Pointer to the source OHIPCParcel object, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the concatenation fails.|

### OH_IPCParcel_WriteInterfaceToken()

```C
int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)
```

**Description**

Writes the interface descriptor to the [OHIPCParcel](capi-ohipcparcel.md) object for interface identity verification. It is commonly used in security verification scenarios in IPC communication, for example, preventing malicious processes from sending forged requests, ensuring that messages are sent to the correct service interface, and distinguishing different interface calls in a multi-interface service. It does not support multiple threads concurrently accessing the same object. The written data is subject to the total IPC serialization size limit (see [OH_IPCParcel_Create()](#oh_ipcparcel_create)).

Call this function:
- Writes the interface descriptor string to the current write position of the [OHIPCParcel](capi-ohipcparcel.md) object.
- The write position automatically advances by the corresponding number of bytes.
- The interface descriptor data is serialized and stored in the Parcel object.
- The length of the interface descriptor string cannot exceed the remaining writable space of the Parcel.
- Calling sequence: first call OH_IPCParcel_WriteInterfaceToken() to write the interface descriptor, and then the receiving end calls [OH_IPCParcel_ReadInterfaceToken()](#oh_ipcparcel_readinterfacetoken) to read and verify it.
- If the functions are not called in sequence or not used in pairs, interface identity verification fails, and the request may be rejected or sent to the wrong interface, causing interface confusion.
- The token parameter cannot be null; otherwise, a parameter error is returned.
- It is recommended to write the interface descriptor before writing other request data.
- The interface descriptor should be the fully qualified name or a unique identifier string of the interface.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | const char *token | Interface descriptor information to be written, which cannot be null. The interface descriptor is usually the fully qualified name or a unique identifier string of the interface, used for interface identity verification. The string length ranges from (0, remaining writable space of the parcel], in bytes. If the limit is exceeded, OH_IPC_PARCEL_WRITE_ERROR is returned. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found.<br> Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails.|

### OH_IPCParcel_ReadInterfaceToken()

```C
int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Reads the interface descriptor information from the [OHIPCParcel](capi-ohipcparcel.md) object, which is used for interface identity verification.

Call this function:
- It must be used in pairs with [OH_IPCParcel_WriteInterfaceToken()](#oh_ipcparcel_writeinterfacetoken).
- It reads the interface descriptor string from the current read position.
- It allocates memory through the allocator provided by the user to store the descriptor.
- Returns the descriptor address and length.
- The read position moves forward automatically.
- The token memory is allocated by the user-provided allocator and must be released after use.
- Even if the function fails, check whether the token is empty and release it.
- Failure to release the token properly causes a memory leak.
- It is recommended to verify the interface descriptor before processing the request.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**

  | Name| Description|
  | ------ | ---- |
  | const [OHIPCParcel](capi-ohipcparcel.md) *parcel | Pointer to the OHIPCParcel object, which cannot be null. |
  | char **token | Memory address used to store the interface descriptor information. The memory is allocated by the user-provided allocator and must be released by the user after use. It cannot be null. If the interface returns a failure, the user must still check whether the memory is null and release it proactively; otherwise, a memory leak will occur. |
  | int32_t *len | Length of the read interface descriptor (including the terminator), in bytes. It cannot be null. |
  | [OH_IPC_MemAllocator()](#oh_ipc_memallocator) allocator | User-specified memory allocator used to allocate the token, which cannot be null. |

**Returns**

| Type| Description|
| ---- | ---- |
| int | Returns [OH_IPC_ErrorCode#OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful.<br> Returns [OH_IPC_ErrorCode#OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. Returns [OH_IPC_ErrorCode#OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails.|
