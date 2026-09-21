# RawDir

```c
typedef struct RawDir RawDir
```

## Overview

`RawDir` represents an opened rawfile directory object, which can be used to traverse the directory and files within it. It is obtained through {@link OH_ResourceManager_OpenRawDir}, and must be closed and released through<br>{@link OH_ResourceManager_CloseRawDir} after use.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

**Related module**: [rawfile](capi-rawfile.md)

**Header file**: [raw_dir.h](capi-raw-dir-h.md)

