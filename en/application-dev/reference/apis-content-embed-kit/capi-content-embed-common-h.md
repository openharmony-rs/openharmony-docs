# content_embed_common.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=3fd977e7f3ec49ec14d221bf7599c15661e35034 translatedAt=2026-10-12T12:05:34.522Z pushedAt=2026-10-13T04:58:00.911Z -->

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

| Enum Item | Description |
| -- | -- |
| CE_ERR_OK = 0 | Operation succeeded.<br>**Since:** 24 |
| CE_PERMISSION_DENIED = 201 | Permission verification failed.<br>**Since:** 24 |
| CE_ERR_PARAM_INVALID = 401 | Invalid parameter.<br>**Since:** 24 |
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | The current device does not support this feature.<br>**Since:** 24 |
| CE_ERR_NULL_POINTER = 35300001 | A null pointer is returned, possibly due to memory allocation failure or an internal error.<br>**Since:** 24 |
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | The client has not registered the corresponding callback.<br>**Since:** 24 |
| CE_ERR_EXTENSION_ERROR = 35300003 | An unknown error occurred in the OE Extension.<br>**Since:** 24 |
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | The system service is abnormal, possibly because the service is not started, the connection is interrupted, or the permission is insufficient.<br>**Since:** 24 |
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | An operation related to the Storage object of the OE document failed.<br>**Since:** 24 |
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | An operation related to the Stream object of the OE document failed.<br>**Since:** 24 |
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | A file operation failed, possibly because the file does not exist, the permission is insufficient, the path is incorrect, or the disk space is insufficient.<br>**Since:** 24 |
| CE_ERR_IN_DLP_SANDBOX = 35300008 | The current application is running in a DLP sandbox environment, and the related features are not supported.<br>**Since:** 24 |
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | The ImagePacker operation failed.<br>**Since:** 24 |
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | An exception occurred while the callback registered by the client was being executed.<br>**Since:** 24 |
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | The OE Extension exited unexpectedly.<br>**Since:** 24 |
| CE_ERR_INVALID_LINKING_PATH = 35300012 | A file in a directory that is not allowed to be linked is linked, for example, a file in the application sandbox directory.<br>**Since:** 24 |
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | The current OE Extension connections exceed the limit.<br>**Since:** 24 |
| CE_ERR_FILE_NOT_GRANT = 35300014 | The current file is not authorized.<br>**Since:** 24 |
| CE_ERR_DISK_FULL = 35300015 | The current disk space is insufficient.<br>**Since:** 24 |
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | The current OE Extension does not support this capability.<br>**Since:** 24 |

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
