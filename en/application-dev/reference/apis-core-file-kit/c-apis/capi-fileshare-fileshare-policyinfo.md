# FileShare_PolicyInfo

```c
typedef struct FileShare_PolicyInfo {...} FileShare_PolicyInfo
```

## Overview

Define the FileShare_PolicyInfo structure type.<br> Policy information to manager permissions on a URI.

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *uri | Indicates the uri of the policy information. |
| unsigned int length | Indicates The length of the uri. |
| unsigned int operationMode | Indicates the mode of operation for the URI. example { FileShare_OperationMode.READ_MODE } or { FileShare_OperationMode.READ_MODE \|<br>FileShare_OperationMode.WRITE_MODE }. |


