# raw_file.h

## Overview

Provides the capabilities to operate on rawfiles, including reading files, obtaining the file length, obtaining the current offset, seeking to a specific position, obtaining the file descriptor, and closing the file descriptor.

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) | RawFileDescriptor | Provides rawfile file descriptor information, including the file descriptor, start position within the HAP, and file length.<br>This information is obtained through [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata), and must be released through [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) after use. |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) | RawFileDescriptor64 | Provides the rawfile file descriptor information, including the file descriptor, start position within the HAP, and file length. Large files larger than 2 GB are supported.<br>This information is obtained through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64), and must be released through [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) after use. |
| [RawFile64](capi-rawfile-rawfile64.md) | - | `RawFile64` represents an opened rawfile object, which is used for accessing large files of 2 GB and above. It is obtained through {@link OH_ResourceManager_OpenRawFile64}, and must be closed and released through [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) after use. |
| [RawFile](capi-rawfile-rawfile.md) | RawFile | `RawFile` represents an opened rawfile object. It is obtained through {@link OH_ResourceManager_OpenRawFile}, and must be closed and released through [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) after use. |

### Macro

| Name | Description |
| -- | -- |
| GLOBAL_RAW_FILE_H | Provides the capabilities to operate on rawfiles, including reading files, obtaining the file length, obtaining the current offset, seeking to a specific position, obtaining the file descriptor, and closing the file descriptor.<br>**Since**: 8<br>**System capability**: SystemCapability.Global.ResourceManager |

### Function

