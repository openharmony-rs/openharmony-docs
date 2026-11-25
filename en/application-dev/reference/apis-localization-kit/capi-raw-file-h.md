# raw_file.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=ff7b1e8edb2a9edf56e169c7e7bd019daad6c7e8 translatedAt=2026-11-04T03:57:36.506Z pushedAt=2026-11-04T10:13:14.887Z nl=1 -->

## Overview

Provides the capabilities for operating rawfile files, including reading files, getting the file length, getting the offset position, adjusting the offset position, getting the file descriptor, and closing the file descriptor.

**File to include**: <rawfile/raw_file.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) | RawFileDescriptor | Provides rawfile file descriptor information, including the file descriptor of the rawfile, its start position in the HAP package, and its file length.<br>Obtain it through [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata). After use, call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor resources. |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) | RawFileDescriptor64 | Provides rawfile file descriptor information, including the file descriptor of the rawfile, its start position in the HAP package, and its file length. Supports large files larger than 2 GB.<br>Obtain it through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64). After use, call [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) to release the file descriptor resources. |
| [RawFile64](capi-rawfile-rawfile64.md) | RawFile64 | RawFile64 represents an opened rawfile object and is used to access large files of 2 GB or larger. Obtain it through the [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64) function. After use, call [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) to close and release it. |
| [RawFile](capi-rawfile-rawfile.md) | RawFile | RawFile represents an opened rawfile object. Obtain it through the [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile) function. After use, call [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) to close and release it. |

### Functions

