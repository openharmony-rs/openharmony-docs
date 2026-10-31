# OH_Archive_StreamInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct {...} OH_Archive_StreamInfo
```

## Overview

Defines a struct for compression and decompression of streaming information.

**Since:** 26.0.0

**Related module:** [Archive](capi-archive.md)

**Header file:** [oh_archive.h](capi-oh-archive-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t totalInSize | Size of the input data before compression/decompression, in bytes.<br>**Since:** 26.0.0|
| uint64_t totalOutSize | Size of the output data after compression/decompression, in bytes.<br>**Since:** 26.0.0|
| uint32_t checksum | Checksum of the uncompressed data. When [OH_Archive_StreamChecksumAlg](capi-oh-archive-h.md#oh_archive_streamchecksumalg) is set to **OH_ARCHIVE_NO_CHECKSUM**, the checksum is 0.<br>**Since:** 26.0.0|
