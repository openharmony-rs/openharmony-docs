# cloud_disk_error_code.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

## Overview

This file defines the error codes for the cloud disk management module.

**File to include**: <filemanagement/clouddiskmanager/cloud_disk_error_code.h>

**Library**: libohclouddiskmanager.so

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CloudDisk_ErrorCode](#clouddisk_errorcode) | CloudDisk_ErrorCode | Enumerates the error codes of the cloud disk management module.|

## Enum Description

### CloudDisk_ErrorCode

```c
enum CloudDisk_ErrorCode
```

**Description**

Enumerates the error codes of the cloud disk management module.

**Since**: 21

| Value| Description|
| -- | -- |
| CLOUD_DISK_OK = 0 | The API is called successfully.|
| CLOUD_DISK_PERMISSION_DENIED = 201 | The permission verification fails.|
| CLOUD_DISK_NOT_SUPPORTED = 801 | This feature is not supported on the device.|
| CLOUD_DISK_INVALID_ARG = 34400001 | The input parameter is invalid.|
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | The sync root path is not authorized.|
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC connection fails.|
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | The number of sync root paths exceeds the upper limit.|
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | The sync root path conflicts with the existing sync root path of the application.|
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | The sync root path conflicts with the existing sync root path of another application.|
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | The sync root path fails to be registered.|
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | The sync root path is not registered.|
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | The sync root path fails to be unregistered.|
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | The sync root path does not exist.|
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | The change listener is not registered.|
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | The change listener has been registered.|
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | The change sequence is invalid. You are advised to query all change sequences.|
| CLOUD_DISK_TRY_AGAIN = 34400014 | Temporary failure (for example, due to high underlying I/O load or insufficient memory). Please try again.|
| CLOUD_DISK_NOT_ALLOWED = 34400015 | This feature is not allowed on the current device.|
