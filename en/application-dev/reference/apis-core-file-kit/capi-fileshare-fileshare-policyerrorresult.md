# FileShare_PolicyErrorResult
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0547715d750965c950e08363cedf1ff726e5bd8a translatedAt=2026-11-04T03:44:38.215Z pushedAt=2026-11-04T10:12:33.426Z nl=2 -->

```c
typedef struct FileShare_PolicyErrorResult {...} FileShare_PolicyErrorResult
```

## Overview

The URI policy result when permission granting or activation fails, used to record the failed URI, error code, and failure reason.

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

**Header file**: [oh_file_share.h](capi-oh-file-share-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *uri | URI for which permission grant or activation failed. |
| [FileShare_PolicyErrorCode](capi-oh-file-share-h.md#fileshare_policyerrorcode) code | Error code corresponding to the URI for which the permission grant or activation failed. |
| char *message | Reason corresponding to the URI for which the permission grant or activation failed. It is managed by the system and does not need to be released manually. |
