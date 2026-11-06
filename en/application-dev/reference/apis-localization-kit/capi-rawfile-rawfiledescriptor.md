# RawFileDescriptor

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:21:32.351Z pushedAt=2026-07-17T09:10:34.593Z -->

```c
typedef struct {...} RawFileDescriptor
```

## Overview

Provides rawfile file descriptor information, including the file descriptor, start position within the HAP, and file length.<br>This information is obtained through [OH_ResourceManager_GetRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptordata), and must be released through [OH_ResourceManager_ReleaseRawFileDescriptorData](capi-raw-file-h.md#oh_resourcemanager_releaserawfiledescriptordata) after use.

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int fd | File descriptor of the rawfile. |
| int64_t start | Start position of the rawfile in the HAP, in bytes. |
| int64_t length | Length of the rawfile, in bytes. |