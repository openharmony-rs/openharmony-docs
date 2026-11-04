# raw_file.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=ff7b1e8edb2a9edf56e169c7e7bd019daad6c7e8 translatedAt=2026-11-03T13:34:23.863Z pushedAt=2026-11-04T08:47:59.719Z nl=1 -->

## Overview

Provides the capability to operate rawfile files, including reading files, obtaining the file length, obtaining the offset position, adjusting the offset position, obtaining the file descriptor, and closing the file descriptor.

**File to include**: <rawfile/raw_file.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) | RawFileDescriptor | Provides the file descriptor information of a rawfile, including the file descriptor, start position in the HAP package, and file length of the rawfile.<br>Obtain it through [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata), and call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor resources after use. |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) | RawFileDescriptor64 | Provides the file descriptor information of a rawfile, including the file descriptor, start position in the HAP package, and file length of the rawfile. Supports large files greater than 2 GB.<br>Obtain it through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64), and call [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) to release the file descriptor resources after use. |
| [RawFile64](capi-rawfile-rawfile64.md) | RawFile64 | RawFile64 represents an opened rawfile object, used to access large files of 2 GB or larger. Obtain it through the [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64) function, and call [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) to close and release it after use. |
| [RawFile](capi-rawfile-rawfile.md) | RawFile | RawFile represents an opened rawfile object. Obtain it through the [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile) function, and call [OH_ResourceManager_CloseRawFile](capi-raw-file-h.md#oh_resourcemanager_closerawfile) to close and release it after use. |

### Functions

| Name| Description|
| -- | -- |
| [int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)](#oh_resourcemanager_readrawfile) | Reads data of a specified length from the current offset position of a rawfile, and the offset position moves backward by the specified length. If the current offset position is [0] and the specified length is 10, the offset position becomes [10] after the data is read. |
| [int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)](#oh_resourcemanager_seekrawfile) | Adjusts the offset position of a rawfile based on the specified offset and offset method. |
| [long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)](#oh_resourcemanager_getrawfilesize) | Obtains the length of a rawfile, in bytes. |
| [long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)](#oh_resourcemanager_getrawfileremaininglength) | Obtains the remaining length of a rawfile from the current offset position to the end of the file, in bytes. |
| [void OH_ResourceManager_CloseRawFile(RawFile *rawFile)](#oh_resourcemanager_closerawfile) | Closes an opened RawFile object and releases all related resources. |
| [long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)](#oh_resourcemanager_getrawfileoffset) | Obtains the current offset position of a rawfile, in bytes. It can be used to track progress during segmented reading, or to confirm the current offset position after adjusting it. |
| [bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)](#oh_resourcemanager_getrawfiledescriptor) | Obtains the descriptor information of a rawfile. After obtaining the descriptor information, developers can call functions such as pread to read the rawfile. (Deprecated since API version 12) |
| [bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)](#oh_resourcemanager_getrawfiledescriptordata) | Obtains the descriptor information of a rawfile. After obtaining the descriptor information, developers can call functions such as pread to read the rawfile. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)](#oh_resourcemanager_releaserawfiledescriptor) | Releases the descriptor resources of a rawfile. After a successful release, the fd in descriptor becomes invalid and cannot be used again. (Deprecated since API version 12) |
| [bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)](#oh_resourcemanager_releaserawfiledescriptordata) | Releases the descriptor resources of a rawfile. After a successful release, the fd in descriptor becomes invalid and cannot be used again. |
| [int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)](#oh_resourcemanager_readrawfile64) | Reads data of a specified length from the current offset position of a rawfile, and the offset position moves backward by the specified length. If the current offset position is [0] and the specified length is 10, the offset position becomes [10] after the data is read.<br> Supports large files greater than 2 GB. |
| [int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)](#oh_resourcemanager_seekrawfile64) | Adjusts the offset position of a rawfile based on the specified offset and offset method. Supports large files greater than 2 GB. |
| [int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)](#oh_resourcemanager_getrawfilesize64) | Obtains the length of a rawfile, in bytes. Supports large files greater than 2 GB. |
| [int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileremaininglength64) | Obtains the remaining length of a rawfile from the current offset position to the end of the file, in bytes. Supports large files greater than 2 GB. |
| [void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)](#oh_resourcemanager_closerawfile64) | Closes an opened RawFile64 object and releases all related resources. |
| [int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileoffset64) | Obtains the current offset position of a rawfile, in bytes. It can be used to track progress during segmented reading, or to confirm the current offset position after adjusting it.<br> Supports large files greater than 2 GB. |
| [bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)](#oh_resourcemanager_getrawfiledescriptor64) | Obtains the descriptor information of a rawfile. After obtaining the descriptor information, developers can call functions such as pread to read the rawfile. Supports large files greater than 2 GB. |
| [bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)](#oh_resourcemanager_releaserawfiledescriptor64) | Releases the descriptor resources of a rawfile. After a successful release, the fd in descriptor becomes invalid and cannot be used again. |

## Function Description

### OH_ResourceManager_ReadRawFile()

```c
int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)
```

**Description**

Reads data of a specified length from the current offset position of a rawfile, and the offset position moves backward by the specified length. If the current offset position is [0] and the specified length is 10, the offset position becomes [10] after the data is read.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| void *buf | Output parameter. Pointer to the buffer that receives the read data. The memory is allocated by the developer and must be released after use. |
| size_t length | Input parameter. Expected length of the data to read, in bytes. |

**Returns**

| Type| Description|
| -- | -- |
| int | Length of the data read. Returns 0 if the file has been fully read, no data is available, or rawFile is NULL. |

### OH_ResourceManager_SeekRawFile()

```c
int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)
```

**Description**

Adjusts the offset position of a rawfile based on the specified offset and offset method.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| long offset | Input parameter. Specified offset, which is an integer. A positive value indicates a backward offset, and a negative value indicates a forward offset. The unit is Byte. |
| int whence | Input parameter. Offset method, with values 0, 1, and 2.<br>     0: calculates the offset position from the beginning of the file.<br>     1: calculates the offset position from the current position.<br>     2: calculates the offset position from the end of the file. |

**Returns**

| Type| Description|
| -- | -- |
| int | Result of the positioning operation.<br>     Returns 0 if the operation is successful and the file offset position is moved to the specified position.<br>     Returns -1 if the operation fails and the file offset position remains unchanged. Possible causes include rawFile being NULL, offset exceeding the file range, or an invalid whence value. |

### OH_ResourceManager_GetRawFileSize()

```c
long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)
```

**Description**

Obtains the file length of a rawfile, in bytes.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | File length of the rawfile. If rawFile is NULL, 0 is returned. |

### OH_ResourceManager_GetRawFileRemainingLength()

```c
long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)
```

**Description**

Obtains the remaining length from the current offset position to the end of a rawfile, in bytes.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | Remaining length of the rawfile. 0 if rawFile is NULL. |

### OH_ResourceManager_CloseRawFile()

```c
void OH_ResourceManager_CloseRawFile(RawFile *rawFile)
```

**Description**

Closes an opened RawFile object and releases all related resources.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). After release, the pointer becomes invalid and cannot be used again for other operations. |

**Reference**

[OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile)


### OH_ResourceManager_GetRawFileOffset()

```c
long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)
```

**Description**

Obtains the current offset position of a rawfile, in bytes. It can be used to track the progress during segmented reading, or to confirm the current offset position after adjusting the offset position.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |

**Returns**

| Type| Description|
| -- | -- |
| long | Returns the current offset position of the rawfile. If rawFile is NULL, returns 0. |

### OH_ResourceManager_GetRawFileDescriptor()

```c
bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)
```

**Description**

Obtains the file descriptor information of a rawfile. After obtaining the file descriptor information, developers can call functions such as pread to read the rawfile.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata)

