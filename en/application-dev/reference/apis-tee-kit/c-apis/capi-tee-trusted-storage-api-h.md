# tee_trusted_storage_api.h

## Overview

Provides trusted storage APIs.<br> You can use these APIs to implement trusted storage features.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [\_\_TEE_ObjectEnumHandle](capi-teetrusted---tee-objectenumhandle.md) | Defines the handle for enumerating objects. |

### Enum

| Name | Description |
| -- | -- |
| [\_\_TEE_Whence](#\_\_tee_whence) | Defines the start position in the data stream associated with an object. It is used in the <b>TEE_SeekObjectData</b> function. |
| [Object_Storage_Constants](#object_storage_constants) | Defines the storage ID, which identifies the storage space of the application. |
| [Miscellaneous_Constants](#miscellaneous_constants) | Defines the system resource constraints, such as the maximum value for the data stream position indicator. |
| [TEE_DATA_Size](#tee_data_size) | Defines the maximum number of bytes that can be held in a data stream. |
| [Data_Flag_Constants](#data_flag_constants) | Defines the <b>handleFlags</b> of a <b>TEE_ObjectHandle</b>. The <b>handleFlags</b> determines the access permissions to the data stream associated with the object. |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result TEE_CreatePersistentObject(uint32_t storageID, const void *objectID, size_t objectIDLen, uint32_t flags, TEE_ObjectHandle attributes, const void *initialData, size_t initialDataLen, TEE_ObjectHandle *object)](#tee_createpersistentobject) | Creates a persistent object.<br> This function creates a persistent object with initialized <b>TEE_Attribute</b> and data stream. You can use the returned handle to access the <b>TEE_Attribute</b> and data stream of the object. |
| [TEE_Result TEE_OpenPersistentObject(uint32_t storageID, const void *objectID, size_t objectIDLen, uint32_t flags, TEE_ObjectHandle *object)](#tee_openpersistentobject) | Opens an existing persistent object.<br> The handle returned can be used to access the <b>TEE_Attribute</b> and data stream of the object. |
| [TEE_Result TEE_ReadObjectData(TEE_ObjectHandle object, void *buffer, size_t size, uint32_t *count)](#tee_readobjectdata) | Reads data from the data stream associated with an object into the buffer.<br> The <b>TEE_ObjectHandle</b> of the object must have been opened with the <b>TEE_DATA_FLAG_ACCESS_READ</b> permission. |
| [TEE_Result TEE_WriteObjectData(TEE_ObjectHandle object, const void *buffer, size_t size)](#tee_writeobjectdata) | Writes bytes from the buffer to the data stream associated with an object.<br> The <b>TEE_ObjectHandle</b> must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE</b> permission. |
| [TEE_Result TEE_TruncateObjectData(TEE_ObjectHandle object, size_t size)](#tee_truncateobjectdata) | Changes the size of a data stream.<br> If the size is less than the current size of the data stream, all bytes beyond <b>size</b> are deleted. If the size is greater than the current size of the data stream, add 0s at the end of the stream to extend the stream. The object handle must be opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE</b> permission. |
| [TEE_Result TEE_SeekObjectData(TEE_ObjectHandle object, int32_t offset, TEE_Whence whence)](#tee_seekobjectdata) | Sets the position of the data stream to which <b>TEE_ObjectHandle</b> points.<br> The data position indicator is determined by the start position and an offset together. The <b>whence</b> parameter determines the start position. Its value is set in <b>TEE_Whence</b> as follows: <b>TEE_DATA_SEEK_SET = 0</b>: The start position is the beginning of the data stream. <b>TEE_DATA_SEEK_CUR</b>: The start position is the current position of the data stream. <b>TEE_DATA_SEEK_END</b>: The start position is the end of the data stream. If the parameter <b>offset</b> is a positive number, the data position is moved forward. If <b>offset</b> is a negative number, the data position is moved backward. |
| [TEE_Result TEE_SyncPersistentObject(TEE_ObjectHandle object)](#tee_syncpersistentobject) | Synchronizes the opened <b>TEE_ObjectHandle</b> and the corresponding security attribute file to the disk. |
| [TEE_Result TEE_RenamePersistentObject(TEE_ObjectHandle object, void *newObjectID, size_t newObjectIDLen)](#tee_renamepersistentobject) | Changes the object identifier.<br> The <b>TEE_ObjectHandle</b> must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE_META</b> permission. |
| [TEE_Result TEE_CloseAndDeletePersistentObject1(TEE_ObjectHandle object)](#tee_closeanddeletepersistentobject1) | Closes a <b>TEE_ObjectHandle</b> and deletes the object.<br> The object must be a persistent object, and the object handle must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE_META</b> permission. |

### Variable

| Name | Description |
| -- | -- |
| uint32_t TEE_Whence | Defines the type for the data stream position.<br>**Since**: 20 |

## Enum type description

### __TEE_Whence

```c
enum __TEE_Whence
```

**Description**

Defines the start position in the data stream associated with an object. It is used in the <b>TEE_SeekObjectData</b> function.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DATA_SEEK_SET = 0 | Set the start position to the beginning of the data stream. |
| TEE_DATA_SEEK_CUR | Set the start position to the current data stream position. |
| TEE_DATA_SEEK_END | Set the start position to the end of the data stream. |

### Object_Storage_Constants

```c
enum Object_Storage_Constants
```

**Description**

Defines the storage ID, which identifies the storage space of the application.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_OBJECT_STORAGE_PRIVATE = 0x00000001 | Separate private storage space for each application. |
| TEE_OBJECT_STORAGE_PERSO   = 0x00000002 | Separate personal storage space for application. |
| TEE_OBJECT_SEC_FLASH       = 0x80000000 | Space for secure flash storage. |
| TEE_OBJECT_STORAGE_RPMB    = 0x80000001 | Space for RPMB storage. |
| TEE_OBJECT_STORAGE_CE      = 0x80000002 | Credential encrypted storage space. |
| TEE_OBJECT_STORAGE_ANTIROLLBACK = 0x80000003 | Anti-rollback storage space. |

### Miscellaneous_Constants

```c
enum Miscellaneous_Constants
```

**Description**

Defines the system resource constraints, such as the maximum value for the data stream position indicator.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DATA_MAX_POSITION = 0xFFFFFFFF | Maximum length that the position indicator of the data stream can take. |
| TEE_OBJECT_ID_MAX_LEN = 64 | Maximum length of the object ID, which can extend to 128 bytes. |

### TEE_DATA_Size

```c
enum TEE_DATA_Size
```

**Description**

Defines the maximum number of bytes that can be held in a data stream.

**Since**: 20

| Enum item | Description |
| -- | -- |

### Data_Flag_Constants

```c
enum Data_Flag_Constants
```

**Description**

Defines the <b>handleFlags</b> of a <b>TEE_ObjectHandle</b>. The <b>handleFlags</b> determines the access permissions to the data stream associated with the object.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DATA_FLAG_ACCESS_READ = 0x00000001 | The data stream can be read. |
| TEE_DATA_FLAG_ACCESS_WRITE = 0x00000002 | The data stream can be written or truncated. |
| TEE_DATA_FLAG_ACCESS_WRITE_META = 0x00000004 | The data stream can be deleted or renamed. |
| TEE_DATA_FLAG_SHARE_READ = 0x00000010 | Multiple TEE_ObjectHandles can be opened for concurrent read. |
| TEE_DATA_FLAG_SHARE_WRITE = 0x00000020 | Multiple TEE_ObjectHandles can be opened for concurrent write. |
| TEE_DATA_FLAG_CREATE = 0x00000200 | Reserved. |
| TEE_DATA_FLAG_EXCLUSIVE = 0x00000400 | Protect the existing file with the same name. Throw an error if the file with the same name exists; create a data file otherwise. |
| TEE_DATA_FLAG_OVERWRITE = 0x00000400 | Protect the existing file with the same name. Throw an error if the file with the same name exists; create a data file otherwise. |
| TEE_DATA_FLAG_GID = 0x02000000 | If the bit25 is set to 1, it means deriving TA root key by using gid |
| TEE_DATA_FLAG_HUK2 = 0x04000000 | If the bit26 is set to 1, it means deriving TA root key by using huk2 |
| TEE_DATA_FLAG_DERIVE_32BYTES_KEY_ONCE =  0x08000000 | If the bit27 is set to 1, it means deriving the 32-bytes TA root key at one time, if it is 0, it means deriving TA root keys and combined them together. |
| TEE_DATA_FLAG_AES256 =  0x10000000 | Use AES256 if bit 28 is 1; use AES128 if bit 28 is 0. |
| TEE_DATA_FLAG_OPEN_AESC = 0x20000000 | If bit 29 is set to 1, open the earlier version preferentially. |
| TEE_DATA_FLAG_GM =  0x40000000 | If bit30 is set to 1, it means use GM algorithm to protect data |


## Function description

### TEE_CreatePersistentObject()

```c
TEE_Result TEE_CreatePersistentObject(uint32_t storageID, const void *objectID, size_t objectIDLen, uint32_t flags, TEE_ObjectHandle attributes, const void *initialData, size_t initialDataLen, TEE_ObjectHandle *object)
```

**Description**

Creates a persistent object.<br> This function creates a persistent object with initialized <b>TEE_Attribute</b> and data stream. You can use the returned handle to access the <b>TEE_Attribute</b> and data stream of the object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t storageID | Indicates the storage to use. The value is specified by <b>Object_Storage_Constants</b>. |
| const void *objectID | Indicates the pointer to the object identifier, that is, the name of the object to create. |
| size_t objectIDLen | Indicates the length of the object identifier, in bytes. It cannot exceed 128 bytes. |
| uint32_t flags | Indicates the flags of the object created. The value can be one or more of <b>Data_Flag_Constants</b> or <b>Handle_Flag_Constants</b>. |
| TEE_ObjectHandle attributes | Indicates the <b>TEE_ObjectHandle</b> of a transient object from which to take <b>TEE_Attribute</b>. It can be <b>TEE_HANDLE_NULL</b> if the persistent object contains no attribute. |
| const void *initialData | Indicates the pointer to the initial data used to initialize the data stream data. |
| size_t initialDataLen | Indicates the length of the initial data, in bytes. |
| TEE_ObjectHandle *object | Indicates the pointer to the <b>TEE_ObjectHandle</b> returned after the function is successfully executed. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_ITEM_NOT_FOUND</b> if the storage specified by <b>storageID</b> does not exist.          Returns <b>TEE_ERROR_ACCESS_CONFLICT</b> if an access conflict occurs.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation.          Returns <b>TEE_ERROR_STORAGE_NO_SPACE</b> if there is no enough space to create the object. |

### TEE_OpenPersistentObject()

```c
TEE_Result TEE_OpenPersistentObject(uint32_t storageID, const void *objectID, size_t objectIDLen, uint32_t flags, TEE_ObjectHandle *object)
```

**Description**

Opens an existing persistent object.<br> The handle returned can be used to access the <b>TEE_Attribute</b> and data stream of the object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t storageID | Indicates the storage to use. The value is specified by <b>Object_Storage_Constants</b>. |
| const void *objectID | Indicates the pointer to the object identifier, that is, the name of the object to open. |
| size_t objectIDLen | Indicates the length of the object identifier, in bytes. It cannot exceed 128 bytes. |
| uint32_t flags | Indicates the flags of the object opened. The value can be one or more of <b>Data_Flag_Constants</b> or <b>Handle_Flag_Constants</b>. |
| TEE_ObjectHandle *object | Indicates the pointer to the <b>TEE_ObjectHandle</b> returned after the function is successfully executed. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_ITEM_NOT_FOUND</b> if the storage specified by <b>storageID</b> does not exist  or the object identifier cannot be found in the storage.          Returns <b>TEE_ERROR_ACCESS_CONFLICT</b> if an access conflict occurs.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation. |

### TEE_ReadObjectData()

```c
TEE_Result TEE_ReadObjectData(TEE_ObjectHandle object, void *buffer, size_t size, uint32_t *count)
```

**Description**

Reads data from the data stream associated with an object into the buffer.<br> The <b>TEE_ObjectHandle</b> of the object must have been opened with the <b>TEE_DATA_FLAG_ACCESS_READ</b> permission.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the object to read. |
| void *buffer | Indicates the pointer to the buffer used to store the data read. |
| size_t size | Indicates the number of bytes to read. |
| uint32_t *count | Indicates the pointer to the variable that contains the number of bytes read. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation. |

### TEE_WriteObjectData()

```c
TEE_Result TEE_WriteObjectData(TEE_ObjectHandle object, const void *buffer, size_t size)
```

**Description**

Writes bytes from the buffer to the data stream associated with an object.<br> The <b>TEE_ObjectHandle</b> must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE</b> permission.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the object. |
| const void *buffer | Indicates the pointer to the buffer that stores the data to be written. |
| size_t size | Indicates the number of bytes to be written. It cannot exceed 4096 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation.          Returns <b>TEE_ERROR_STORAGE_NO_SPACE</b> if the storage space is not sufficient to complete the operation. |

### TEE_TruncateObjectData()

```c
TEE_Result TEE_TruncateObjectData(TEE_ObjectHandle object, size_t size)
```

**Description**

Changes the size of a data stream.<br> If the size is less than the current size of the data stream, all bytes beyond <b>size</b> are deleted. If the size is greater than the current size of the data stream, add 0s at the end of the stream to extend the stream. The object handle must be opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE</b> permission.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the object. |
| size_t size | Indicates the new size of the data stream. It cannot exceed 4096 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_STORAGE_NO_SPACE</b> if the storage space is not sufficient to complete the operation. |

### TEE_SeekObjectData()

```c
TEE_Result TEE_SeekObjectData(TEE_ObjectHandle object, int32_t offset, TEE_Whence whence)
```

**Description**

Sets the position of the data stream to which <b>TEE_ObjectHandle</b> points.<br> The data position indicator is determined by the start position and an offset together. The <b>whence</b> parameter determines the start position. Its value is set in <b>TEE_Whence</b> as follows: <b>TEE_DATA_SEEK_SET = 0</b>: The start position is the beginning of the data stream. <b>TEE_DATA_SEEK_CUR</b>: The start position is the current position of the data stream. <b>TEE_DATA_SEEK_END</b>: The start position is the end of the data stream. If the parameter <b>offset</b> is a positive number, the data position is moved forward. If <b>offset</b> is a negative number, the data position is moved backward.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the object. |
| int32_t offset | Indicates the number of bytes to move the data position. It cannot exceed 4096 bytes. |
| TEE_Whence whence | Indicates the start position in the data stream to calculate the new position. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_OVERFLOW</b> if the position indicator resulting from this operation  is greater than <b>TEE_DATA_MAX_POSIT</b>. |

### TEE_SyncPersistentObject()

```c
TEE_Result TEE_SyncPersistentObject(TEE_ObjectHandle object)
```

**Description**

Synchronizes the opened <b>TEE_ObjectHandle</b> and the corresponding security attribute file to the disk.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the <b>TEE_ObjectHandle</b> of the object. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_RenamePersistentObject()

```c
TEE_Result TEE_RenamePersistentObject(TEE_ObjectHandle object, void *newObjectID, size_t newObjectIDLen)
```

**Description**

Changes the object identifier.<br> The <b>TEE_ObjectHandle</b> must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE_META</b> permission.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the target object. |
| void *newObjectID | Indicates the pointer to the new object identifier. |
| size_t newObjectIDLen | Indicates the length of the new object identifier. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### TEE_CloseAndDeletePersistentObject1()

```c
TEE_Result TEE_CloseAndDeletePersistentObject1(TEE_ObjectHandle object)
```

**Description**

Closes a <b>TEE_ObjectHandle</b> and deletes the object.<br> The object must be a persistent object, and the object handle must have been opened with the <b>TEE_DATA_FLAG_ACCESS_WRITE_META</b> permission.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the object handle to close. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_STORAGE_NOT_AVAILABLE</b> if the object is stored  in a storage area that is inaccessible currently. |


