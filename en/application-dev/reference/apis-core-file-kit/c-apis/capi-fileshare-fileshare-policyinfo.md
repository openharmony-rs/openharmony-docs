# FileShare_PolicyInfo

```c
typedef struct FileShare_PolicyInfo {...} FileShare_PolicyInfo
```

## Overview

Define the FileShare_PolicyInfo structure type.<br> Policy information to manager permissions on a URI.

<!--Device-struct FileShare_PolicyInfo {...}--><!--Device-struct FileShare_PolicyInfo {...}-End-->

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

**Related module**: [fileShare](capi-core-file-kit-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *uri | Indicates the uri of the policy information.<br><!--Device-char *uri--><!--Device-char *uri-End--> |
| unsigned int length | Indicates The length of the uri.<br><!--Device-unsigned int length--><!--Device-unsigned int length-End--> |
| unsigned int operationMode | Indicates the mode of operation for the URI. example { FileShare_OperationMode.READ_MODE } or { FileShare_OperationMode.READ_MODE \| FileShare_OperationMode.WRITE_MODE }.<br><!--Device-unsigned int operationMode--><!--Device-unsigned int operationMode-End--> |


