# raw_file.h

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides functions related to rawfiles, including searching for, reading, and closing rawfiles.

**File to include**: <rawfile/raw_file.h>

**Library**: librawfile.z.so

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

## Summary

### Structs

| Name| typedef Keyword| Description                                                                                                                                                                     |
| -- | -- |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) | RawFileDescriptor | Defines the file descriptor information of a file in the **rawfile** directory. **RawFileDescriptor** is an output parameter of [OH_ResourceManager_GetRawFileDescriptor](#oh_resourcemanager_getrawfiledescriptor). It contains the file descriptor of a rawfile and the start position and length of the rawfile in the HAP.        |
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) | RawFileDescriptor64 | Defines the file descriptor of a large rawfile. **RawFileDescriptor64** is an output parameter of [OH_ResourceManager_GetRawFileDescriptor64](#oh_resourcemanager_getrawfiledescriptor64). It contains the file descriptor of a rawfile and the start position and length of the rawfile in the HAP.|
| [RawFile](capi-rawfile-rawfile.md) | RawFile | Provides access to rawfiles.                                                                                                                                                       |
| [RawFile64](capi-rawfile-rawfile64.md) | RawFile64 | Provides access to large rawfiles.                                                                                                                                                     |

### Functions

| Name| Description|
| -- | -- |
| [int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)](#oh_resourcemanager_readrawfile) | Reads data of the specified length from the current position in a rawfile.|
| [int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)](#oh_resourcemanager_seekrawfile) | Searches for the data read/write position in a rawfile based on the specified offset.|
| [long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)](#oh_resourcemanager_getrawfilesize) | Obtains the length of the rawfile, in long.|
| [long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)](#oh_resourcemanager_getrawfileremaininglength) | Obtains the remaining length of the rawfile, in long.|
| [void OH_ResourceManager_CloseRawFile(RawFile *rawFile)](#oh_resourcemanager_closerawfile) | Closes a [RawFile](capi-rawfile-rawfile.md) and releases all associated resources.|
| [long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)](#oh_resourcemanager_getrawfileoffset) | Obtains the current offset of a rawfile, in long. Current offset of the rawfile.|
| [bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)](#oh_resourcemanager_getrawfiledescriptor) | Opens a rawfile based on the specified offset (in long) and file length (in long) and obtains the file descriptor. The file descriptor obtained can be used to read the file. (It is deprecated in API version 12.)|
| [bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)](#oh_resourcemanager_getrawfiledescriptordata) | Opens a rawfile based on the specified offset (in long) and file length (in long) and obtains the file descriptor. The file descriptor obtained can be used to read the file.|
| [bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)](#oh_resourcemanager_releaserawfiledescriptor) | Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use. (It is deprecated in API version 12.)|
| [bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)](#oh_resourcemanager_releaserawfiledescriptordata) | Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.|
| [int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)](#oh_resourcemanager_readrawfile64) | Reads data of the specified length from the current position in a large rawfile.|
| [int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)](#oh_resourcemanager_seekrawfile64) | Searches for the data read/write position in a large rawfile based on the specified offset.|
| [int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)](#oh_resourcemanager_getrawfilesize64) | Obtains the length of a large rawfile, in int64_t.|
| [int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileremaininglength64) | Obtains the remaining length of a large rawfile, in int64_t.|
| [void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)](#oh_resourcemanager_closerawfile64) | Closes an opened [RawFile64](capi-rawfile-rawfile64.md) and releases all associated resources.|
| [int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)](#oh_resourcemanager_getrawfileoffset64) | Obtains the offset of a large rawfile, in int64_t.|
| [bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)](#oh_resourcemanager_getrawfiledescriptor64) | Opens a large rawfile based on the specified offset (in int64_t) and file length (in int64_t) and obtains the file descriptor. The file descriptor obtained can be used to read the file.|
| [bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)](#oh_resourcemanager_releaserawfiledescriptor64) | Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.|


## Function Description

### OH_ResourceManager_ReadRawFile()

```c
int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length)
```

**Description**

Reads data of the specified length from the current position in a rawfile.

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|
| void *buf | Pointer to the buffer for receiving the read data.|
| size_t length | Length of the data to read.|

**Returns**

| Type| Description|
| -- | -- |
| int | Number of read bytes. If the read length exceeds the length of the file end or rawfile is empty, **0** is returned.|

### OH_ResourceManager_SeekRawFile()

```c
int OH_ResourceManager_SeekRawFile(const RawFile *rawFile, long offset, int whence)
```

**Description**

Searches for the data read/write position in a rawfile based on the specified offset.

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
|[const RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|
| long offset | Specified offset.|
| int whence | Read/Write position. The options are as follows:<br> **0**: The read/write position is the start position of the file plus the offset.<br> **1**: The read/write position is the current position plus the offset.<br> **2**: The read/write position is the end position of the file plus the offset.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** if the search is successful; **-1** otherwise.|

### OH_ResourceManager_GetRawFileSize()

```c
long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)
```

**Description**

Obtains the length of the rawfile, in long.

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|

**Returns**

| Type| Description|
| -- | -- |
| long | Overall length of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_GetRawFileRemainingLength()

```c
long OH_ResourceManager_GetRawFileRemainingLength(const RawFile *rawFile)
```

**Description**

Obtains the remaining length of the rawfile, in long.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|

**Returns**

| Type| Description|
| -- | -- |
| long | Remaining length of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_CloseRawFile()

```c
void OH_ResourceManager_CloseRawFile(RawFile *rawFile)
```

**Description**

Closes a [RawFile](capi-rawfile-rawfile.md) and releases all associated resources.

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
| [RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|

**Reference**

[OH_ResourceManager_OpenRawFile](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile)

### OH_ResourceManager_GetRawFileOffset()

```c
long OH_ResourceManager_GetRawFileOffset(const RawFile *rawFile)
```

**Description**

Obtains the current offset of a rawfile, in long. Current offset of the rawfile.

**Since**: 8


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|

**Returns**

| Type| Description|
| -- | -- |
| long | Current offset of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_GetRawFileDescriptor()

```c
bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor)
```

**Description**

Opens a rawfile based on the specified offset (in long) and file length (in long) and obtains the file descriptor. The file descriptor obtained can be used to read the file.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata)

**Parameters**

| Name                                              | Description|
|---------------------------------------------------| -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile  | Pointer to [RawFile](capi-rawfile-rawfile.md). |
|  RawFileDescriptor &descriptor  |  File descriptor of the rawfile, start position of the rawfile in the HAP, and length of the rawfile. |

**Returns**

| Type| Description|
| -- | -- |
| bool | <b>true</b> if the file is opened; returns <b>false</b> if the access to the file is rejected.|

### OH_ResourceManager_GetRawFileDescriptorData()

```c
bool OH_ResourceManager_GetRawFileDescriptorData(const RawFile *rawFile, RawFileDescriptor *descriptor)
```

**Description**

Opens a rawfile based on the specified offset (in long) and file length (in long) and obtains the file descriptor. The file descriptor obtained can be used to read the file.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile](capi-rawfile-rawfile.md) *rawFile | Pointer to [RawFile](capi-rawfile-rawfile.md).|
| [RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | File descriptor of the rawfile, start position of the rawfile in the HAP, and length of the rawfile.|

**Returns**

| Type| Description|
| -- | -- |
| bool | <b>true</b> if the file is opened; returns <b>false</b> if the access to the file is rejected.|



### OH_ResourceManager_ReleaseRawFileDescriptor()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor(const RawFileDescriptor &descriptor)
```

**Description**

Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.

**Since**: 8

**Deprecated from**: 12

**Substitute**: [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata)

**Parameters**

| Name| Description|
| -- | -- |
|[ const RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) &descriptor | File descriptor of the rawfile. It contains the file descriptor, start position in the HAP, and file length.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns <b>true</b> if the file descriptor is released; returns <b>false</b> otherwise.|

### OH_ResourceManager_ReleaseRawFileDescriptorData()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptorData(const RawFileDescriptor *descriptor)
```

**Description**

Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor](capi-rawfile-rawfiledescriptor.md) *descriptor | File descriptor of the rawfile. It contains the file descriptor, start position in the HAP, and file length.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns <b>true</b> if the file descriptor is released; returns <b>false</b> otherwise.|

### OH_ResourceManager_ReadRawFile64()

```c
int64_t OH_ResourceManager_ReadRawFile64(const RawFile64 *rawFile, void *buf, int64_t length)
```

**Description**

Reads data of the specified length from the current position in a large rawfile.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|
| void *buf | Pointer to the buffer for receiving the read data.|
| int64_t length | Length of the data to read.|

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Number of read bytes. If the read length exceeds the length of the file end or rawfile is empty, **0** is returned.|

### OH_ResourceManager_SeekRawFile64()

```c
int OH_ResourceManager_SeekRawFile64(const RawFile64 *rawFile, int64_t offset, int whence)
```

**Description**

Searches for the data read/write position in a large rawfile based on the specified offset.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|
| int64_t offset | Specified offset.|
| int whence | Read/Write position. The options are as follows:<br> **0**: The read/write position is the start position of the file plus the offset.<br> **1**: The read/write position is the current position plus the offset.<br> **2**: The read/write position is the end position of the file plus the offset.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** if the search is successful; **-1** otherwise.|

### OH_ResourceManager_GetRawFileSize64()

```c
int64_t OH_ResourceManager_GetRawFileSize64(RawFile64 *rawFile)
```

**Description**

Obtains the length of a large rawfile, in int64_t.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Overall length of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_GetRawFileRemainingLength64()

```c
int64_t OH_ResourceManager_GetRawFileRemainingLength64(const RawFile64 *rawFile)
```

**Description**

Obtains the remaining length of a large rawfile, in int64_t.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Remaining length of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_CloseRawFile64()

```c
void OH_ResourceManager_CloseRawFile64(RawFile64 *rawFile)
```

**Description**

Closes an opened [RawFile64](capi-rawfile-rawfile64.md) and releases all associated resources.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|

**Reference**

[OH_ResourceManager_OpenRawFile64](capi-raw-file-manager-h.md#oh_resourcemanager_openrawfile64)

### OH_ResourceManager_GetRawFileOffset64()

```c
int64_t OH_ResourceManager_GetRawFileOffset64(const RawFile64 *rawFile)
```

**Description**

Obtains the offset of a large rawfile, in int64_t.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|

**Returns**

| Type| Description|
| -- | -- |
| int64_t | Current offset of the rawfile. If the rawfile is empty, **0** is returned.|

### OH_ResourceManager_GetRawFileDescriptor64()

```c
bool OH_ResourceManager_GetRawFileDescriptor64(const RawFile64 *rawFile, RawFileDescriptor64 *descriptor)
```

**Description**

Opens a large rawfile based on the specified offset (in int64_t) and file length (in int64_t) and obtains the file descriptor. The file descriptor obtained can be used to read the file.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFile64](capi-rawfile-rawfile64.md) *rawFile | Pointer to [RawFile64](capi-rawfile-rawfile64.md).|
| [RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | File descriptor of the rawfile, start position of the rawfile in the HAP, and length of the rawfile.|

**Returns**

| Type| Description|
| -- | -- |
| bool | <b>true</b> if the file is opened; returns <b>false</b> if the access to the file is rejected.|

### OH_ResourceManager_ReleaseRawFileDescriptor64()

```c
bool OH_ResourceManager_ReleaseRawFileDescriptor64(const RawFileDescriptor64 *descriptor)
```

**Description**

Releases the file descriptor of a rawfile. To prevent file descriptor leakage, you are advised to release a rawfile descriptor immediately after use.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [const RawFileDescriptor64](capi-rawfile-rawfiledescriptor64.md) *descriptor | File descriptor of the rawfile. It contains the file descriptor, start position in the HAP, and file length.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns <b>true</b> if the file descriptor is released; returns <b>false</b> otherwise.|
