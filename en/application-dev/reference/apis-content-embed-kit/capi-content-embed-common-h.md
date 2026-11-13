# content_embed_common.h

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7789ba94ea6009532e441b120c06b22f43b19e85 translatedAt=2026-10-15T03:45:08.644Z pushedAt=2026-10-16T01:27:15.698Z -->

## Overview

Defines the error codes of the **ContentEmbed** module and enumerates the capabilities supported by embedded documents.

**File to include**: <ContentEmbedKit/content_embed/content_embed_common.h>

**Library:** libcontent_embed_ndk.so

**System capability**: SystemCapability.ContentEmbed.ObjectEditor

**Since**: 24

**Related module:** [ContentEmbed](capi-contentembed.md)

## Summary

### Enumerations

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ContentEmbed_ErrorCode](#contentembed_errorcode) | ContentEmbed_ErrorCode | Defines the error codes of the **ContentEmbed** module.|
| [ContentEmbed_CapabilityCode](#contentembed_capabilitycode) | ContentEmbed_CapabilityCode | Enumerates the capabilities supported by the embedded document object. Multiple capability values can be combined using bit masks. |

### Macros

| Name| Description|
| -- | -- |
| MAX_OEID_LENGTH (1 * 40) | Maximum length of the embedded document OEID.<br>**Since**: 24|

## Enumeration Description

### ContentEmbed_ErrorCode

```c
enum ContentEmbed_ErrorCode
```

**Description**

Defines the error codes of the **ContentEmbed** module.

**Since**: 24

| Enum Item | Description |
| -- | -- |
| CE_ERR_OK = 0 | The operation is successful.<br>**Since:** 24 |
| CE_PERMISSION_DENIED = 201 | Permission verification failed.<br>**Since:** 24 |
| CE_ERR_PARAM_INVALID = 401 | The parameter is invalid. Check whether the parameter type and value range are correct.<br>**Since:** 24 |
| CE_ERR_DEVICE_NOT_SUPPORTED = 801 | This feature is not supported on the device.<br>**Since:** 24 |
| CE_ERR_NULL_POINTER = 35300001 | The pointer is null. The possible cause is that memory allocation fails or an internal error occurs.<br>**Since:** 24 |
| CE_ERR_CLIENT_CALLBACK_NOT_REGISTERED = 35300002 | The corresponding callback is not registered on the client.<br>**Since:** 24 |
| CE_ERR_EXTENSION_ERROR = 35300003 | An unknown error occurred in the OE extension.<br>**Since:** 24 |
| CE_ERR_SYSTEM_ABNORMAL = 35300004 | The system service is abnormal. The possible causes are that the service is not started, the connection is interrupted, or the permission is insufficient.<br>**Since:** 24 |
| CE_ERR_STORAGE_OPERATION_FAILED = 35300005 | An operation on the storage object of the OE document failed.<br>**Since:** 24 |
| CE_ERR_STREAM_OPERATION_FAILED = 35300006 | An operation on the stream object of the OE document failed.<br>**Since:** 24 |
| CE_ERR_FILE_OPERATION_FAILED = 35300007 | The file operation failed. The possible causes are as follows: The file does not exist, the permission is insufficient, the path is incorrect, or the disk space is insufficient.<br>**Since:** 24 |
| CE_ERR_IN_DLP_SANDBOX = 35300008 | The app is running in the DLP sandbox environment and does not support the calling of related functions.<br>**Since:** 24 |
| CE_ERR_IMAGE_PACKER_OPERATION_FAILED = 35300009 | The **ImagePacker** operation failed.<br>**Since:** 24 |
| CE_ERR_CLIENT_CALLBACK_FAILED = 35300010 | An error occurred during execution of a callback registered on the client.<br>**Since:** 24 |
| CE_ERR_EXTENSION_ABNORMAL_EXIT = 35300011 | The OE extension exited unexpectedly.<br>**Since:** 24 |
| CE_ERR_INVALID_LINKING_PATH = 35300012 | A file in a directory that cannot be linked was linked, for example, a file in the app sandbox directory.<br>**Since:** 24 |
| CE_ERR_CONNECT_LIMIT_EXCEED = 35300013 | The number of current OE extension connections exceeds the limit.<br>**Since:** 24 |
| CE_ERR_FILE_NOT_GRANT = 35300014 | The current file is not authorized.<br>**Since:** 24 |
| CE_ERR_DISK_FULL = 35300015 | The current disk space is insufficient.<br>**Since:** 24 |
| CE_ERR_EXTENSION_NOT_SUPPORT = 35300016 | The current OE extension does not support this capability.<br>**Since:** 24 |

### ContentEmbed_CapabilityCode

```c
enum ContentEmbed_CapabilityCode
```

**Description**

Enumerates the capabilities supported by the embedded document object. Multiple capability values can be combined using bit masks.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| CE_CAPABILITY_SUPPORT_SNAPSHOT = 1 << 0 | The snapshot of an OE document can be obtained.<br>**Since**: 24|
| CE_CAPABILITY_SUPPORT_DO_EDIT = 1 << 1 | The OE document can be edited.<br>**Since**: 24|
