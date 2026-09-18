# FileShare_PolicyErrorResult

```c
typedef struct FileShare_PolicyErrorResult {...} FileShare_PolicyErrorResult
```

## Overview

Define the FileShare_PolicyErrorResult structure type.<br> Failed policy result on URI.

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *uri | Indicates the failed uri of the policy information. |
| [FileShare_PolicyErrorCode](capi-oh-file-share-h.md#fileshare_policyerrorcode) code | Indicates the error code of the failure in the policy information. |
| char *message | Indicates the reason of the failure in the policy information. |