| Name| Description|
| -- | -- |
| [int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)](#oh_resourcemanager_readrawfile) | Reads data of a specified length from the current offset position of a rawfile, and moves the offset position backward by the specified length. For example, if the current offset position is 0 and the specified length is 10, the offset position becomes 10 after the data is read. |
| [int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)](#oh_resourcemanager_seekrawfile) | Adjusts the offset position of a rawfile based on the specified offset and offset mode. |
| [long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)](#oh_resourcemanager_getrawfilesize) | Obtains the length of a rawfile, in bytes. |
| [long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)](#oh_resourcemanager_getrawfileremaininglength) | Obtains the remaining length of a rawfile from the current offset position to the end of the file, in bytes. |
| [void OH_ResourceManager_CloseRawFile(RawFile *rawFile)](#oh_resourcemanager_closerawfile) | Closes an opened RawFile object and releases all related resources. |
| [long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)](#oh_resourcemanager_getrawfileoffset) | Obtains the current offset position of a rawfile, in bytes. It can be used to track the progress during segmented reading or to confirm the current offset position after the offset position is adjusted. |
| [bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)](#oh_resourcemanager_getrawfiledescriptor) | Obtains the file descriptor information of a rawfile. After the file descriptor information is obtained, developers can call functions such as pread to read the rawfile. (Deprecated since API version 12) |
| [bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)](#oh_resourcemanager_getrawfiledescriptordata) | Obtains the file descriptor information of a rawfile. After the file descriptor information is obtained, developers can call functions such as pread to read the rawfile. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)](#oh_resourcemanager_releaserawfiledescriptor) | Releases the file descriptor resources of a rawfile. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again. (Deprecated since API version 12) |
| [bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)](#oh_resourcemanager_releaserawfiledescriptordata) | Releases the file descriptor resources of a rawfile. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again. |
| [int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)](#oh_resourcemanager_readrawfile64) | Reads data of a specified length from the current offset position of a rawfile, and moves the offset position backward by the specified length. For example, if the current offset position is 0 and the specified length is 10, the offset position becomes 10 after the data is read.<br> Supports files larger than 2 GB. |
| [int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)](#oh_resourcemanager_seekrawfile64) | Adjusts the offset position of a rawfile based on the specified offset and offset mode. Supports files larger than 2 GB. |
| [int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)](#oh_resourcemanager_getrawfilesize64) | Obtains the length of a rawfile, in bytes. Supports files larger than 2 GB. |
| [int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileremaininglength64) | Obtains the remaining length of a rawfile from the current offset position to the end of the file, in bytes. Supports files larger than 2 GB. |
| [void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)](#oh_resourcemanager_closerawfile64) | Closes an opened RawFile64 object and releases all related resources. |
| [int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileoffset64) | Obtains the current offset position of a rawfile, in bytes. It can be used to track the progress during segmented reading or to confirm the current offset position after the offset position is adjusted.<br> Supports files larger than 2 GB. |
| [bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)](#oh_resourcemanager_getrawfiledescriptor64) | Obtains the file descriptor information of a rawfile. After the file descriptor information is obtained, developers can call functions such as pread to read the rawfile. Supports files larger than 2 GB. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)](#oh_resourcemanager_releaserawfiledescriptor64) | Releases the file descriptor resources of a rawfile. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again. |

## Function Description

### OH_ResourceManager_ReadRawFile()

```c
int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)
```

**Description**

Reads data of a specified length from the current offset position of the rawfile file, and the offset position moves backward by the specified length simultaneously. For example, if the current offset position is [0] and the specified length is 10, the position after reading the data is [10].

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input Parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| void *buf | Output Parameter. Pointer to the buffer that receives the read data. The memory is allocated by the developer and must be released after use. |
| size_t length | Input Parameter. Length of the data to read, in bytes. |

**Returns**

| Type| Description|
| -- | -- |
| int | Length of the data read. Returns 0 if the file has been fully read, no data is available, or rawFile is NULL. |

### OH_ResourceManager_SeekRawFile()

```c
int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)
```

**Description**

Adjusts the offset position of the rawfile file based on the specified offset and offset method.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| long offset | Input parameter. Specified offset, which is an integer. A positive value indicates a backward offset, and a negative value indicates a forward offset. The unit is bytes. |
| int whence | Input parameter. Offset method, with the value 0, 1, or 2.<br>     0: Calculates the offset from the beginning of the file.<br>     1: Calculates the offset from the current position.<br>     2: Calculates the offset from the end of the file. |

**Returns**

| Type| Description|
| -- | -- |
| int | Result code.<br>     Returns 0 if the operation is successful, and the file offset position moves to the specified position.<br>     Returns -1 if the operation fails, and the file offset position remains unchanged. Possible causes include rawFile being NULL, offset exceeding the file range, or an invalid whence value. |

### OH_ResourceManager_GetRawFileSize()

```c
long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)
```

**Description**

Gets the length of the rawfile file, in bytes.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | File length of the rawfile. Returns 0 if rawFile is NULL. |

### OH_ResourceManager_GetRawFileRemainingLength()

```c
long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)
```

**Description**

Gets the remaining length of the rawfile file from the current offset position to the end of the file, in bytes.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input Parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | Returns the remaining length of the rawfile. Returns 0 if rawFile is NULL. |

### OH_ResourceManager_CloseRawFile()

```c
void OH_ResourceManager_CloseRawFile(RawFile *rawFile)
```

**Description**

Closes the opened RawFile object and releases all related resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). After the object is released, the pointer becomes invalid and cannot be used for other operations. |

**Reference**

[OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile)


### OH_ResourceManager_GetRawFileOffset()

```c
long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)
```

**Description**

Gets the current offset position of the rawfile file, in bytes. It can be used to track progress during segmented reading, or to confirm the current offset position after adjusting the offset position.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | Current offset position of the rawfile. Returns 0 if rawFile is NULL. |

### OH_ResourceManager_GetRawFileDescriptor()

```c
bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)
```

**Description**

Gets the rawfile file descriptor information. After obtaining the file descriptor information, developers can call functions such as pread to read the rawfile file.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata)

**Parameters**

| Name                                              | Description|
|---------------------------------------------------| -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| descriptor | Output parameter. Reference to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object, used to return the file descriptor information. After use, [OH_ResourceManager_ReleaseRawFileDescriptor](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor) must be called to release the file descriptor and prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result. true indicates success. false indicates failure. Possible causes are rawFile being NULL, descriptor being NULL, or rawfile file access being denied. |

### OH_ResourceManager_GetRawFileDescriptorData()

```c
bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)
```

**Description**

