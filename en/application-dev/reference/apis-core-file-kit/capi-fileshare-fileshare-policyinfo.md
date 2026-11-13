# FileShare_PolicyInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0a9e482a4ffa553c6c867b65cd7a285444942180 translatedAt=2026-11-03T03:47:11.265Z pushedAt=2026-11-04T03:11:33.464Z nl=1 -->

```c
typedef struct FileShare_PolicyInfo {...} FileShare_PolicyInfo
```

## Overview

Policy information for granting or activating URI access permissions, used to describe the target URI and access mode in cross-application file sharing scenarios.

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *uri | URI for which access permission needs to be granted or activated. It must comply with the system URI format specification. |
| unsigned int length | Byte length of the string pointed to by uri, excluding the string terminator '\0'. |
| unsigned int operationMode | Access mode of the URI for which permission is granted or activated. READ_MODE indicates read permission, and WRITE_MODE indicates write permission.<br>Example: FileShare_OperationMode.READ_MODE, FileShare_OperationMode.WRITE_MODE, or FileShare_OperationMode.READ_MODE\|FileShare_OperationMode.WRITE_MODE. |
