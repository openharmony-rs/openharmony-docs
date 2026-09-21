# RawFile64

```c
typedef struct RawFile64 RawFile64
```

## Overview

`RawFile64` represents an opened rawfile object, which is used for accessing large files of 2 GB and above. It is obtained through {@link OH_ResourceManager_OpenRawFile64}, and must be closed and released through<br>{@link OH_ResourceManager_CloseRawFile64} after use.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 11

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_file.h](capi-raw-file-h.md)

