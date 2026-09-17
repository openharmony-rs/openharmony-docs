# oh_fileio.h

## Overview

Defines the native APIs used to obtain the location of a file.

**Library**: libohfileio.so

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 12

**Related module**: [FileIO](capi-fileio.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [FileIO_FileLocation](#fileio_filelocation) | FileIO_FileLocation | Enumerates the file location. |

### Function

| Name | Description |
| -- | -- |
| [FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)](#oh_fileio_getfilelocation) | Obtains the location of a file. |

## Enum type description

### FileIO_FileLocation

```c
enum FileIO_FileLocation
```

**Description**

Enumerates the file location.

**Since**: 12

| Enum item | Description |
| -- | -- |
| LOCAL = 1 | The file is stored on the local device.<br>**Since**: 12 |
| CLOUD = 2 | The file is stored on the cloud.<br>**Since**: 12 |
| LOCAL_AND_CLOUD = 3 | The file is stored on the local device and cloud.<br>**Since**: 12 |


## Function description

### OH_FileIO_GetFileLocation()

```c
FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)
```

**Description**

Obtains the location of a file.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *uri | Pointer to the URI of the file. |
| int uriLength | Length of the URI. |
| [FileIO_FileLocation](capi-oh-fileio-h.md#fileio_filelocation) *location | Pointer to the location of the file obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Return the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>        {@link ERR_ENOENT} 13900002 - No such file or directory.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |


