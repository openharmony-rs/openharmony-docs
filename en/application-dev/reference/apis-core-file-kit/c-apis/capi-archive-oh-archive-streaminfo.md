# OH_Archive_StreamInfo

```c
typedef struct OH_Archive_StreamInfo {...} OH_Archive_StreamInfo
```

## Overview

Stream compression information structure.

**Since**: 26.0.0

**Related module**: [Archive](capi-archive.md)

**Header file**: [oh_archive.h](capi-oh-archive-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t totalInSize | Total input bytes before compression.<br>**Since**: 26.0.0 |
| uint64_t totalOutSize | Total output bytes after compression.<br>**Since**: 26.0.0 |
| uint32_t checksum | Checksum, zero if set OH_ARCHIVE_NO_CHECKSUM.<br>**Since**: 26.0.0 |


