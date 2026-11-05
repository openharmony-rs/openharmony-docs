# RawFileDescriptor

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:06:24.942Z pushedAt=2026-11-04T10:13:14.902Z nl=1 -->

```c
typedef struct {...} RawFileDescriptor
```

## Overview

Provides the rawfile descriptor information, including the file descriptor of the rawfile, its start position in the HAP, and the file length.<br>Obtain the information by calling [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata), and call [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) to release the file descriptor resource after use.

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int fd | File descriptor of the rawfile. |
| long start | Start position of the rawfile in the HAP package, in bytes. |
| long length | Length of the rawfile, in bytes. |


