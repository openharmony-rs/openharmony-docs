# oh_fileio.h

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=fa9d8beb34c9c36d5c088263fe228c1ceec6f643 translatedAt=2026-11-03T03:50:11.846Z pushedAt=2026-11-04T03:11:33.475Z nl=1 -->

## Overview

Defines the interfaces of the fileio module, providing native interfaces for obtaining file storage locations to help applications select appropriate access policies based on the file storage location.

**File to include**: <filemanagement/fileio/oh_fileio.h>

**Library**: libohfileio.so

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 12

**Related module**: [FileIO](capi-fileio.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [FileIO_FileLocation](#fileio_filelocation) | FileIO_FileLocation | Enumerates the file locations.|

### Functions

| Name| Description|
| -- | -- |
| [FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)](#oh_fileio_getfilelocation) | Obtains the file storage location. After a successful call, the file storage location is written to the output parameter location. |

## Enum Description

### FileIO_FileLocation

```c
enum FileIO_FileLocation
```

**Description**

Enumerates the file locations.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| LOCAL = 1 | The file is stored on the local device.|
| CLOUD = 2 | The file is stored on the cloud.|
| LOCAL_AND_CLOUD = 3 | The file is stored on the local device and cloud.|


## Function Description

### OH_FileIO_GetFileLocation()

```c
FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)
```

**Description**

Obtains the file storage location. If the operation is successful, the file storage location is written to the output parameter location.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| char *uri | Pointer to the URI string, used to specify the file whose storage location is to be queried. |
| int uriLength | Length of the URI string, excluding the string terminator '\0', in bytes. The value range is (0, 4096]. |
| [FileIO_FileLocation](capi-oh-fileio-h.md#fileio_filelocation) *location | Pointer to the file storage location. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns the FileManagement module error code [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).  <br>401 - Invalid input parameter, pointer is null. <br>ERR_ENOENT 13900002 - No such file or directory. <br>ERR_ENOMEM 13900011 - Failed to apply for memory. |


