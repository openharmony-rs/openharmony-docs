# cloud_disk_error_code.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=59eeb9f6a3c275fe7a80a4997398fbcb8aee3ded translatedAt=2026-11-04T03:36:37.642Z pushedAt=2026-11-04T10:12:33.392Z nl=1 -->

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
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | The sync root path is unauthorized. The sync root path refers to the local directory path used by the application for cloud synchronization. |
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC connection fails.|
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | The number of sync root paths exceeds the upper limit.|
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | The sync root path conflicts with the existing sync root path of the application.|
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | The sync root path conflicts with the existing sync root path of another application.|
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | The sync root path fails to be registered.|
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | The sync root path is not registered.|
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | The sync root path fails to be unregistered.|
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | The sync root path does not exist.|
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | The change listener is not registered. |
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | The change listener is already registered. |
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | The change sequence number is invalid or expired. It is recommended to query all change records again. |
| CLOUD_DISK_TRY_AGAIN = 34400014 | A temporary failure occurred. Retry is recommended (for example, excessive underlying I/O load or insufficient memory). |
| CLOUD_DISK_NOT_ALLOWED = 34400015 | This feature is not allowed on the current device.|
| OH_CLOUD_DISK_FILE_ALREADY_EXISTS = 34400016 | A file with the same name already exists under the target path.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_NOT_A_PLACEHOLDER = 34400017 | The target path is not a placeholder file.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_IS_A_PLACEHOLDER = 34400018 | The target path is already a placeholder file.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_HYDRATE_IN_PROGRESS = 34400019 | The placeholder file is being hydrated.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_NO_SPACE_LEFT = 34400020 | Insufficient disk space remaining.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_NOT_REGISTERED = 34400021 | The callback table is not registered.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_ALREADY_REGISTERED = 34400022 | The callback table is already registered.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_NOT_A_DIRECTORY = 34400023 | The parent directory of the target path is not a directory.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_FILE_NOT_EXIST = 34400024 | The target path does not exist.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_NAME_TOO_LONG = 34400025 | The file name or path is too long.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_FILE_TOO_LARGE = 34400026 | The file is too large.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_PLACEHOLDER_CUSTOM_INFO_NOT_FOUND = 34400027 | The placeholder has no custom information.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_PLACEHOLDER_NOT_FULLY_HYDRATED = 34400028 | The placeholder file is not fully hydrated.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_DEHYDRATE_DENIED = 34400029 | The application callback rejected the dehydration operation.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_CANCELLED = 34400030 | The hydration task has been canceled.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_ALREADY_HYDRATED = 34400031 | The placeholder file is already fully hydrated.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_NO_HYDRATION_IN_PROGRESS = 34400032 | No hydration task is in progress.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_INVALID_PLACEHOLDER_STATE = 34400033 | The stored placeholder state is invalid.<br>**Since:** 26.0.1 |
| OH_CLOUD_DISK_HYDRATION_TASK_LIMIT_REACHED = 34400034 | The number of pending placeholder hydration tasks has reached the upper limit.<br>**Since:** 26.0.1 |
