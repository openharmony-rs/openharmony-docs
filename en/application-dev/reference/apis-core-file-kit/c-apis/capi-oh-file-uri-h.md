# oh_file_uri.h

## Overview

uri verification and conversion This class is mainly for URI format verification and URI conversion processing; The conversion and operation of the media library type URI is not supported, and the class only converts according to the existing specifications, and there is no guarantee that the conversion result will actually exist.

**Library**: libohfileuri.so

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12

**Related module**: [fileUri](capi-fileuri.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FileManagement_ErrCode OH_FileUri_GetUriFromPath(const char *path, unsigned int length, char **result)](#oh_fileuri_geturifrompath) | Get uri From path. |
| [FileManagement_ErrCode OH_FileUri_GetPathFromUri(const char *uri, unsigned int length, char **result)](#oh_fileuri_getpathfromuri) | Get path From uri. |
| [FileManagement_ErrCode OH_FileUri_GetFullDirectoryUri(const char *uri, unsigned int length, char **result)](#oh_fileuri_getfulldirectoryuri) | Gets the uri of the path or directory where the uri is located. |
| [bool OH_FileUri_IsValidUri(const char *uri, unsigned int length)](#oh_fileuri_isvaliduri) | Check that the incoming uri is valid |
| [FileManagement_ErrCode OH_FileUri_GetFileName(const char *uri, unsigned int length, char **result)](#oh_fileuri_getfilename) | Gets the fileName From uri. This function obtains that the last segment of the URI string is the return value of the function, and the URI of the media type is not supported |

## Function description

### OH_FileUri_GetUriFromPath()

```c
FileManagement_ErrCode OH_FileUri_GetUriFromPath(const char *path, unsigned int length, char **result)
```

**Description**

Get uri From path.

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *path | Input a pointer to the path string. |
| unsigned int length | The length of the input path. |
| char **result | Output a pointer to a uri string. Please use free() to clear the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER}  401 - Invalid input parameter.<br>        {@link ERR_UNKNOWN} 13900042 - Unknow error. The length of the output uri string is 0.<br>        {@link ERR_ENOMEM}  13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileUri_GetPathFromUri()

```c
FileManagement_ErrCode OH_FileUri_GetPathFromUri(const char *uri, unsigned int length, char **result)
```

**Description**

Get path From uri.

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *uri | Input a pointer to the uri string. |
| unsigned int length | The length of the input uri. |
| char **result | Output a pointer to a path string. Please use free() to clear the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_UNKNOWN} 13900042 - Unknow error. The length of the output path string is 0.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileUri_GetFullDirectoryUri()

```c
FileManagement_ErrCode OH_FileUri_GetFullDirectoryUri(const char *uri, unsigned int length, char **result)
```

**Description**

Gets the uri of the path or directory where the uri is located.

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *uri | Input a pointer to the uri string. |
| unsigned int length |  The length of the input uri. |
| char **result | Output a pointer to a uri string. Please use free() to clear the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_ENOENT} 13900002 - No such file or directory.<br>        {@link ERR_UNKNOWN} 13900042 - Unknow error. The length of the output path string is 0.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileUri_IsValidUri()

```c
bool OH_FileUri_IsValidUri(const char *uri, unsigned int length)
```

**Description**

Check that the incoming uri is valid

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *uri | Input a pointer to the uri string. |
| unsigned int length | The length of the input uri. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true: Valid incoming uri, false: Invalid incoming uri. |

### OH_FileUri_GetFileName()

```c
FileManagement_ErrCode OH_FileUri_GetFileName(const char *uri, unsigned int length, char **result)
```

**Description**

Gets the fileName From uri. This function obtains that the last segment of the URI string is the return value of the function, and the URI of the media type is not supported

**System capability**: SystemCapability.FileManagement.AppFileService

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *uri | Input a pointer to the uri string. |
| unsigned int length |  The length of the input uri. |
| char **result | Output a pointer to a FileName string. Please use free() to clear the resource. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.         {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |


