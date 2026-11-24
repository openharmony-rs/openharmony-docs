# content_embed_common.h

## Overview

Provides the error code definitions for the ContentEmbed module and the type enumeration descriptions for the capabilities supported by embedded documents.

**Library**: libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module**: [ContentEmbed](capi-content-embed-kit-contentembed.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ContentEmbed_ErrorCode](#contentembed_errorcode) | ContentEmbed_ErrorCode | Defines the error codes of the Content Embed Kit. |
| [ContentEmbed_CapabilityCode](#contentembed_capabilitycode) | ContentEmbed_CapabilityCode | Enumerates the functions supported by embedded document objects. Multiple capability values can be combined using bit masks. |

### Macros

| Name | Description |
| -- | -- |
| MAX_OEID_LENGTH (1 * 40) | Indicates the maximum string length of the OEID of an embedded document.<br>**Since**: 24 |

## Enum type description

### ContentEmbed_ErrorCode

```c
enum ContentEmbed_ErrorCode
```

**Description**

Defines the error codes of the Content Embed Kit.

<!--Device-enum ContentEmbed_ErrorCode--><!--Device-enum ContentEmbed_ErrorCode-End-->

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

| Enum item | Description |
| -- | -- |
| CE_ERR_OK = 0 | The operation is successful.<br>**Since**: 24<br><!--Device-CE_ERR_OK = 0--><!--Device-CE_ERR_OK = 0-End--> |
| CE_PERMISSION_DENIED = 201 | Permission verification failed.<br>**Since**: 24<br><!--Device-CE_PERMISSION_DENIED = 201--><!--Device-CE_PERMISSION_DENIED = 201-End--> |
| CE_ERR_PARAM_INVALID = 401 | Invalid parameter.<br>**Since**: 24<br><!--Device-CE_ERR_PARAM_INVALID = 401--><!--Device-CE_ERR_PARAM_INVALID = 401-End--> |
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | This feature isn\'t supported on your device.<br>**Since**: 24<br><!--Device-CE_ERR_DEVICE_NOT_SUPPORTED = 801--><!--Device-CE_ERR_DEVICE_NOT_SUPPORTED = 801-End--> |
| CE_ERR_NULL_POINTER = 35300001 | A null pointer is returned, which may be caused by memory allocation failure or internal error.<br>**Since**: 24<br><!--Device-CE_ERR_NULL_POINTER = 35300001--><!--Device-CE_ERR_NULL_POINTER = 35300001-End--> |
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | The client has not registered the corresponding callback function.<br>**Since**: 24<br><!--Device-CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002--><!--Device-CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002-End--> |
| CE_ERR_EXTENSION_ERROR = 35300003 | An unknown error occurs in the OE Extension.<br>**Since**: 24<br><!--Device-CE_ERR_EXTENSION_ERROR = 35300003--><!--Device-CE_ERR_EXTENSION_ERROR = 35300003-End--> |
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | The system service is abnormal, possibly because the service is not started, the connection is interrupted, or the permission is insufficient.<br>**Since**: 24<br><!--Device-CE_ERR_SYSTEM_ABNORMAL = 35300004--><!--Device-CE_ERR_SYSTEM_ABNORMAL = 35300004-End--> |
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | Operations on the Storage object of the OE document failed.<br>**Since**: 24<br><!--Device-CE_ERR_STORAGE_OPERATION_FAILED = 35300005--><!--Device-CE_ERR_STORAGE_OPERATION_FAILED = 35300005-End--> |
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | Operations on the Stream object of the OE document failed.<br>**Since**: 24<br><!--Device-CE_ERR_STREAM_OPERATION_FAILED = 35300006--><!--Device-CE_ERR_STREAM_OPERATION_FAILED = 35300006-End--> |
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | The file operation failed, possibly because the file does not exist, the permission is insufficient, the path is incorrect, or the disk space is insufficient.<br>**Since**: 24<br><!--Device-CE_ERR_FILE_OPERATION_FAILED = 35300007--><!--Device-CE_ERR_FILE_OPERATION_FAILED = 35300007-End--> |
| CE_ERR_IN_DLP_SANDBOX = 35300008 | The current application is running in the DLP sandbox environment and cannot call related functions.<br>**Since**: 24<br><!--Device-CE_ERR_IN_DLP_SANDBOX = 35300008--><!--Device-CE_ERR_IN_DLP_SANDBOX = 35300008-End--> |
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | The ImagePacker operation failed.<br>**Since**: 24<br><!--Device-CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009--><!--Device-CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009-End--> |
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | An exception occurred during the execution of the callback function registered by the client.<br>**Since**: 24<br><!--Device-CE_ERR_CLIENT_CALLBACK_FAILED = 35300010--><!--Device-CE_ERR_CLIENT_CALLBACK_FAILED = 35300010-End--> |
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | The OE Extension exits unexpectedly.<br>**Since**: 24<br><!--Device-CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011--><!--Device-CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011-End--> |
| CE_ERR_INVALID_LINKING_PATH = 35300012 | A file that is linked to a directory that cannot be linked to, such as a file in the app sandbox directory.<br>**Since**: 24<br><!--Device-CE_ERR_INVALID_LINKING_PATH = 35300012--><!--Device-CE_ERR_INVALID_LINKING_PATH = 35300012-End--> |
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | The number of connected OE Extensions exceeds the upper limit.<br>**Since**: 24<br><!--Device-CE_ERR_CONNECT_LIMIT_EXCEED = 35300013--><!--Device-CE_ERR_CONNECT_LIMIT_EXCEED = 35300013-End--> |
| CE_ERR_FILE_NOT_GRANT = 35300014 | The current file is not authorized.<br>**Since**: 24<br><!--Device-CE_ERR_FILE_NOT_GRANT = 35300014--><!--Device-CE_ERR_FILE_NOT_GRANT = 35300014-End--> |
| CE_ERR_DISK_FULL = 35300015 | The current disk space is insufficient.<br>**Since**: 24<br><!--Device-CE_ERR_DISK_FULL = 35300015--><!--Device-CE_ERR_DISK_FULL = 35300015-End--> |
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | The current OE Extension does not support this capability.<br>**Since**: 24<br><!--Device-CE_ERR_EXTENSION_NOT_SUPPORT = 35300016--><!--Device-CE_ERR_EXTENSION_NOT_SUPPORT = 35300016-End--> |

### ContentEmbed_CapabilityCode

```c
enum ContentEmbed_CapabilityCode
```

**Description**

Enumerates the functions supported by embedded document objects. Multiple capability values can be combined using bit masks.

<!--Device-enum ContentEmbed_CapabilityCode--><!--Device-enum ContentEmbed_CapabilityCode-End-->

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

| Enum item | Description |
| -- | -- |
| CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0 | Indicates that the snapshot image of an OE document can be obtained.<br>**Since**: 24<br><!--Device-CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0--><!--Device-CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0-End--> |
| CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1 | Indicates that the OE document can be edited.<br>**Since**: 24<br><!--Device-CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1--><!--Device-CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1-End--> |


