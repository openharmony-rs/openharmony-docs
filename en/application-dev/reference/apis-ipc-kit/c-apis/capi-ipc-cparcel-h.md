# ipc_cparcel.h

## Overview

This file provides C APIs for IPC serialization and deserialization, which are used to serialize and deserialize data during IPC communication.

**File to Include**: <IPCKit/ipc_cparcel.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Related module**: [OHIPCParcel](capi-ipc-kit-ohipcparcel.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) | - | IPC serialization object, used for serializing and deserializing data in cross-process communication. This object must be created and destroyed through related functions. You must follow the lifecycle management specifications of the object and properly manage memory resources. |
| [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) | - | IPC remote proxy object, which is used on the client side to proxy the capabilities of a remote service to implement cross-process communication. This object encapsulates a reference to the remote service and supports sending requests to and receiving responses from the remote service. It is applicable to scenarios that require cross-process service capability invocation, such as cross-process service calls, system service access, and cross-application data sharing. Using this object simplifies the implementation of cross-process communication and improves development efficiency. |
| [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) | - | Defines an IPC remote service object. This struct is used to represent a remote service on the server. As the service agent of the server in IPC, it processes requests from the client and implements cross-process communication. **OHIPCRemoteStub** is a core struct provided by IPC Kit. It simplifies the IPC service development process and provides a unified request processing mechanism, helping you quickly implement cross-process communication capabilities. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void* (\*OH_IPC_MemAllocator)(int32_t len)](#oh_ipc_memallocator) | OH_IPC_MemAllocator | Defines the memory allocation function type, which is used to customize the memory allocation policy for IPC communication. This function is commonly used in scenarios that require special memory management, such as shared memory transmission, memory pool management, and limiting memory usage. |
| [OHIPCParcel* OH_IPCParcel_Create(void)](#oh_ipcparcel_create) | - | Creates an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for data serialization in IPC communication. When this function is called: - An [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object is allocated and initialized in memory. - The object is initially empty, and its serializable size must not exceed 204800 bytes. - The returned object pointer can be used for subsequent data read and write operations. - Concurrent access to the same object from multiple threads is not supported. - Typical usage flow: [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) ? Data read/write operations ? [OH_IPCParcel_Destroy()](capi-ipc-cparcel-h.md#oh_ipcparcel_destroy()) |
| [void OH_IPCParcel_Destroy(OHIPCParcel *parcel)](#oh_ipcparcel_destroy) | - | Destroys an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. When this function is called: - The memory buffer occupied by the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object is released. - All data in the object is released. The memory occupied by the object itself is released. - The input pointer becomes invalid and should not be used any more. - Before calling this function, ensure that no other thread is using the object. - It is advised to set the pointer to NULL to avoid dangling pointers. - This function and [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) must be used in pairs. - Ensure that all required data has been read before destroying the object. - Do not call the destruction function multiple times for the same object. - Only objects created by [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) can be destroyed. - The object cannot be accessed after destruction. |
| [int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)](#oh_ipcparcel_getdatasize) | - | Obtains the size of the data contained in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as monitoring data transmission progress, checking whether the IPC serialization size limit has been exceeded, and debugging data read/write processes. When this function is called: - The total number of bytes of data that has been written to the **Parcel** object is calculated. - The total size of the written data is returned. - The read/write position and the data content remain unchanged. |
| [int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getwritablebytes) | - | Obtains the number of bytes that can be written to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as checking whether there is enough space to write more data, preventing write overflow, and performing pre-checks before batch writes. When this function is called: - The size of the remaining writable space in the **Parcel** object is calculated. - The number of writable bytes is returned. - Neither the read/write position nor the data content of the **Parcel** object is changed. |
| [int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadablebytes) | - | Obtains the number of bytes that can be read from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as checking how much data is available to read, reading data cyclically, and debugging the data reading process. When this function is called: - The number of bytes of unread data in the **Parcel** object is calculated. - The number of readable bytes is returned. - Neither the read/write position nor the data content of the **Parcel** object is changed. |
| [int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getreadposition) | - | Obtains the position where data is read in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as recording the read position for later restoration, working with [OH_IPCParcel_RewindReadPosition()](capi-ipc-cparcel-h.md#oh_ipcparcel_rewindreadposition()) to enable repeated reads, and debugging the data reading progress. When this function is called: - The current read position of the **Parcel** object is returned. - The read position and data content remain unchanged. |
| [int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)](#oh_ipcparcel_getwriteposition) | - | Obtains the position where data is written in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as recording the write position, working with [OH_IPCParcel_RewindWritePosition()](capi-ipc-cparcel-h.md#oh_ipcparcel_rewindwriteposition()) to correct write errors, and debugging the data write progress. When this function is called: - The current write position of the **Parcel** object is returned. - The write position and data content remain unchanged. |
| [int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)](#oh_ipcparcel_rewindreadposition) | - | Resets the read position of the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object to the specified position. This function is commonly used in scenarios where data needs to be parsed repeatedly. When this function is called: - The read position pointer is moved to the position specified by **newReadPos**, which must be within the range of [0, current data size]. - The data already written remains unchanged. - Subsequent read operations start from the new position. |
| [int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)](#oh_ipcparcel_rewindwriteposition) | - | Resets the write position of the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object to the specified position. This function is usually used in scenarios where data errors need to be corrected after data is written, data needs to be rewritten by segment, or some write operations need to be canceled. When this function is called: - The write position pointer is moved to the position specified by **newWritePos**, which must be within the range of [0, current data size]. - Resetting the position may cause some data to be overwritten or invalidated. Use this function with caution. - Subsequent write operations start from the new position. - Resetting the write position does not affect the read position. |
| [int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)](#oh_ipcparcel_writeint8) | - | Writes an int8_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. Concurrent access to the same object from multiple threads is not supported. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). - This function and [OH_IPCParcel_ReadInt8()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint8()) must be used in pairs. - Calling sequence: First you call **OH_IPCParcel_WriteInt8()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt8()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint8()) to read the data. - Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect. |
| [int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)](#oh_ipcparcel_readint8) | - | Reads an int8_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. Concurrent access to the same object from multiple threads is not supported. |
| [int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)](#oh_ipcparcel_writeint16) | - | Writes an int16_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). - This function and [OH_IPCParcel_ReadInt16()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint16()) must be used in pairs. - Calling sequence: First you call **OH_IPCParcel_WriteInt16()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt16()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint16()) to read the data. - Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect. |
| [int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)](#oh_ipcparcel_readint16) | - | Reads an int16_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)](#oh_ipcparcel_writeint32) | - | Writes an int32_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). - This function and [OH_IPCParcel_ReadInt32()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint32()) must be used in pairs. - Calling sequence: First you call **OH_IPCParcel_WriteInt32()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt32()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint32()) to read the data. - Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect. |
| [int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)](#oh_ipcparcel_readint32) | - | Reads an int32_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)](#oh_ipcparcel_writeint64) | - | Writes an int64_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)](#oh_ipcparcel_readint64) | - | Reads an int64_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)](#oh_ipcparcel_writeuint8) | - | Writes a uint8_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)](#oh_ipcparcel_readuint8) | - | Reads a uint8_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)](#oh_ipcparcel_writeuint16) | - | Writes a uint16_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)](#oh_ipcparcel_readuint16) | - | Reads a uint16_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)](#oh_ipcparcel_writeuint32) | - | Writes a uint32_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)](#oh_ipcparcel_readuint32) | - | Reads a uint32_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)](#oh_ipcparcel_writeuint64) | - | Writes a uint64_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)](#oh_ipcparcel_readuint64) | - | Reads a uint64_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)](#oh_ipcparcel_writefloat) | - | Writes a float value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)](#oh_ipcparcel_readfloat) | - | Reads a float value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)](#oh_ipcparcel_writedouble) | - | Writes a double value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). |
| [int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)](#oh_ipcparcel_readdouble) | - | Reads a double value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. |
| [int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)](#oh_ipcparcel_writestring) | - | Writes a string including a string terminator to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)](#oh_ipcparcel_readstring) | - | Reads a string from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. You can obtain the length of the string from **strlen**. <br>When this function is called: |
| [int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)](#oh_ipcparcel_writebuffer) | - | Writes data of the specified length from the memory to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as writing binary data, image data, custom structures, and shared memory content. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)](#oh_ipcparcel_readbuffer) | - | Reads memory information of the specified length from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as reading binary data, image data, custom structures, and shared memory content. <br>When this function is called: |
| [int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)](#oh_ipcparcel_writeremotestub) | - | Writes an [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing service objects across processes, implementing remote calls in an IPC server, and sharing service objects. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)](#oh_ipcparcel_readremotestub) | - | Reads the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving service objects across processes, implementing remote calls in an IPC server, and sharing service objects. <br>When this function is called: |
| [int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)](#oh_ipcparcel_writeremoteproxy) | - | Writes an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)](#oh_ipcparcel_readremoteproxy) | - | Reads the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects. <br>When this function is called: |
| [int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)](#oh_ipcparcel_writefiledescriptor) | - | Writes a file descriptor to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing file handles across processes, shared memory file descriptors, and pipe file descriptors. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)](#oh_ipcparcel_readfiledescriptor) | - | Reads a file descriptor from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving file handles across processes, shared memory file descriptors, and pipe file descriptors. Concurrent access to the same object from multiple threads is not supported. <br>When this function is called: |
| [int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)](#oh_ipcparcel_append) | - | Appends data to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as merging data from multiple parcels, packet assembly, and merging data written in segments. The size of appended data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)](#oh_ipcparcel_writeinterfacetoken) | - | Writes an interface token to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for interface identity verification. This function is commonly used in security verification scenarios in IPC communication, such as preventing malicious processes from sending forged requests, ensuring that messages are sent to the correct service API, and distinguishing different API calls in multi-API services. Concurrent access to the same object from multiple threads is not supported. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called: |
| [int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)](#oh_ipcparcel_readinterfacetoken) | - | Reads an interface token from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for interface identity verification. <br>When this function is called: |

## Function description

### OH_IPC_MemAllocator()

```c
typedef void* (*OH_IPC_MemAllocator)(int32_t len)
```

**Description**

Defines the memory allocation function type, which is used to customize the memory allocation policy for IPC communication. This function is commonly used in scenarios that require special memory management, such as shared memory transmission, memory pool management, and limiting memory usage.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t len | Length of the memory to be allocated, in bytes. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the address of the memory allocated if the operation is successful; returns NULL otherwise. |

### OH_IPCParcel_Create()

```c
OHIPCParcel* OH_IPCParcel_Create(void)
```

**Description**

Creates an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for data serialization in IPC communication. When this function is called:
- An [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object is allocated and initialized in memory.
- The object is initially empty, and its serializable size must not exceed 204800 bytes.
- The returned object pointer can be used for subsequent data read and write operations.
- Concurrent access to the same object from multiple threads is not supported.
- Typical usage flow: [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) ? Data read/write operations ? [OH_IPCParcel_Destroy()](capi-ipc-cparcel-h.md#oh_ipcparcel_destroy())

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OHIPCParcel*](capi-ohipcparcel-ohipcparcel.md) | Returns the pointer to the **OHIPCParcel** object created if the operation is successful; returns NULL otherwise. |

### OH_IPCParcel_Destroy()

```c
void OH_IPCParcel_Destroy(OHIPCParcel *parcel)
```

**Description**

Destroys an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. When this function is called:
- The memory buffer occupied by the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object is released.
- All data in the object is released. The memory occupied by the object itself is released.
- The input pointer becomes invalid and should not be used any more.
- Before calling this function, ensure that no other thread is using the object.
- It is advised to set the pointer to NULL to avoid dangling pointers.
- This function and [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) must be used in pairs.
- Ensure that all required data has been read before destroying the object.
- Do not call the destruction function multiple times for the same object.
- Only objects created by [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create()) can be destroyed.
- The object cannot be accessed after destruction.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object to be destroyed. It cannot be NULL. |

### OH_IPCParcel_GetDataSize()

```c
int OH_IPCParcel_GetDataSize(const OHIPCParcel *parcel)
```

**Description**

Obtains the size of the data contained in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as monitoring data transmission progress, checking whether the IPC serialization size limit has been exceeded, and debugging data read/write processes. When this function is called:
- The total number of bytes of data that has been written to the **Parcel** object is calculated.
- The total size of the written data is returned.
- The read/write position and the data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Total size of data that has been written to the **Parcel** object, in bytes. If the parameter is invalid, **- 1** is returned. |

### OH_IPCParcel_GetWritableBytes()

```c
int OH_IPCParcel_GetWritableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can be written to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as checking whether there is enough space to write more data, preventing write overflow, and performing pre-checks before batch writes. When this function is called:
- The size of the remaining writable space in the **Parcel** object is calculated.
- The number of writable bytes is returned.
- Neither the read/write position nor the data content of the **Parcel** object is changed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Size of the writable bytes, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetReadableBytes()

```c
int OH_IPCParcel_GetReadableBytes(const OHIPCParcel *parcel)
```

**Description**

Obtains the number of bytes that can be read from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as checking how much data is available to read, reading data cyclically, and debugging the data reading process. When this function is called:
- The number of bytes of unread data in the **Parcel** object is calculated.
- The number of readable bytes is returned.
- Neither the read/write position nor the data content of the **Parcel** object is changed.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Size of the readable bytes, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetReadPosition()

```c
int OH_IPCParcel_GetReadPosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the position where data is read in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as recording the read position for later restoration, working with [OH_IPCParcel_RewindReadPosition()](capi-ipc-cparcel-h.md#oh_ipcparcel_rewindreadposition()) to enable repeated reads, and debugging the data reading progress. When this function is called:
- The current read position of the **Parcel** object is returned.
- The read position and data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Current read position, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_GetWritePosition()

```c
int OH_IPCParcel_GetWritePosition(const OHIPCParcel *parcel)
```

**Description**

Obtains the position where data is written in an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as recording the write position, working with [OH_IPCParcel_RewindWritePosition()](capi-ipc-cparcel-h.md#oh_ipcparcel_rewindwriteposition()) to correct write errors, and debugging the data write progress. When this function is called:
- The current write position of the **Parcel** object is returned.
- The write position and data content remain unchanged.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Current write position, in bytes. If the parameter is invalid, **-1** is returned. |

### OH_IPCParcel_RewindReadPosition()

```c
int OH_IPCParcel_RewindReadPosition(OHIPCParcel *parcel, uint32_t newReadPos)
```

**Description**

Resets the read position of the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object to the specified position. This function is commonly used in scenarios where data needs to be parsed repeatedly. When this function is called:
- The read position pointer is moved to the position specified by **newReadPos**, which must be within the range of [0, current data size].
- The data already written remains unchanged.
- Subsequent read operations start from the new position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint32_t newReadPos | New position to read data, in bytes. The value ranges from 0 to the current data size. If the value is out of range, the **OH_IPC_CHECK_PARAM_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. |

### OH_IPCParcel_RewindWritePosition()

```c
int OH_IPCParcel_RewindWritePosition(OHIPCParcel *parcel, uint32_t newWritePos)
```

**Description**

Resets the write position of the [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object to the specified position. This function is usually used in scenarios where data errors need to be corrected after data is written, data needs to be rewritten by segment, or some write operations need to be canceled. When this function is called:
- The write position pointer is moved to the position specified by **newWritePos**, which must be within the range of [0, current data size].
- Resetting the position may cause some data to be overwritten or invalidated. Use this function with caution.
- Subsequent write operations start from the new position.
- Resetting the write position does not affect the read position.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint32_t newWritePos | New position to write data, in bytes. The value ranges from 0 to the current data size. If the value is out of range, the **OH_IPC_CHECK_PARAM_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. |

### OH_IPCParcel_WriteInt8()

```c
int OH_IPCParcel_WriteInt8(OHIPCParcel *parcel, int8_t value)
```

**Description**

Writes an int8_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. Concurrent access to the same object from multiple threads is not supported. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).
- This function and [OH_IPCParcel_ReadInt8()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint8()) must be used in pairs.
- Calling sequence: First you call **OH_IPCParcel_WriteInt8()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt8()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint8()) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int8_t value | int8_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInt8()

```c
int OH_IPCParcel_ReadInt8(const OHIPCParcel *parcel, int8_t *value)
```

**Description**

Reads an int8_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. Concurrent access to the same object from multiple threads is not supported.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int8_t *value | Pointer to store the read int8_t data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteInt16()

```c
int OH_IPCParcel_WriteInt16(OHIPCParcel *parcel, int16_t value)
```

**Description**

Writes an int16_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).
- This function and [OH_IPCParcel_ReadInt16()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint16()) must be used in pairs.
- Calling sequence: First you call **OH_IPCParcel_WriteInt16()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt16()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint16()) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int16_t value | int16_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInt16()

```c
int OH_IPCParcel_ReadInt16(const OHIPCParcel *parcel, int16_t *value)
```

**Description**

Reads an int16_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int16_t *value | Pointer to store the read int16_t data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteInt32()

```c
int OH_IPCParcel_WriteInt32(OHIPCParcel *parcel, int32_t value)
```

**Description**

Writes an int32_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).
- This function and [OH_IPCParcel_ReadInt32()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint32()) must be used in pairs.
- Calling sequence: First you call **OH_IPCParcel_WriteInt32()** to write the data, and then the receiving side calls [OH_IPCParcel_ReadInt32()](capi-ipc-cparcel-h.md#oh_ipcparcel_readint32()) to read the data.
- Incorrect pairing: If the functions are not called in the correct sequence or the read type does not match, the read operation will fail or the data will be incorrect.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int32_t value | int32_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInt32()

```c
int OH_IPCParcel_ReadInt32(const OHIPCParcel *parcel, int32_t *value)
```

**Description**

Reads an int32_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int32_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteInt64()

```c
int OH_IPCParcel_WriteInt64(OHIPCParcel *parcel, int64_t value)
```

**Description**

Writes an int64_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int64_t value | int64_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInt64()

```c
int OH_IPCParcel_ReadInt64(const OHIPCParcel *parcel, int64_t *value)
```

**Description**

Reads an int64_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int64_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteUint8()

```c
int OH_IPCParcel_WriteUint8(OHIPCParcel *parcel, uint8_t value)
```

**Description**

Writes a uint8_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint8_t value | uint8_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadUint8()

```c
int OH_IPCParcel_ReadUint8(const OHIPCParcel *parcel, uint8_t *value)
```

**Description**

Reads a uint8_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint8_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteUint16()

```c
int OH_IPCParcel_WriteUint16(OHIPCParcel *parcel, uint16_t value)
```

**Description**

Writes a uint16_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint16_t value | uint16_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadUint16()

```c
int OH_IPCParcel_ReadUint16(const OHIPCParcel *parcel, uint16_t *value)
```

**Description**

Reads a uint16_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint16_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteUint32()

```c
int OH_IPCParcel_WriteUint32(OHIPCParcel *parcel, uint32_t value)
```

**Description**

Writes a uint32_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint32_t value | uint32_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadUint32()

```c
int OH_IPCParcel_ReadUint32(const OHIPCParcel *parcel, uint32_t *value)
```

**Description**

Reads a uint32_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint32_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteUint64()

```c
int OH_IPCParcel_WriteUint64(OHIPCParcel *parcel, uint64_t value)
```

**Description**

Writes a uint64_t value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint64_t value | uint64_t data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadUint64()

```c
int OH_IPCParcel_ReadUint64(const OHIPCParcel *parcel, uint64_t *value)
```

**Description**

Reads a uint64_t value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| uint64_t *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteFloat()

```c
int OH_IPCParcel_WriteFloat(OHIPCParcel *parcel, float value)
```

**Description**

Writes a float value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| float value | float data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadFloat()

```c
int OH_IPCParcel_ReadFloat(const OHIPCParcel *parcel, float *value)
```

**Description**

Reads a float value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| float *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteDouble()

```c
int OH_IPCParcel_WriteDouble(OHIPCParcel *parcel, double value)
```

**Description**

Writes a double value to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())).

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| double value | Double data value to be written, which is used for IPC data serialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadDouble()

```c
int OH_IPCParcel_ReadDouble(const OHIPCParcel *parcel, double *value)
```

**Description**

Reads a double value from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object.

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| double *value | Pointer to store the read data. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_WriteString()

```c
int OH_IPCParcel_WriteString(OHIPCParcel *parcel, const char *str)
```

**Description**

Writes a string including a string terminator to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| const char *str | Pointer to the string to write, which is used for string data transmission in IPC communication. It cannot be NULL. The length range is [0, 204800], in bytes (including the null terminator. The actual length is dynamically affected by the data already written to the parcel and the overhead of the terminator). The length of the written string is subject to the IPC serialization size limit (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). If the limit is exceeded, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadString()

```c
const char* OH_IPCParcel_ReadString(const OHIPCParcel *parcel)
```

**Description**

Reads a string from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. You can obtain the length of the string from **strlen**. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns the address of the string read if the operation is successful; returns NULL if the operation fails or invalid parameters are found. |

### OH_IPCParcel_WriteBuffer()

```c
int OH_IPCParcel_WriteBuffer(OHIPCParcel *parcel, const uint8_t *buffer, int32_t len)
```

**Description**

Writes data of the specified length from the memory to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as writing binary data, image data, custom structures, and shared memory content. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| const uint8_t *buffer | Starting address of the memory to be written. This is the starting address of the data buffer to be written, pointing to the binary data to be transmitted via IPC. It cannot be NULL. The buffer must have sufficient memory space allocated in advance. |
| int32_t len | Length of the data to be written, in bytes. The value range is [0, available writable bytes of the parcel] . The size of the written data is subject to the IPC serialization size limit (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())) . If a negative value is passed, the **OH_IPC_CHECK_PARAM_ERROR** error is returned. If the value exceeds the available writable bytes, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadBuffer()

```c
const uint8_t* OH_IPCParcel_ReadBuffer(const OHIPCParcel *parcel, int32_t len)
```

**Description**

Reads memory information of the specified length from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as reading binary data, image data, custom structures, and shared memory content. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int32_t len | Length of memory to be read, in bytes. The value range is [0, the number of remaining readable bytes in the parcel]. If the value exceeds the readable bytes, NULL is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| const uint8_t* | Returns the memory address read if the operation is successful; returns NULL if invalid parameters are found or **len** exceeds the readable length of **parcel**. |

### OH_IPCParcel_WriteRemoteStub()

```c
int OH_IPCParcel_WriteRemoteStub(OHIPCParcel *parcel, const OHIPCRemoteStub *stub)
```

**Description**

Writes an [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing service objects across processes, implementing remote calls in an IPC server, and sharing service objects. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| [const OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) *stub | Pointer to the **OHIPCRemoteStub** object to write. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadRemoteStub()

```c
OHIPCRemoteStub* OH_IPCParcel_ReadRemoteStub(const OHIPCParcel *parcel)
```

**Description**

Reads the [OHIPCRemoteStub](capi-ohipcparcel-ohipcremotestub.md) object from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving service objects across processes, implementing remote calls in an IPC server, and sharing service objects. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHIPCRemoteStub*](capi-ohipcparcel-ohipcremotestub.md) | Returns the pointer to the **OHIPCRemoteStub** object read if the operation is successful; returns NULL otherwise. |

### OH_IPCParcel_WriteRemoteProxy()

```c
int OH_IPCParcel_WriteRemoteProxy(OHIPCParcel *parcel, const OHIPCRemoteProxy *proxy)
```

**Description**

Writes an [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| [const OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) *proxy | Pointer to the **OHIPCRemoteProxy** object to write. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadRemoteProxy()

```c
OHIPCRemoteProxy* OH_IPCParcel_ReadRemoteProxy(const OHIPCParcel *parcel)
```

**Description**

Reads the [OHIPCRemoteProxy](capi-ohipcparcel-ohipcremoteproxy.md) object from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving proxy objects across processes, implementing remote calls in an IPC client, and sharing proxy objects. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHIPCRemoteProxy*](capi-ohipcparcel-ohipcremoteproxy.md) | Returns the pointer to the **OHIPCRemoteProxy** object created if the operation is successful; returns NULL otherwise. |

### OH_IPCParcel_WriteFileDescriptor()

```c
int OH_IPCParcel_WriteFileDescriptor(OHIPCParcel *parcel, int32_t fd)
```

**Description**

Writes a file descriptor to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as passing file handles across processes, shared memory file descriptors, and pipe file descriptors. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int32_t fd | File descriptor to write. The value must be a valid file descriptor, which is a non-negative integer. If a negative value or an invalid file descriptor is passed, the **OH_IPC_CHECK_PARAM_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadFileDescriptor()

```c
int OH_IPCParcel_ReadFileDescriptor(const OHIPCParcel *parcel, int32_t *fd)
```

**Description**

Reads a file descriptor from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as receiving file handles across processes, shared memory file descriptors, and pipe file descriptors. Concurrent access to the same object from multiple threads is not supported. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| int32_t *fd | Pointer to store the read file descriptor. It cannot be NULL. Before reading, ensure that valid file descriptor data has been written to the parcel. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |

### OH_IPCParcel_Append()

```c
int OH_IPCParcel_Append(OHIPCParcel *parcel, const OHIPCParcel *data)
```

**Description**

Appends data to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object. This function is commonly used in scenarios such as merging data from multiple parcels, packet assembly, and merging data written in segments. The size of appended data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *data | Pointer to source **OHIPCParcel** object. It cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the concatenation fails. |

### OH_IPCParcel_WriteInterfaceToken()

```c
int OH_IPCParcel_WriteInterfaceToken(OHIPCParcel *parcel, const char *token)
```

**Description**

Writes an interface token to an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for interface identity verification. This function is commonly used in security verification scenarios in IPC communication, such as preventing malicious processes from sending forged requests, ensuring that messages are sent to the correct service API, and distinguishing different API calls in multi-API services. Concurrent access to the same object from multiple threads is not supported. The size of written data cannot exceed the total size of IPC serialized data (see [OH_IPCParcel_Create()](capi-ipc-cparcel-h.md#oh_ipcparcel_create())). <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| const char *token | Pointer to the interface token to write. It cannot be NULL. The interface token is usually the fully qualified name or a unique identifier string of an interface, and is used for interface identity verification. The string length range is (0, remaining writable space of the parcel]. The unit is bytes. If the limit is exceeded, the **OH_IPC_PARCEL_WRITE_ERROR** error is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. <br>Returns [OH_IPC_PARCEL_WRITE_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the write operation fails. |

### OH_IPCParcel_ReadInterfaceToken()

```c
int OH_IPCParcel_ReadInterfaceToken(const OHIPCParcel *parcel, char **token, int32_t *len, OH_IPC_MemAllocator allocator)
```

**Description**

Reads an interface token from an [OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) object for interface identity verification. <br>When this function is called:

**System capability**: SystemCapability.Communication.IPC.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OHIPCParcel](capi-ohipcparcel-ohipcparcel.md) *parcel | Pointer to the **OHIPCParcel** object. It cannot be NULL. |
| char **token | Memory address for storing the interface token information. The memory is allocated using the user- provided allocator, and must be explicitly freed by the user after use. It must not be NULL. If an error code is returned, you still need to check whether the memory is empty and release the memory. Otherwise, memory leaks may occur. |
| int32_t *len | Pointer to store the length of the read interface token (including the null terminator). The unit is bytes. It must not be NULL. |
| [OH_IPC_MemAllocator](capi-ipc-cparcel-h.md#oh_ipc_memallocator) allocator | Memory allocator specified by the user for allocating the memory for **token**. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns [OH_IPC_SUCCESS](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the operation is successful. <br>Returns [OH_IPC_CHECK_PARAM_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if invalid parameters are found. Returns [OH_IPC_PARCEL_READ_ERROR](capi-ipc-error-code-h.md#oh_ipc_errorcode) if the read operation fails. |


