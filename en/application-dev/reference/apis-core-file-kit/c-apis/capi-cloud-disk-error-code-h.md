# cloud_disk_error_code.h

## Overview

This file defines the error codes for the cloud disk management module.

**Library**: libohclouddiskmanager.so

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CloudDisk_ErrorCode](#clouddisk_errorcode) | CloudDisk_ErrorCode | Enumerates the error codes of the cloud disk management module. |

## Enum type description

### CloudDisk_ErrorCode

```c
enum CloudDisk_ErrorCode
```

**Description**

Enumerates the error codes of the cloud disk management module.

**Since**: 21

| Enum item | Description |
| -- | -- |
| CLOUD_DISK_OK = 0 | The API is called successfully.<br>**Since**: 21 |
| CLOUD_DISK_PERMISSION_DENIED = 201 | The permission verification fails.<br>**Since**: 21 |
| CLOUD_DISK_NOT_SUPPORTED = 801 | This feature is not supported on the device.<br>**Since**: 21 |
| CLOUD_DISK_INVALID_ARG = 34400001 | The input parameter is invalid.<br>**Since**: 21 |
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | The sync root path is not authorized.<br>**Since**: 21 |
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC connection fails.<br>**Since**: 21 |
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | The number of sync root paths exceeds the upper limit.<br>**Since**: 21 |
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | The sync root path conflicts with the existing sync root path of the application.<br>**Since**: 21 |
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | The sync root path conflicts with the existing sync root path of another application.<br>**Since**: 21 |
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | The sync root path fails to be registered.<br>**Since**: 21 |
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | The sync root path is not registered.<br>**Since**: 21 |
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | The sync root path fails to be unregistered.<br>**Since**: 21 |
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | The sync root path does not exist.<br>**Since**: 21 |
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | The change listener is not registered.<br>**Since**: 21 |
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | The change listener has been registered.<br>**Since**: 21 |
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | The change sequence is invalid. You are advised to query all change sequences.<br>**Since**: 21 |
| CLOUD_DISK_TRY_AGAIN = 34400014 | Temporary failure (for example, due to high underlying I/O load or insufficient memory). Please try again.<br>**Since**: 21 |
| CLOUD_DISK_NOT_ALLOWED = 34400015 | This feature is not allowed on the current device.<br>**Since**: 21 |
| OH_CLOUD_DISK_FILE_ALREADY_EXISTS = 34400016 | A file with the same name already exists in the target path.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_NOT_A_PLACEHOLDER = 34400017 | The target path is not a placeholder file.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_IS_A_PLACEHOLDER = 34400018 | The target path is already a placeholder file.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_HYDRATE_IN_PROGRESS = 34400019 | Hydration in progress.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_NO_SPACE_LEFT = 34400020 | The available disk space is insufficient.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_CALLBACK_NOT_REGISTERED = 34400021 | The callback table is not registered.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_CALLBACK_ALREADY_REGISTERED = 34400022 | The callback table has been registered.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_NOT_A_DIRECTORY = 34400023 | The parent directory of the target path is not a directory.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_FILE_NOT_EXIST = 34400024 | The target path does not exist.<br>**Since**: 26.1.0 |
| OH_CLOUD_DISK_NAME_TOO_LONG = 34400025 | The file name or path is too long.<br>**Since**: 26.1.0 |


