# RawFile64

```c
typedef struct RawFile64 RawFile64
```

## Overview

`RawFile64` represents an opened rawfile object, which is used for accessing large files of 2 GB and above. It is obtained through {@link OH_ResourceManager_OpenRawFile64}, and must be closed and released through [OH_ResourceManager_CloseRawFile64](capi-raw-file-h.md#oh_resourcemanager_closerawfile64) after use.

**Since**: 11

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

