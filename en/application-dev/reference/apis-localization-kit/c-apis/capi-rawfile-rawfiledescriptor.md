# RawFileDescriptor

```c
typedef struct RawFileDescriptor {...} RawFileDescriptor
```

## Overview

Provides rawfile file descriptor information, including the file descriptor, start position within the HAP, and file length.<br>This information is obtained through {@link OH_ResourceManager_GetRawFileDescriptorData}, and<br>must be released through {@link OH_ResourceManager_ReleaseRawFileDescriptorData} after use.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int fd | File descriptor of the rawfile. |
| long start | Start position of the rawfile in the HAP, in bytes. |
| long length | Length of the rawfile, in bytes. |


