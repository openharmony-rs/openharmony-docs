# RawFileDescriptor64

```c
typedef struct RawFileDescriptor64 {...} RawFileDescriptor64
```

## Overview

Provides the rawfile file descriptor information, including the file descriptor, start position within the HAP, and file length. Large files larger than 2 GB are supported.<br>This information is obtained through {@link OH_ResourceManager_GetRawFileDescriptor64}, and must be released through<br>{@link OH_ResourceManager_ReleaseRawFileDescriptor64} after use.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 11

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int fd | File descriptor of the rawfile. |
| int64_t start | Start position of the rawfile in the HAP, in bytes. |
| int64_t length | Length of the rawfile, in bytes. |


