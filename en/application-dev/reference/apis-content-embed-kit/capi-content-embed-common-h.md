# content_embed_common.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## Overview

Provides the error code definitions for the ContentEmbed module and the type enumeration descriptions for the capabilities supported by embedded documents.

**File to include**: <ContentEmbedKit/content_embed/content_embed_common.h>

**Library:** libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module:** [ContentEmbed](capi-contentembed.md)

## Summary

### Enumerations

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode](#contentembed_errorcode) | ContentEmbed_ErrorCode | Defines the error codes of the Content Embed Kit.|
| [ContentEmbed_CapabilityCode](#contentembed_capabilitycode) | ContentEmbed_CapabilityCode | Enumerates the capabilities supported by embedded document objects. Multiple capability values can be combined using bit masks.|

### Macros

| Name| Description|
| -- | -- |
| MAX_OEID_LENGTH (1 * 40) | Indicates the maximum string length of the object ID (OEID) of an embedded document.<br>**Since**: 24|

## Enumeration Description

### ContentEmbed_ErrorCode

```c
enum ContentEmbed_ErrorCode
```

**Description**

Defines the error codes of the Content Embed Kit.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| CE_ERR_OK = 0 | The operation is successful.<br>**Since**: 24|
| CE_PERMISSION_DENIED = 201 | Permission verification failed.<br>**Since**: 24|
| CE_ERR_PARAM_INVALID = 401 | Invalid parameter.<br>**Since**: 24|
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | This feature isn\'t supported on your device.<br>**Since**: 24|
| CE_ERR_NULL_POINTER = 35300001 | A null pointer is returned, which may be caused by memory allocation failure or internal error.<br>**Since**: 24|
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | The client has not registered the corresponding callback function.<br>**Since**: 24|
| CE_ERR_EXTENSION_ERROR = 35300003 | An unknown error occurs in the OE Extension.<br>**Since**: 24|
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | The system service is abnormal, possibly because the service is not started, the connection is interrupted, or the permission is insufficient.<br>**Since**: 24|
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | Operations on the Storage object of the OE document failed.<br>**Since**: 24|
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | Operations on the Stream object of the OE document failed.<br>**Since**: 24|
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | The file operation failed, possibly because the file does not exist, the permission is insufficient, the path is incorrect, or the disk space is insufficient.<br>**Since**: 24|
| CE_ERR_IN_DLP_SANDBOX = 35300008 | The current application is running in the DLP sandbox environment and cannot call related functions.<br>**Since**: 24|
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | The ImagePacker operation failed.<br>**Since**: 24|
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | An exception occurred during the execution of the callback function registered by the client.<br>**Since**: 24|
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | The OE Extension exits unexpectedly.<br>**Since**: 24|
| CE_ERR_INVALID_LINKING_PATH = 35300012 | A file that is linked to a directory that cannot be linked to, such as a file in the app sandbox directory.<br>**Since**: 24|
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | The number of connected OE Extensions exceeds the upper limit.<br>**Since**: 24|
| CE_ERR_FILE_NOT_GRANT = 35300014 | The current file is not authorized.<br>**Since**: 24|
| CE_ERR_DISK_FULL = 35300015 | The current disk space is insufficient.<br>**Since**: 24|
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | The current OE Extension does not support this capability.<br>**Since**: 24|

### ContentEmbed_CapabilityCode

```c
enum ContentEmbed_CapabilityCode
```

**Description**

Enumerates the functions supported by embedded document objects. Multiple capability values can be combined using bit masks.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0 | Indicates that the snapshot image of an OE document can be obtained.<br>**Since**: 24|
| CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1 | Indicates that the OE document can be edited.<br>**Since**: 24|
