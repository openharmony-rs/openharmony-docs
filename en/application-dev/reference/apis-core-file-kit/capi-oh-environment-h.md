# oh_environment.h

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## Overview

Defines the native APIs used to obtain the sandbox paths of the user files.

**Header file**: <filemanagement/environment/oh_environment.h>

**Library**: libohenvironment.so

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Since**: 12

**Related module**: [Environment](capi-environment.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)](#oh_environment_getuserdownloaddir) | Obtains the sandbox path of the **Download** root directory.|
| [FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)](#oh_environment_getuserdesktopdir) | Obtains the sandbox path of the **Desktop** root directory.|
| [FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)](#oh_environment_getuserdocumentdir) | Obtains the sandbox path of the **Document** root directory.|

## Function Description

### OH_Environment_GetUserDownloadDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)
```

**Description**

Obtains the sandbox path of the **Download** root directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Double pointer to the path of the **Download** root directory. You also need to include **malloc.h** and use **free()** to release the memory allocated.|

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).|

### OH_Environment_GetUserDesktopDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)
```

**Description**

Obtains the sandbox path of the **Desktop** root directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Double pointer to the path of the **Desktop** root directory. You also need to include **malloc.h** and use **free()** to release the memory allocated.|

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).|

### OH_Environment_GetUserDocumentDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)
```

**Description**

Obtains the sandbox path of the **Document** root directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Double pointer to the path of the **Document** root directory. You also need to include **malloc.h** and use **free()** to release the memory allocated.|

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).|