**Parameters**

| Name                                              | Description|
|---------------------------------------------------| -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| descriptor | Output parameter. Reference to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object, used to return the file descriptor information. After use, call [OH_ResourceManager_ReleaseRawFileDescriptor](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor) to release the file descriptor and prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result of the operation. true indicates that the operation is successful. false indicates that the operation fails. Possible causes include rawFile being NULL, descriptor being NULL, or access to the rawfile being denied. |

### OH_ResourceManager_GetRawFileDescriptorData()

```c
bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)
```

**Description**

Obtains the file descriptor information of a rawfile. After obtaining the file descriptor information, developers can call functions such as pread to read the rawfile.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Input parameter. Pointer to the RawFile object, obtained through [OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile). |
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Output parameter. Pointer to the RawFileDescriptor object, used to return the file descriptor information. After use, call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor to prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result. true indicates that the file is obtained successfully. false indicates that the file fails to be obtained. Possible causes: rawFile is NULL, descriptor is NULL, or access to the rawfile is denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After successful release, the fd in descriptor becomes invalid and cannot be used again.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata)

**Parameters**

| Name| Description|
| -- | -- |
| descriptor | Input parameter. Pointer to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to release. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the release result. true indicates that the release is successful, and false indicates that the release failed. Possible causes: descriptor is NULL or the file descriptor has been released. |

### OH_ResourceManager_ReleaseRawFileDescriptorData()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After successful release, the fd in descriptor becomes invalid and cannot be used again.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | Input parameter. Pointer to the [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) object to release. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the release result. true indicates that the release is successful, and false indicates that the release failed. Possible causes: descriptor is NULL or the file descriptor has been released. |

### OH_ResourceManager_ReadRawFile64()

```c
int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)
```

**Description**

Reads data of the specified length from the current offset position of the rawfile, and the offset position moves backward by the specified length. For example, if the current offset position is [0] and the specified length is 10, the offset position becomes [10] after reading.<br> Supports files larger than 2 GB.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |
| void *buf | Output parameter. Pointer to the buffer that receives the read data. The developer allocates the memory and releases it after use. |
| int64_t length | Input parameter. Expected length of the data to read, in bytes. |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Length of the data read. If the file has been fully read and no data is available, or if rawFile is NULL, 0 is returned. |

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
| int64_t offset | Input parameter. Specified offset, which is an integer. A positive value indicates a backward offset, and a negative value indicates a forward offset. The unit is Byte. |
| int whence | Input parameter. Offset method. The value can be 0, 1, or 2.<br>     0: Calculate the offset position from the beginning of the file.<br>     1: Calculate the offset position from the current position.<br>     2: Calculate the offset position from the end of the file. |

**Returns**

| Type| Description|
| -- | -- |
| int | Positioning result.<br>     Returns 0 if the operation is successful, and the file offset position moves to the specified position.<br>     Returns -1 if the operation fails, and the file offset position remains unchanged. Possible causes include rawFile being NULL, offset exceeding the file range, or an invalid whence value. |

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
| int64_t | File length of the rawfile. If rawFile is NULL, 0 is returned. |

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
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Remaining length of the rawfile. If rawFile is NULL, 0 is returned. |

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
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to the RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). After release, the pointer becomes invalid and cannot be used for other operations. |

**Reference**

[OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64)


### OH_ResourceManager_GetRawFileOffset64()

```c
int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)
```

**Description**

Obtains the current offset position of the rawfile, in bytes. It can be used to track progress during segmented reading or to confirm the current offset position after adjusting the offset position.<br> Supports files larger than 2 GB.

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
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Input parameter. Pointer to a RawFile64 object, obtained through [OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64). |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Output parameter. Pointer to a RawFileDescriptor64 object, used to return the file descriptor information. After use, [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) must be called to release the file descriptor and prevent file descriptor leaks. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the result. true indicates success. false indicates failure. Possible causes: rawFile is NULL, descriptor is NULL, or rawfile file access is denied. |

### OH_ResourceManager_ReleaseRawFileDescriptor64()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)
```

**Description**

Releases the rawfile file descriptor resource. After successful release, the fd in descriptor becomes invalid and cannot be used again.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | Input parameter. Pointer to the RawFileDescriptor64 object to be released, obtained through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Release result. true indicates successful release, and false indicates release failure. Possible causes: descriptor is NULL or the file descriptor has been released. |