Gets the rawfile file descriptor information. After obtaining the file descriptor information, developers can call functions such as pread to read the rawfile file.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Output parameter. Pointer to the RawFileDescriptor object, used to return the file descriptor information. After use, call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor to prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result. true indicates success. false indicates failure. Possible causes: rawFile is NULL, descriptor is NULL, or rawfile file access is denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata)

**Parameters**

| Name| Description|
| -- | -- |
| descriptor | Input Parameter. Reference to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to be released. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Indicates the release result. true indicates successful release, and false indicates release failure. The possible causes are that descriptor is NULL or the file descriptor has been released. |

### OH_ResourceManager_ReleaseRawFileDescriptorData()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Input parameter. Pointer to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to be released. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the release result. true indicates successful release, and false indicates release failure. Possible causes are that descriptor is NULL or the file descriptor has already been released. |

### OH_ResourceManager_ReadRawFile64()

```c
int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)
```

**Description**

Reads data of a specified length from the current offset position of the rawfile, and the offset position moves backward by the specified length. For example, if the current offset position is [0] and the specified length is 10, the offset position becomes [10] after the data is read.<br> Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |
| void *buf | Output parameter. Pointer to the buffer that receives the read data. The memory is allocated by the developer and must be released after use. |
| int64_t length | Input parameter. Expected length of the data to read, in bytes. |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Returns the length of data read. Returns 0 if the file has been fully read, no data is available, or rawFile is NULL. |

### OH_ResourceManager_SeekRawFile64()

```c
int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)
```

**Description**

Adjusts the offset position of the rawfile based on the specified offset and offset method. Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |
| int64_t offset | Input parameter. Specified offset, which is an integer. A positive value indicates a backward offset, and a negative value indicates a forward offset. The unit is bytes. |
| int whence | Input parameter. Offset method. The value can be 0, 1, or 2.<br>     0: Calculate the offset from the beginning of the file.<br>     1: Calculate the offset from the current position.<br>     2: Calculate the offset from the end of the file. |

**Returns**

| Type| Description|
| -- | -- |
| int | Result code.<br>     Returns 0 if the operation is successful, and the file offset position moves to the specified position.<br>     Returns -1 if the operation fails, and the file offset position remains unchanged. Possible causes include rawFile being NULL, offset exceeding the file range, or an invalid whence value. |

### OH_ResourceManager_GetRawFileSize64()

```c
int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)
```

**Description**

Obtains the length of the rawfile, in bytes. Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | File length of the rawfile. Returns 0 if rawFile is NULL. |

### OH_ResourceManager_GetRawFileRemainingLength64()

```c
int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)
```

**Description**

Obtains the remaining length of the rawfile from the current offset position to the end of the file, in bytes. Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input Parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Remaining length of the rawfile. 0 is returned if rawFile is NULL. |

### OH_ResourceManager_CloseRawFile64()

```c
void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)
```

**Description**

Closes the opened RawFile64 object and releases all related resources.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). After the object is released, the pointer becomes invalid and cannot be used for other operations. |

**Reference**

[OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64)


### OH_ResourceManager_GetRawFileOffset64()

```c
int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)
```

**Description**

Obtains the current offset position of the rawfile, in bytes. It can be used to track progress during segmented reading, or to confirm the current offset position after adjusting the offset position.<br> Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Returns the current offset position of the rawfile. If rawFile is NULL, returns 0. |

### OH_ResourceManager_GetRawFileDescriptor64()

```c
bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)
```

**Description**

Obtains the rawfile file descriptor information. After obtaining the file descriptor information, developers can call functions such as pread to read the rawfile. Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Output parameter. Pointer to the RawFileDescriptor64 object, used to return the file descriptor information. After use, call [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) to release the file descriptor to prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result. true indicates success. false indicates failure. Possible causes are rawFile being NULL, descriptor being NULL, or rawfile file access being denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor64()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After the release is successful, the fd in the descriptor becomes invalid and cannot be used again.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Input parameter. Pointer to the RawFileDescriptor64 object to release, obtained through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64). |

**Returns**

| Type| Description|
| -- | -- |
| bool | true if the file is released successfully; false otherwise. Possible causes: descriptor is NULL or the file descriptor has been released. |


