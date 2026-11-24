# OH_Archive_StreamInfo

```c
typedef struct OH_Archive_StreamInfo {...} OH_Archive_StreamInfo
```

## Overview

Stream compression information structure.

<!--Device-typedef struct OH_Archive_StreamInfo {...} OH_Archive_StreamInfo--><!--Device-typedef struct OH_Archive_StreamInfo {...} OH_Archive_StreamInfo-End-->

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Related module**: [Archive](capi-core-file-kit-archive.md)

**Header file**: [oh_archive.h](capi-oh-archive-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t totalInSize | Total input bytes before compression.<br>**Since**: 26.0.0<br><!--Device-uint64_t totalInSize--><!--Device-uint64_t totalInSize-End--> |
| uint64_t totalOutSize | Total output bytes after compression.<br>**Since**: 26.0.0<br><!--Device-uint64_t totalOutSize--><!--Device-uint64_t totalOutSize-End--> |
| uint32_t checksum | Checksum, zero if set OH_ARCHIVE_NO_CHECKSUM.<br>**Since**: 26.0.0<br><!--Device-uint32_t checksum--><!--Device-uint32_t checksum-End--> |