| Name | Description |
| -- | -- |
| [int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)](#oh_resourcemanager_readrawfile) | Reads data of the specified length from the current offset position of a rawfile file. The offset position moves forward by the specified length after the read operation. For example, if the current offset position is [0] and the specified length is 10, the offset position after data reading is [10]. |
| [int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)](#oh_resourcemanager_seekrawfile) | Adjusts the offset position of a rawfile based on the specified offset and offset mode. |
| [long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)](#oh_resourcemanager_getrawfilesize) | Obtains the length (in bytes) of a rawfile. |
| [long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)](#oh_resourcemanager_getrawfileremaininglength) | Obtains the remaining length (in bytes) of a rawfile from the current offset position to the end of the file. |
| [void OH_ResourceManager_CloseRawFile(RawFile *rawFile)](#oh_resourcemanager_closerawfile) | Closes a `RawFile` object and releases all associated resources. |
| [long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)](#oh_resourcemanager_getrawfileoffset) | Obtains the current offset position (in bytes) of a rawfile. This information can be used to track progress during segmented reading, or to confirm the current offset position after seeking. |
| [bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)](#oh_resourcemanager_getrawfiledescriptor) | Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile.(Deprecated in API12) |
| [bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)](#oh_resourcemanager_getrawfiledescriptordata) | Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)](#oh_resourcemanager_releaserawfiledescriptor) | Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.(Deprecated in API12) |
| [bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)](#oh_resourcemanager_releaserawfiledescriptordata) | Releases rawfile file descriptor resources. After successful release, `fd` in `descriptor` becomes invalid and cannot be used any more. |
| [int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)](#oh_resourcemanager_readrawfile64) | Reads data of the specified length from the current offset position of a rawfile file. The offset position moves forward by the specified length after the read operation. For example, if the current offset position is [0] and the specified length is 10, the offset position after data reading is [10]. <br>Files larger than 2 GB are supported. |
| [int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)](#oh_resourcemanager_seekrawfile64) | Adjusts the offset position of a rawfile based on the specified offset and offset mode. Files larger than 2 GB are supported. |
| [int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)](#oh_resourcemanager_getrawfilesize64) | Obtains the length (in bytes) of a rawfile. Files larger than 2 GB are supported. |
| [int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileremaininglength64) | Obtains the remaining length (in bytes) of a rawfile from the current offset position to the end of the file. Files larger than 2 GB are supported. |
| [void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)](#oh_resourcemanager_closerawfile64) | Closes a `RawFile64` object and releases all associated resources. |
| [int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileoffset64) | Obtains the current offset position (in bytes) of a rawfile. This information can be used to track progress during segmented reading, or to confirm the current offset position after seeking. <br>Files larger than 2 GB are supported. |
| [bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)](#oh_resourcemanager_getrawfiledescriptor64) | Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile. Files larger than 2 GB are supported. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)](#oh_resourcemanager_releaserawfiledescriptor64) | Releases rawfile file descriptor resources. After successful release, `fd` in `descriptor` becomes invalid and cannot be used any more. |

## Function description

### OH_ResourceManager_ReadRawFile()

```c
int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)
```

**Description**

Reads data of the specified length from the current offset position of a rawfile file. The offset position moves forward by the specified length after the read operation. For example, if the current offset position is [0] and the specified length is 10, the offset position after data reading is [10].

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |
| void *buf | Output parameter. Pointer to the buffer for receiving the read data. The memory is allocated by you and needs to be freed after use. |
| size_t length | Input parameter. Expected length of data to be read, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Length of the data read. If the file has been read and no data is available for reading, or if `rawFile` is      `NULL`, `0` is returned. |

### OH_ResourceManager_SeekRawFile()

```c
int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)
```

**Description**

Adjusts the offset position of a rawfile based on the specified offset and offset mode.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |
| long offset | Input parameter. Specified offset. The value is an integer. A positive value indicates backward offset, and a negative value indicates forward offset. The unit is bytes. |
| int whence | Input parameter. Offset mode. The value can be `0`, `1`, or `2`. <br>`0`: The offset is calculated from the beginning of the file. <br>`1`: The offset is calculated from the current position. <br>`2`: The offset is calculated from the end of the file. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Seeking result.      <br>0: The operation is successful and the file offset is moved to the specified position.      <br>-1: The operation fails and the file offset remains unchanged. Possible cause: `rawFile` is `NULL`,      `offset` is out the file range, or `whence` is invalid. |

### OH_ResourceManager_GetRawFileSize()

```c
long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)
```

**Description**

Obtains the length (in bytes) of a rawfile.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |

**Returns**:

| Type | Description |
| -- | -- |
| long | Length of the rawfile. If `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_GetRawFileRemainingLength()

```c
long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)
```

**Description**

Obtains the remaining length (in bytes) of a rawfile from the current offset position to the end of the file.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |

**Returns**:

| Type | Description |
| -- | -- |
| long | Remaining length of the rawfile. If `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_CloseRawFile()

```c
void OH_ResourceManager_CloseRawFile(RawFile *rawFile)
```

**Description**

Closes a `RawFile` object and releases all associated resources.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. After the release, the pointer becomes invalid and cannot be used for other operations. |

**Reference**:

{@link OH_ResourceManager_OpenRawFile}


### OH_ResourceManager_GetRawFileOffset()

```c
long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)
```

**Description**

Obtains the current offset position (in bytes) of a rawfile. This information can be used to track progress during segmented reading, or to confirm the current offset position after seeking.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |

**Returns**:

| Type | Description |
| -- | -- |
| long | Current offset position of the rawfile. If the `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_GetRawFileDescriptor()

```c
bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)
```

**Description**

Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile.

**Since**: 8

**Deprecated**: 12

**Replaced by**: [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata)

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |
| descriptor | Output parameter. Reference to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object, After use, you must call [OH_ResourceManager_ReleaseRawFileDescriptor](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor) to release the file descriptor, preventing file descriptor leakage. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <b>true</b> if the file is opened; returns <b>false</b> if the access to the file is rejected. |

### OH_ResourceManager_GetRawFileDescriptorData()

```c
bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)
```

**Description**

Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to a `RawFile` object, which is obtained through {@link OH_ResourceManager_OpenRawFile}. |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Output parameter. Pointer to the `RawFileDescriptor` object, which is used to return the file descriptor information. After use, you must call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor, preventing file descriptor leakage. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Obtaining result. If the operation is successful, `true` is returned. If the operation fails, `false` is      returned. The possible cause is that `rawFile` or `descriptor` is `NULL` or the access to the rawfile is denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)
```

**Description**

Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.

**Since**: 8

**Deprecated**: 12

**Replaced by**: [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata)

**Parameters**:

