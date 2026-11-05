# FileShare_PolicyInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1762df6ba981ae50b3c588474c27020695a73e2f translatedAt=2026-11-04T03:44:55.900Z pushedAt=2026-11-04T10:12:33.430Z nl=1 -->

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
| unsigned int operationMode | URI access mode for granting or activating permissions. READ_MODE indicates read permission, and WRITE_MODE indicates write permission.<br> Example: FileShare_OperationMode.READ_MODE, FileShare_OperationMode.WRITE_MODE,<br> or FileShare_OperationMode.READ_MODE\|FileShare_OperationMode.WRITE_MODE. |