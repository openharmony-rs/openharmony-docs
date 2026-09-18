# OH_Archive_Stream_Config

```c
typedef struct OH_Archive_Stream_Config {...} OH_Archive_Stream_Config
```

## Overview

Stream compression configuration structure.

**Since**: 26.0.0

**Related module**: [Archive](capi-archive.md)

**Header file**: [oh_archive.h](capi-oh-archive-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t blockSize | Size of each memory block in bytes (e.g., 32768 bytes, 65536 bytes), for COMPRESS_DEFLATED, block_size>=32768 bytes<br>**Since**: 26.0.0 |
| int32_t threadNum | Number of threads<br>**Since**: 26.0.0 |
| [OH_Archive_StreamChecksumAlg](capi-oh-archive-h.md#oh_archive_streamchecksumalg) checksum | Hash algorithm used for checksum.<br>**Since**: 26.0.0 |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | Compression method.<br>**Since**: 26.0.0 |


