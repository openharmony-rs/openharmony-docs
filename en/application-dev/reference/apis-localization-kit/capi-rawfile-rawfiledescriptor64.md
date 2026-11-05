# RawFileDescriptor64

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:06:58.832Z pushedAt=2026-11-04T10:13:14.903Z nl=1 -->

```c
typedef struct {...} RawFileDescriptor64
```

## Overview

Provides rawfile file descriptor information, including the file descriptor of the rawfile, its start position in the HAP package, and its file length. Supports files larger than 2GB.<br>Obtain the descriptor through [OH_ResourceManager_GetRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor64), and call [OH_ResourceManager_ReleaseRawFileDescriptor64](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptor64) to release the file descriptor resource after use.

**Since**: 11

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int fd | File descriptor of the rawfile. |
| int64_t start | Start position of the rawfile in the HAP package, in bytes. |
| int64_t length | Length of the rawfile, in bytes. |