| Parameter | Description |
| -- | -- |
| descriptor | Input parameter. Reference to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to be released. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Release result. If the operation is successful, `true` is returned. If the operation fails, `false` is      returned. The possible cause is that `descriptor` is `NULL` or the file descriptor has been released. |

### OH_ResourceManager_ReleaseRawFileDescriptorData()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)
```

**Description**

Releases rawfile file descriptor resources. After successful release, `fd` in `descriptor` becomes invalid and cannot be used any more.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Input parameter. Pointer to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to be released. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Release result. If the operation is successful, `true` is returned. If the operation fails, `false` is      returned. The possible cause is that `descriptor` is `NULL` or the file descriptor has been released. |

### OH_ResourceManager_ReadRawFile64()

```c
int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)
```

**Description**

Reads data of the specified length from the current offset position of a rawfile file. The offset position moves forward by the specified length after the read operation. For example, if the current offset position is [0] and the specified length is 10, the offset position after data reading is [10]. <br>Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |
| void *buf | Output parameter. Pointer to the buffer for receiving the read data. The memory is allocated by you and needs to be freed after use. |
| int64_t length | Input parameter. Expected length of data to be read, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Length of the data read. If the file has been read and no data is available for reading, or if `rawFile` is      `NULL`, `0` is returned. |

### OH_ResourceManager_SeekRawFile64()

```c
int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)
```

**Description**

Adjusts the offset position of a rawfile based on the specified offset and offset mode. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |
| int64_t offset | Input parameter. Specified offset. The value is an integer. A positive value indicates backward offset, and a negative value indicates forward offset. The unit is bytes. |
| int whence | Input parameter. Offset mode. The value can be `0`, `1`, or `2`. <br>`0`: The offset is calculated from the beginning of the file. <br>`1`: The offset is calculated from the current position. <br>`2`: The offset is calculated from the end of the file. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Seeking result.      <br>0: The operation is successful and the file offset is moved to the specified position.      <br>-1: The operation fails and the file offset remains unchanged. Possible cause: `rawFile` is `NULL`,      `offset` is out the file range, or `whence` is invalid. |

### OH_ResourceManager_GetRawFileSize64()

```c
int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)
```

**Description**

Obtains the length (in bytes) of a rawfile. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Length of the rawfile. If `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_GetRawFileRemainingLength64()

```c
int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)
```

**Description**

Obtains the remaining length (in bytes) of a rawfile from the current offset position to the end of the file. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Remaining length of the rawfile. If `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_CloseRawFile64()

```c
void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)
```

**Description**

Closes a `RawFile64` object and releases all associated resources.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. After the release, the pointer becomes invalid and cannot be used for other operations. |

**Reference**:

{@link OH_ResourceManager_OpenRawFile64}


### OH_ResourceManager_GetRawFileOffset64()

```c
int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)
```

**Description**

Obtains the current offset position (in bytes) of a rawfile. This information can be used to track progress during segmented reading, or to confirm the current offset position after seeking. <br>Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Current offset position of the rawfile. If the `rawFile` is `NULL`, `0` is returned. |

### OH_ResourceManager_GetRawFileDescriptor64()

```c
bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)
```

**Description**

Obtains the rawfile descriptor information. After obtaining the file descriptor information, you can call functions such as **pread** to read the rawfile. Files larger than 2 GB are supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a `RawFile64` object, which is obtained through {@link OH_ResourceManager_OpenRawFile64}. |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Output parameter. Pointer to the `RawFileDescriptor64` object, which is used to return the file descriptor information. After use, you must call [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) to release the file descriptor, preventing file descriptor leakage. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Obtaining result. If the operation is successful, `true` is returned. If the operation fails, `false` is      returned. The possible cause is that `rawFile` or `descriptor` is `NULL` or the access to the rawfile is denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor64()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)
```

**Description**

Releases rawfile file descriptor resources. After successful release, `fd` in `descriptor` becomes invalid and cannot be used any more.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Input parameter. Pointer to the `RawFileDescriptor64` object to be released, which is obtained through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Release result. If the operation is successful, `true` is returned. If the operation fails, `false` is      returned. The possible cause is that `descriptor` is `NULL` or the file descriptor has been released. |


